# Elasticsearch

Clément MACHADO

Exercice 1

Le fichier elasticsearch.yml:
# ======================== Elasticsearch Configuration =========================
#
# NOTE: Elasticsearch comes with reasonable defaults for most settings.
#       Before you set out to tweak and tune the configuration, make sure you
#       understand what are you trying to accomplish and the consequences.
#
# The primary way of configuring a node is via this file. This template lists
# the most important settings you may want to configure for a production cluster.
#
# Please consult the documentation for further information on configuration options:
# https://www.elastic.co/guide/en/elasticsearch/reference/index.html
#
# ---------------------------------- Cluster -----------------------------------
#
# Use a descriptive name for your cluster:
#
cluster.name: magic-system
#
# ------------------------------------ Node ------------------------------------
#
# Use a descriptive name for the node:
#
node.name: es-01
#
# Add custom attributes to the node:
#
#node.attr.rack: r1
#
# ----------------------------------- Paths ------------------------------------
#
# Path to directory where to store the data (separate multiple locations by comma):
#
path.data: /var/lib/elasticsearch
#
# Path to log files:
#
path.logs: /var/log/elasticsearch
#
# ----------------------------------- Memory -----------------------------------
#
# Lock the memory on startup:
#
#bootstrap.memory_lock: true
#
# Make sure that the heap size is set to about half the memory available
# on the system and that the owner of the process is allowed to use this
# limit.
#
# Elasticsearch performs poorly when the system is swapping the memory.
#
# ---------------------------------- Network -----------------------------------
#
# By default Elasticsearch is only accessible on localhost. Set a different
# address here to expose this node on the network:
#
#network.host: 192.168.0.1
#
# By default Elasticsearch listens for HTTP traffic on the first free port it
# finds starting at 9200. Set a specific HTTP port here:
#
#http.port: 9200
#
# For more information, consult the network module documentation.
#
# --------------------------------- Discovery ----------------------------------
#
# Pass an initial list of hosts to perform discovery when this node is started:
# The default list of hosts is ["127.0.0.1", "[::1]"]
#
#discovery.seed_hosts: ["host1", "host2"]
#
# Bootstrap the cluster using an initial set of master-eligible nodes:
#
#cluster.initial_master_nodes: ["node-1", "node-2"]
#
# For more information, consult the discovery and cluster formation module documentation.
#
# ---------------------------------- Various -----------------------------------
#
# Allow wildcard deletion of indices:
#
#action.destructive_requires_name: false

#----------------------- BEGIN SECURITY AUTO CONFIGURATION -----------------------
#
# The following settings, TLS certificates, and keys have been automatically      
# generated to configure Elasticsearch security features on 25-04-2023 07:36:16
#
# --------------------------------------------------------------------------------

# Enable security features
xpack.security.enabled: false

xpack.security.enrollment.enabled: true

# Enable encryption for HTTP API client connections, such as Kibana, Logstash, and Agents
xpack.security.http.ssl:
  enabled: true
  keystore.path: certs/http.p12

# Enable encryption and mutual authentication between cluster nodes
xpack.security.transport.ssl:
  enabled: true
  verification_mode: certificate
  keystore.path: certs/transport.p12
  truststore.path: certs/transport.p12
# Create a new cluster with the current node only
# Additional nodes can still join the cluster later
cluster.initial_master_nodes: ["PC-clement"]

# Allow HTTP API connections from anywhere
# Connections are encrypted and require user authentication
http.host: 0.0.0.0

# Allow other nodes to join the cluster from anywhere
# Connections are encrypted and mutually authenticated
#transport.host: 0.0.0.0

#----------------------- END SECURITY AUTO CONFIGURATION -------------------------
Le nom du fichier pour paramétrer les options de la JVM est: jvm.options. Il se situe dans: /etc/elasticsearch/jvm.options lorsque l'installation est réalisé avec apt.

Il faut écrire la valeur suivante: -Xmx8g dans le fichier jvm.options pour limiter la heap size à 8GB.

