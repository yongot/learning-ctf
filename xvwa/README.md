# Xtreme Vulnerable Web Application

## Docker XVWA
Download and run
```docker run --name xvwa -d -p 18080:80 tuxotron/xvwa```

Open your browser
```http://locallhost/xvwa```
```http://<<ip address>>/xvwa```

The first thing you need to do is to go to Setup / Reset menu and click on Submit / Reset button. This will prepare the database.

Stop the container
```docker stop xvwa```

Start the same container
```docker start xvwa```


Reference:
- [xvwa github](https://github.com/s4n7h0/xvwa) 
- [xvwa_lamp_container](https://github.com/tuxotron/xvwa_lamp_container)
- [xvwa answers](https://github.com/rudSarkar/xvwa-solution)
