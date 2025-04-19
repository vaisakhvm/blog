---
title: "A Minimal Client-Server in C"
date: 2025-04-19
---

Wrote a basic server and client in C. Server listens, client says hi, server replies.

### `server.c`
{% highlight c %}
int main(int argc, char *argv[]) {
    int sockfd, newsockfd;
    struct sockaddr_in serv_addr, cli_addr;
    socklen_t clilen;
    char buffer[1024];

    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_addr.s_addr = INADDR_ANY;
    serv_addr.sin_port = htons(atoi(argv[1]));

    bind(sockfd, (struct sockaddr *) &serv_addr, sizeof(serv_addr));
    listen(sockfd, 5);
    clilen = sizeof(cli_addr);

    while (1) {
        newsockfd = accept(sockfd, (struct sockaddr *) &cli_addr, &clilen);
        memset(buffer, 0, 1024);
        read(newsockfd, buffer, 1023);
        printf("Client: %s\n", buffer);
        write(newsockfd, "Hello from server\n", 18);
        close(newsockfd);
    }
}
{% endhighlight %}

### `client.c`
{% highlight c %}
int main(int argc, char *argv[]) {
    int sockfd;
    struct sockaddr_in serv_addr;
    struct hostent *server;
    char buffer[1024];

    server = gethostbyname(argv[1]);
    sockfd = socket(AF_INET, SOCK_STREAM, 0);

    memset(&serv_addr, 0, sizeof(serv_addr));
    memcpy(&serv_addr.sin_addr, server->h_addr, server->h_length);
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_port = htons(atoi(argv[2]));

    connect(sockfd, (struct sockaddr *) &serv_addr, sizeof(serv_addr));
    strcpy(buffer, argv[3]);
    write(sockfd, buffer, strlen(buffer));
    close(sockfd);
}
{% endhighlight %}

### Compile
{% highlight bash %}
gcc server.c -o server
gcc client.c -o client
{% endhighlight %}

### Run

{% highlight bash %}
# Terminal 1 – Start the server:
./server 3500
{% endhighlight %}


{% highlight bash %}
# Terminal 2 – Run the client:
./client 127.0.0.1 3500 "hello server"
{% endhighlight %}