Exercice 2
J'ai utilisé la méthode {"index":{"_index": "recettes-test"}}
J'ai utilisé l'endpoint: POST /_bulk
Voici la requête complète:
POST /_bulk
{"index":{"_index": "recettes-test"}}
{"title": "Tarte aux pommes", "author": "Alice", "description": "Une tarte aux pommes croustillante et délicieuse", "publication_date": "2022-05-01", "pages": 20}
{"index":{"_index": "recettes-test"}}
{"title": "Gaufres au caramel", "author": "Bob", "description": "Des gaufres moelleuses avec une sauce caramel maison", "publication_date": "2021-12-15", "pages": 15}
{"index":{"_index": "recettes-test"}}
{"title": "Muffins au citron", "author": "Dimitri", "description": "Des muffins frais et acidulés", "publication_date": "2023-01-03", "pages": 18}
{"index":{"_index": "recettes-test"}}
{"title": "Crêpes à la framboise", "author": "Zoé", "description": "Des crêpes légères et fruitées", "publication_date": "2022-07-23", "pages": 22}
{"index":{"_index": "recettes-test"}}
{"title": "Tiramisu aux pommes caramélisées", "author": "Camille", "description": "Un tiramisu revisité avec des pommes caramélisées", "publication_date": "2021-11-11", "pages": 25}
{"index":{"_index": "recettes-test"}}
{"title": "Gâteau au citron", "author": "Alex", "description": "Un gâteau moelleux et parfumé au citron", "publication_date": "2023-02-14", "pages": 30}
{"index":{"_index": "recettes-test"}}
{"title": "Tarte aux framboises et citron vert", "author": "Alice", "description": "Une tarte légère et acidulée", "publication_date": "2022-08-09", "pages": 21}
{"index":{"_index": "recettes-test"}}
{"title": "Gaufres à la pomme", "author": "Bob", "description": "Des gaufres aux pommes cuites à la cannelle", "publication_date": "2021-09-30", "pages": 16}
{"index":{"_index": "recettes-test"}}
{"title": "Muffins au caramel", "author": "Dimitri", "description": "Des muffins gourmands au caramel fondant", "publication_date": "2022-04-19", "pages": 19}
{"index":{"_index": "recettes-test"}}
{"title": "Crêpes au citron et sucre", "author": "Zoé", "description": "Des crêpes classiques au citron et sucre", "publication_date": "2023-03-27", "pages": 23}
{"index":{"_index": "recettes-test"}}
{"title": "Gâteau aux framboises", "author": "Camille", "description": "Un gâteau aux framboises légèrement acidulé", "publication_date": "2021-10-10", "pages": 28}
{"index":{"_index": "recettes-test"}}
{"title": "Tarte au citron meringuée", "author": "Alex", "description": "Une tarte au citron avec une belle meringue dorée", "publication_date": "2023-04-01", "pages": 24}
{"index":{"_index": "recettes-test"}}
{"title": "Muffins aux framboises et citron", "author": "Dimitri", "description": "Des muffins moelleux et fruités", "publication_date": "2022-09-16", "pages": 17}
{"index":{"_index": "recettes-test"}}
{"title": "Crêpes au caramel", "author": "Zoé", "description": "Des crêpes avec une sauce caramel maison", "publication_date": "2023-02-28", "pages": 20}
{"index":{"_index": "recettes-test"}}
{"title": "Gaufres à la pomme et cannelle", "author": "Bob", "description": "Des gaufres avec des pommes cuites à la cannelle", "publication_date": "2022-01-07", "pages": 19}
{"index":{"_index": "recettes-test"}}
{"title": "Tiramisu aux framboises", "author": "Alice", "description": "Un tiramisu léger et fruité", "publication_date": "2021-12-25", "pages": 26}
{"index":{"_index": "recettes-test"}}
{"title": "Gâteau au citron et aux amandes", "author": "Camille", "description": "Un gâteau moelleux et parfumé aux amandes et au citron", "publication_date": "2022-10-03", "pages": 27}
{"index":{"_index": "recettes-test"}}
{"title": "Tarte aux pommes et à la cannelle", "author": "Alex", "description": "Une tarte aux pommes avec de la cannelle et une pâte sablée croquante", "publication_date": "2023-03-10", "pages": 23}
{"index":{"_index": "recettes-test"}}
{"title": "Muffins au caramel et noisettes", "author": "Dimitri", "description": "Des muffins gourmands avec un cœur de caramel et des éclats de noisettes", "publication_date": "2022-05-14", "pages": 22}
{"index":{"_index": "recettes-test"}}
{"title": "Crêpes à la pomme et cannelle", "author": "Zoé", "description": "Des crêpes avec des pommes cuites à la cannelle et une pointe de vanille", "publication_date": "2023-01-20", "pages": 21}
Exercice 3
1.
Il n'y a aucun résultat. Il faudrait utiliser le french analyzer pour que celui-ci supprime tout les s à la fin des mots.

