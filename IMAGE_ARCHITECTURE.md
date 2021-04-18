```
docker-borgmatic/
├── base
│   ├── data
│   │   ├── borgmatic
│   │   │   ├── config.yml
│   │   │   └── crontab.txt
│   │   └── rclone_config
│   │       └── rclone.conf           # Optional, only if the after_backup hook uses rclone
│   ├── docker-compose.restore.yml     
│   ├── docker-compose.yml
│   ├── Dockerfile
│   ├── .env
│   └── entry.sh      
├── msmtp
│   ├── data
│   │   ├── borgmatic.d
│   │   │   ├── config.yml             # same as in base
│   │   │   ├── crontab.txt            # with mailto
│   │   │   └── msmtprc.sh
│   │   └── rclone_config
│   │       └── rclone.conf
│   ├── docker-compose.yml             # image: frutti93/borgmatic:latest-msmtp, env: msmtp.env
│   ├── Dockerfile                     # FROM frutti93/borgmatic:${VERSION}
│   ├── entry.sh                       # starts msmtp in addition
│   ├── .env
│   ├── msmtp.env                      # msmtp environment variables
│   └── README.md                      # describes specifics only
├── ntfy
│   ├── data
│   │   ├── borgmatic.d
│   │   │   ├── config.yml             # same as in base
│   │   │   └── crontab.txt            # same as in base
│   │   └── rclone_config
│   │       └── rclone.conf
│   ├── docker-compose.yml             # image: frutti93/borgmatic:latest-ntfy
│   ├── Dockerfile                     # FROM frutti93/borgmatic:${VERSION}
│   ├── entry.sh                       # same as in base
│   └── README.md                      # describes specifics only
└── README.md     
```
