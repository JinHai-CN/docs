---
id: configure-milvus
title: Configure Milvus
sidebar_label: Configure Milvus
---

# Configure Milvus


## Milvus file structure
After you have successfully started Milvus server, you can see a Milvus file under the path *home/$USER/milvus*, which contains the following child files:

- *milvus/db* (database storage)
- *milvus/logs* (log storage)
- *milvus/conf* (configuration file)
    - *server_config.yaml* (service configuration file)
    - *log_config.conf* (log configuration file)

## Set up Milvus service

Follow these procedures to configure Milvus service:

1. In the directory *home/$USER/milvus/conf*, open Milvus service configuration file *server_config.yaml*.

2. Modify the parameters in the file.

   1）In section *server_config*, edit service parameters.
   
     | Parameter            | Description                          | Reference value           |
     |----------------|-----------------------------------|-------------------|
     | address        | The IP address that Milvus server monitors      | 0.0.0.0           |
     | port           | The port that Milvus server monitors, default is 19530 | 1025 ~ 65534 |            
     | gpu_index      | Current GPU, default is 0          | 0 ~ GPU number ~1                |
     | mode           | Milvus deployment method                    | single / cluster |            
                                                                                                                     
   2）In section *db_config*, edit database parameters.
   
     | Parameter               | Description                            | Reference value    |
     |-------------------|-------------------------------------|----------|
     | db_path           | Directory of Milvus database files            |    /opt/data   |
     | db_backend_url    | Meta database URL                         |sqlite://:@:/ |
     | index_building_threshold | index building trigger value       |  1024 (MB)  |
     | archive_disk_threshold | Archive action triggered if storage size exceed this value. Default value is 512 (GB).| >0 |
     | archive_days_threshold | Files older than x days will be archived. Default value is 30 (Day).|  >0  |
     
   > Note: db_backend_url format is: dialect://username:password@host:port/database. ('dialect' can be either 'mysql' or 'sqlite', depending on whether you use MySQL or SQLite for the metadata storage.)
                                 
   3）In section *metric_config*, edit monitor parameters.
   
     |Parameter               |  Description                             | Reference value     |
     |-------------------|-------------------------------------|----------|
     | is_startup        | Select if or not to turn on the monitoring system          | on / off |
     | collector         | Connected monitoring system               | Prometheus             |
     | collect_type      | Data collecting type of Prometheus     |   pull / push          |
     | port              | Port to visit Prometheus       | 8080                   |
     | push_gateway_ip_address | IP address of push gateway   | 127.0.0.1             |
     | push_gateway_port       | Port of push gateway   |  9091                 |

   4）In section *cache_config*, edit below parameter.
   
     |  Parameter                | Description                             | Reference value     |
     |-------------------|-------------------------------------|----------|
     | cpu_cache_capacity | Memory used for cache in CPU. Default value is 16 (GB)       |  0 ~ Total memory size |

     
3. Restart Milvus Docker.

   ```
   $ docker restart <container id>
   ```