La requête utilisée:

GET /recettes-test/_search
{
  "query": {
    "match": {
      "description": "pomme"
    }
  }
}
2.
J'ai obtenu un seul document.

La requête utilisée:

GET /recettes-test/_search
{
  "query": {
    "bool": {
      "must": [
        {"match": {
          "author.keyword": "Zoé"
        }},
        {"range": {
          "pages": {
            "lt": 21
          }
        }}
      ]
    }
  }
}
Exercice 4
Le type de champs approprié est le type keyword, en effet le thème sera sûrement en un seul mot et une recherche sur le keyword sera le plus adapté.
La requête utilisée:

PUT /recettes-test/_mapping
{
  "properties": {
    "theme": {
      "type": "keyword"
    }
  }
}
Exercice 5
Requête de création de l'index et du mapping:

PUT /recettes-test-mapping
{
  "mappings": {
    "properties": {
      "titre": {"type": "text"},
      "author": {"type": "keyword"},
      "description": {"type": "text"},
      "publication_date": {"type": "date"},
      "pages": {"type": "integer"}
    }
  }
}
Requête de réindexation:

POST _reindex
{
  "source": {
    "index": "recettes-test"
  },
  "dest": {
    "index": "recettes-test-mapping"
  }
}
Exercice 6
1.
Requête de recherche avec agrégation:

GET /recettes-test/_search
{
  "size": 20, 
  "query": {
    "range": {
      "publication_date": {
        "lt": "2023"
      }
    }
  },
  "aggs": {
    "recette-par-auteur": {
      "terms": {
        "field": "author.keyword"
      }
    }
  }
}
Réponse à la requête d'agrégation

{
  "took": 1,
  "timed_out": false,
  "_shards": {
    "total": 1,
    "successful": 1,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": {
      "value": 13,
      "relation": "eq"
    },
    "max_score": 1,
    "hits": [
      {
        "_index": "recettes-test",
        "_id": "lvkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Tarte aux pommes",
          "author": "Alice",
          "description": "Une tarte aux pommes croustillante et délicieuse",
          "publication_date": "2022-05-01",
          "pages": 20
        }
      },
      {
        "_index": "recettes-test",
        "_id": "l_kZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Gaufres au caramel",
          "author": "Bob",
          "description": "Des gaufres moelleuses avec une sauce caramel maison",
          "publication_date": "2021-12-15",
          "pages": 15
        }
      },
      {
        "_index": "recettes-test",
        "_id": "mfkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Crêpes à la framboise",
          "author": "Zoé",
          "description": "Des crêpes légères et fruitées",
          "publication_date": "2022-07-23",
          "pages": 22
        }
      },
      {
        "_index": "recettes-test",
        "_id": "mvkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Tiramisu aux pommes caramélisées",
          "author": "Camille",
          "description": "Un tiramisu revisité avec des pommes caramélisées",
          "publication_date": "2021-11-11",
          "pages": 25
        }
      },
      {
        "_index": "recettes-test",
        "_id": "nPkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Tarte aux framboises et citron vert",
          "author": "Alice",
          "description": "Une tarte légère et acidulée",
          "publication_date": "2022-08-09",
          "pages": 21
        }
      },
      {
        "_index": "recettes-test",
        "_id": "nfkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Gaufres à la pomme",
          "author": "Bob",
          "description": "Des gaufres aux pommes cuites à la cannelle",
          "publication_date": "2021-09-30",
          "pages": 16
        }
      },
      {
        "_index": "recettes-test",
        "_id": "nvkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Muffins au caramel",
          "author": "Dimitri",
          "description": "Des muffins gourmands au caramel fondant",
          "publication_date": "2022-04-19",
          "pages": 19
        }
      },
      {
        "_index": "recettes-test",
        "_id": "oPkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Gâteau aux framboises",
          "author": "Camille",
          "description": "Un gâteau aux framboises légèrement acidulé",
          "publication_date": "2021-10-10",
          "pages": 28
        }
      },
      {
        "_index": "recettes-test",
        "_id": "ovkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Muffins aux framboises et citron",
          "author": "Dimitri",
          "description": "Des muffins moelleux et fruités",
          "publication_date": "2022-09-16",
          "pages": 17
        }
      },
      {
        "_index": "recettes-test",
        "_id": "pPkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Gaufres à la pomme et cannelle",
          "author": "Bob",
          "description": "Des gaufres avec des pommes cuites à la cannelle",
          "publication_date": "2022-01-07",
          "pages": 19
        }
      },
      {
        "_index": "recettes-test",
        "_id": "pfkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Tiramisu aux framboises",
          "author": "Alice",
          "description": "Un tiramisu léger et fruité",
          "publication_date": "2021-12-25",
          "pages": 26
        }
      },
      {
        "_index": "recettes-test",
        "_id": "pvkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Gâteau au citron et aux amandes",
          "author": "Camille",
          "description": "Un gâteau moelleux et parfumé aux amandes et au citron",
          "publication_date": "2022-10-03",
          "pages": 27
        }
      },
      {
        "_index": "recettes-test",
        "_id": "qPkZwocBT1ZecB6g31Dz",
        "_score": 1,
        "_source": {
          "title": "Muffins au caramel et noisettes",
          "author": "Dimitri",
          "description": "Des muffins gourmands avec un cœur de caramel et des éclats de noisettes",
          "publication_date": "2022-05-14",
          "pages": 22
        }
      }
    ]
  },
  "aggregations": {
    "recette-par-auteur": {
      "doc_count_error_upper_bound": 0,
      "sum_other_doc_count": 0,
      "buckets": [
        {
          "key": "Alice",
          "doc_count": 3
        },
        {
          "key": "Bob",
          "doc_count": 3
        },
        {
          "key": "Camille",
          "doc_count": 3
        },
        {
          "key": "Dimitri",
          "doc_count": 3
        },
        {
          "key": "Zoé",
          "doc_count": 1
        }
      ]
    }
  }
}
2.
Requête d'agrégation de la moyenne du nombre de pages par auteur:

