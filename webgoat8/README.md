# Webgoat 8

## Docker Webgoat
Download webgoat image
```docker pull webgoat/webgoat-8.0```

Run webgoat docker
```docker run -p 8080:8080 -t webgoat/webgoat-8.0```

Accessing webgoat page
```http://127.0.0.1:8080/WebGoat```

Find the webgoat container id
```docker ps```

Stop webgoat docker
```docker stop 1240f272bc03```


## Docker Webgoat and Webwolf
Prepare the goat-with-reverseproxy.yaml

Download webgoat and webwolf bundle image
```docker pull webgoat/goatandwolf```

Init docker swarm
```docker swarm init```

Run the webgoat demo with yaml configuration file
```docker stack deploy --compose-file goat-with-reverseproxy.yaml webgoatdemo```

Remove webgoat stack
```docker stack rm webgoatdemo```

Set windows hosts file to map address
```127.0.0.1 www.webgoat.local www.webwolf.local```

Browse URL for webgoat
```http://www.webgoat.local/WebGoat/login```

Browse URL for webwolf
```http://www.webwolf.local/WebWolf```




