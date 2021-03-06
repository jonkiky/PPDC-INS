# ElasticSearch

**Index:**

```text
{
  "mappings": {
    "dynamic_templates": [
      {
        "nesteds": {
          "match_mapping_type": "object",
          "match": "facet_*",
          "mapping": {
            "type": "nested"
          }
        }
      }
    ]
  },
  "settings": {
    "index": {
      "number_of_replicas": 0,
      "number_of_shards": 5
    }
  }
}
```

**Note:**

The `nested` type is a specialised version of the [`object`](https://www.elastic.co/guide/en/elasticsearch/reference/current/object.html) data type that allows arrays of objects to be indexed in a way that they can be queried independently of each other.





**Index\_search**

```text
{
  "mappings": {
    "properties": {
      "multiplier": {
        "type": "float"
      }
    },
    "dynamic_templates": [
      {
        "strings": {
          "match_mapping_type": "string",
          "mapping": {
            "type": "text",
            "term_vector": "with_positions_offsets",
            "fields": {
              "raw": {
                "type": "keyword",
                "ignore_above": 1024,
                "normalizer": "custom"
              }
            }
          }
        }
      }
    ]
  },
  "settings": {
    "index": {
      "number_of_replicas": 0,
      "number_of_shards": 5,
      "analysis": {
        "normalizer": {
          "custom": {
            "type": "custom",
            "char_filter": [],
            "filter": ["lowercase"]
          }
        },
        "filter": {
          "autocomplete_filter": {
            "type": "edge_ngram",
            "min_gram": 2,
            "max_gram": 20,
            "token_chars": [
              "letter",
              "digit",
              "punctuation",
              "symbol"
            ]
          },
          "word_delimiter_filter": {
            "type": "word_delimiter",
            "catenate_numbers": false,
            "catenate_words": false,
            "generate_word_parts": false,
            "generate_number_parts": true,
            "catenate_all": false,
            "split_on_case_change": false,
            "split_on_numerics": false,
            "preserve_original": true,
            "stem_english_possesive": true
          }
        },
        "analyzer": {
          "default": {
            "type": "custom",
            "tokenizer": "whitespace",
            "filter": [
              "lowercase",
              "autocomplete_filter"
            ]
          },
          "default_search": {
            "type": "custom",
            "tokenizer": "keyword",
            "filter": [
              "lowercase"
            ]
          },
          "ngram_analyzer": {
            "type": "custom",
            "tokenizer": "whitespace",
            "filter": [
              "lowercase",
              "autocomplete_filter"
            ]
          },
          "token": {
            "type": "custom",
            "tokenizer": "keyword",
            "filter": [
              "lowercase"
            ]
          }
        }
      }
    }
  }
}
```

**index\_**_**known\_drougs**_

```text
{
  "mappings": {
    "properties": {
      "multiplier": {
        "type": "float"
      }
    },
    "dynamic_templates": [
      {
        "strings": {
          "match_mapping_type": "string",
          "mapping": {
            "type": "text",
            "term_vector": "with_positions_offsets",
            "fields": {
              "raw": {
                "type": "keyword",
                "ignore_above": 1024,
                "normalizer": "custom"
              }
            }
          }
        }
      }
    ]
  },
  "settings": {
    "index": {
      "number_of_replicas": 0,
      "number_of_shards": 5,
      "max_ngram_diff": 20,
      "analysis": {
        "normalizer": {
          "custom": {
            "type": "custom",
            "char_filter": [],
            "filter": ["lowercase"]
          }
        },
        "filter": {
          "autocomplete_filter": {
            "type": "ngram",
            "min_gram": 1,
            "max_gram": 20,
            "token_chars": [
              "letter",
              "digit",
              "punctuation",
              "symbol"
            ]
          },
          "word_delimiter_filter": {
            "type": "word_delimiter",
            "catenate_numbers": false,
            "catenate_words": false,
            "generate_word_parts": false,
            "generate_number_parts": true,
            "catenate_all": false,
            "split_on_case_change": false,
            "split_on_numerics": false,
            "preserve_original": true,
            "stem_english_possesive": true
          }
        },
        "analyzer": {
          "default": {
            "type": "custom",
            "tokenizer": "whitespace",
            "filter": [
              "lowercase",
              "autocomplete_filter"
            ]
          },
          "default_search": {
            "type": "custom",
            "tokenizer": "keyword",
            "filter": [
              "lowercase"
            ]
          },
          "ngram_analyzer": {
            "type": "custom",
            "tokenizer": "whitespace",
            "filter": [
              "lowercase",
              "autocomplete_filter"
            ]
          },
          "token": {
            "type": "custom",
            "tokenizer": "keyword",
            "filter": [
              "lowercase"
            ]
          }
        }
      }
    }
  }
}
```