GET /recettes-test/_search
{
  "size": 0,
  "aggs": {
    "aggregation-utilisateur": {
      "terms": {
        "field": "author.keyword"
      },
      "aggs": {
        "moyenne-page": {
          "avg": {
            "field": "pages"
          }
        }
      }
    }
  }
}
Résultat de la requête d'agrégation:

{
  "took": 25,
  "timed_out": false,
  "_shards": {
    "total": 1,
    "successful": 1,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": {
      "value": 20,
      "relation": "eq"
    },
    "max_score": null,
    "hits": []
  },
  "aggregations": {
    "aggregation-utilisateur": {
      "doc_count_error_upper_bound": 0,
      "sum_other_doc_count": 0,
      "buckets": [
        {
          "key": "Dimitri",
          "doc_count": 4,
          "moyenne-page": {
            "value": 19
          }
        },
        {
          "key": "Zoé",
          "doc_count": 4,
          "moyenne-page": {
            "value": 21.5
          }
        },
        {
          "key": "Alex",
          "doc_count": 3,
          "moyenne-page": {
            "value": 25.666666666666668
          }
        },
        {
          "key": "Alice",
          "doc_count": 3,
          "moyenne-page": {
            "value": 22.333333333333332
          }
        },
        {
          "key": "Bob",
          "doc_count": 3,
          "moyenne-page": {
            "value": 16.666666666666668
          }
        },
        {
          "key": "Camille",
          "doc_count": 3,
          "moyenne-page": {
            "value": 26.666666666666668
          }
        }
      ]
    }
  }
}
Exercice 7
Requête pour créer le nouvel index:

PUT /recettes-fr
{
  "settings": {
    "analysis": {
      "analyzer": {
        "default": {
          "type": "french"
        }
      }
    }
  },
  "mappings": {
    "properties": {
      "titre": {"type": "text"},
      "author": {"type": "keyword"},
      "description": {"type": "text"},
      "publication_date": {"type": "date"},
      "pages": {"type": "integer"}
    }
  }
}
On reprend le mapping de la question 5. On spécifie l'analyzer à utiliser par défaut sur french.

Requête pour réindexer les documents dans le nouvel index avec le nouvel analyzer:

POST _reindex
{
  "source": {
    "index": "recettes-test"
  },
  "dest": {
    "index": "recettes-fr"
  }
}
Exercice 8
1.
Le document a été indexé correctement, le type de la donnée est un integer il permet donc les nombres négatifs.

Requête de l'indexation du nouveau document avec un nombre de pages négatif:

