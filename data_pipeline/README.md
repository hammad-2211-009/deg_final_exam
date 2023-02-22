# Data pipeline task

You are working as a data engineer for a big content publisher.
Your boss gave you a task to prepare a report about page views that occured on your sites.

Files with the page view data appear in real-time on the `MinIO` S3 bucket in proper hour-partitioned directories. Example directory structure may look like this:

```
s3://YOUR_BUCKET
└── year=2022
    └── month=12
        └── day=08
            ├── hour=01
            │   ├── 000001.csv
            │   ├── 000002.csv
            │   ├── 000003.csv
            │   └── FULL
            ├── hour=02
            │   ├── 000001.csv
            │   └── FULL
            └── hour=03
```

An empty file named `FULL` indicates that the given hour-partition is complete and ready for further processing.

Prepare pipeline which:
* Runs hourly
* Downloads files from the bucket and put them in some database
* Calculates: (sum of page views, sum of unique users) grouped by site, device type, and browser

Together with the task there is a python script provided (**do not edit it**). If you run the script, it will generate example data for you.
To run the script and send data to `MinIO` you need to do following:
* set `MINIO_ROOT_USER` and `MINIO_ROOT_PASSWORD` environment variables.
* deploy the `MinIO` instance using `docker-compose` (see `minio_deployment` folder).
* create virtual environment and activate it
* install packages listed in requirements.txt
* run `python3 data_generator.py --help` to see available options

Hints:
* To set environment variables, you can run `export VARIABLE_NAME=variable_value`.
