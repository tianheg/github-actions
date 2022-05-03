# Send Mail

```yml
# mail.yml

- name: Send mail
  uses: dawidd6/action-send-mail@v3
  with:
    # Required mail server address:
    server_address: smtp.gmail.com
    # Required mail server port:
    server_port: 465
    # Optional (recommended): mail server username:
    username: ${{secrets.MAIL_USERNAME}}
    # Optional (recommended) mail server password:
    password: ${{secrets.MAIL_PASSWORD}}
    # Required mail subject:
    subject: Github Actions job result
    # Required recipients' addresses:
    to: obiwan@example.com,yoda@example.com
    # Required sender full name (address can be skipped):
    from: Luke Skywalker # <user@example.com>
    # Optional whether this connection use TLS (default is true if server_port is 465)
    secure: true
    # Optional plain body:
    body: Build job of ${{github.repository}} completed successfully!
    # Optional HTML body read from file:
    html_body: file://README.html
    # Optional carbon copy recipients:
    cc: kyloren@example.com,leia@example.com
    # Optional blind carbon copy recipients:
    bcc: r2d2@example.com,hansolo@example.com
    # Optional recipient of the email response:
    reply_to: luke@example.com
    # Optional Message ID this message is replying to:
    in_reply_to: <random-luke@example.com>
    # Optional unsigned/invalid certificates allowance:
    ignore_cert: true
    # Optional converting Markdown to HTML (set content_type to text/html too):
    convert_markdown: true
    # Optional attachments:
    attachments: attachments.zip,git.diff,./dist/static/*.js
    # Optional priority: 'high', 'normal' (default) or 'low'
    priority: low
```

---

References:

1. [dawidd6/action-send-mail: A GitHub Action to send an email to multiple recipients](https://github.com/dawidd6/action-send-mail)