POST /recettes-fr/_doc
{
  "title": "Crêpes nature",
  "author": "Zoé",
  "description": "Des crêpes nature",
  "publication_date": "2023-01-23",
  "pages": -5
}
2.
Il y a 6 documents qui sont renvoyés contenant le mot pomme dans leurs descriptions

Requête de récupération des documents contenant le mot pomme dans leurs descriptions:

GET /recettes-fr/_search
{
  "query": {
    "match": {
      "description": "pomme"
    }
  }
}
Exercice 9
Requête pour obtenir les tokens générés par l'analyzer Norvégien sur la phrase Jeg elsker klokka åtte-timer:

POST _analyze
{
  "analyzer": "norwegian",
  "text": "Jeg elsker klokka åtte-timer"
}
Réponse de la liste des tokens:

{
  "tokens": [
    {
      "token": "elsk",
      "start_offset": 4,
      "end_offset": 10,
      "type": "<ALPHANUM>",
      "position": 1
    },
    {
      "token": "klokk",
      "start_offset": 11,
      "end_offset": 17,
      "type": "<ALPHANUM>",
      "position": 2
    },
    {
      "token": "ått",
      "start_offset": 18,
      "end_offset": 22,
      "type": "<ALPHANUM>",
      "position": 3
    },
    {
      "token": "tim",
      "start_offset": 23,
      "end_offset": 28,
      "type": "<ALPHANUM>",
      "position": 4
    }
  ]
}
Exercice 10
1.
Requête de l'ajout d'un template template-index sur tous les indexs respectant le pattern recettes-* ajoutant un mapping, un analyzer et un alias.

PUT _index_template/template-index
{
  "index_patterns": "recettes-*",
  "template": {
    "settings": {
      "analysis": {
        "analyzer": {
          "default": {
            "type": "french"
          }
        }
      }
    },
    "mappings": {
      "properties": {
        "titre": {
          "type": "text"
        },
        "author": {
          "type": "keyword"
        },
        "description": {
          "type": "text"
        },
        "publication_date": {
          "type": "date"
        },
        "pages": {
          "type": "integer"
        }
      }
    },
    "aliases": {
      "recettes": {}
    }
  }
}
2.
Requête d'indexation d'un document dans l'index recettes-es sans l'avoir créé au préalable:

POST /recettes-es/_doc
{
  "title": "Crêpes",
  "author": "Clément",
  "description": "Des crêpes",
  "publication_date": "2023-03-23",
  "pages": 5
}
3.
Requête pour vérifier que le template à bien fonctionné:

GET /recettes-es
Réponse à la requête de vérification:

{
  "recettes-es": {
    "aliases": {
      "recettes": {}
    },
    "mappings": {
      "properties": {
        "author": {
          "type": "keyword"
        },
        "description": {
          "type": "text"
        },
        "pages": {
          "type": "integer"
        },
        "publication_date": {
          "type": "date"
        },
        "title": {
          "type": "text",
          "fields": {
            "keyword": {
              "type": "keyword",
              "ignore_above": 256
            }
          }
        },
        "titre": {
          "type": "text"
        }
      }
    },
    "settings": {
      "index": {
        "routing": {
          "allocation": {
            "include": {
              "_tier_preference": "data_content"
            }
          }
        },
        "number_of_shards": "1",
        "provided_name": "recettes-es",
        "creation_date": "1682594715573",
        "analysis": {
          "analyzer": {
            "default": {
              "type": "french"
            }
          }
        },
        "number_of_replicas": "1",
        "uuid": "9iqNOeM0QyyjmFMbFSIU4Q",
        "version": {
          "created": "8070099"
        }
      }
    }
  }
}
4.
Requête pour récupérer le nombre de documents derrière l'alias recettes:

GET /recettes
Il y a un seul document derrière l'alias recettes, c'est le document que l'on a créé après le template
{
  "took": 0,
  "timed_out": false,
  "_shards": {
    "total": 1,
    "successful": 1,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": {
      "value": 1,
      "relation": "eq"
    },
    "max_score": 1,
    "hits": [
      {
        "_index": "recettes-es",
        "_id": "rfl1wocBT1ZecB6g2FAM",
        "_score": 1,
        "_source": {
          "title": "Crêpes",
          "author": "Clément",
          "description": "Des crêpes",
          "publication_date": "2023-03-23",
          "pages": 5
        }
      }
    ]
  }
}
