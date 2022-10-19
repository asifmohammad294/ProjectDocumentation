- spring data elastic search
- download link-> https://www.elastic.co/downloads/elasticsearch
- run bin\elasticsearch.bat on Windows it will run on port http://localhost:9200
- to see all the available indices http://localhost:9200/_cat/indices
- to see specific index http://localhost:9200/person
- to search http://localhost:9200/person/_search

# Config.java for older version of spring boot
    //    @Bean
    //    @Override
    //    public RestHighLevelClient elasticsearchClient() {
    //        final ClientConfiguration config = ClientConfiguration.builder()
    //                .connectedTo(elasticsearchUrl)
    //                .build();
    //        return RestClients.create(config).rest();
    //    }

# Config.java for new version of spring boot
    @Bean
    @Override
    public RestHighLevelClient elasticsearchClient() {
        return new RestHighLevelClientBuilder(
                RestClient.builder(
                                new HttpHost("localhost", 9200, "http"))
                        .build())
                .setApiCompatibilityMode(true)
                .build();
    }


# elastic search query to search all records
- https://stackoverflow.com/questions/8829468/elasticsearch-query-to-return-all-records