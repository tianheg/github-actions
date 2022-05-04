# Send Mail

```yml
# mail.yml

- name: Send mail
  uses: tianheg/github-actions@mail
  with:
    server_address: smtp.mailgun.org
    server_port: 465
    username: ${{secrets.MAIL_USERNAME}}
    password: ${{secrets.MAIL_PASSWORD}}
    subject: Github Actions job result
    to: obiwan@example.com,yoda@example.com
    from: Luke Skywalker # <user@example.com>
    body: Build job of ${{github.repository}} completed successfully!
    html_body: file://README.html
    cc: kyloren@example.com,leia@example.com
    bcc: r2d2@example.com,hansolo@example.com
    reply_to: luke@example.com
    in_reply_to: <random-luke@example.com>
    ignore_cert: true
    convert_markdown: true
    attachments: attachments.zip,git.diff,./dist/static/*.js
    priority: low
```

| Name                  | Requirement | Description |
| --------------------- | ----------- | ----------- |
| `server_address`        | _required_ | mail server address |
| `server_port`        | _required_ | mail server port |
| `username`           | _optional_ | (recommended) mail server username |
| `password`            | _optional_ | (recommended) mail server password |
| `subject`   | _required_ | mail subject |
| `to`  | _required_ | recipients' addresses |
| `from`           | _required_ | sender full name (address can be skipped) |
| `secure`          | _optional_(true/false) | whether this connection use TLS (default is true if server_port is 465) |
| `body` | _optional_ | plain body |
| `html_body` | _optional_ | HTML body read from file |
| `cc` | _optional_ | carbon copy recipients |
| `bcc` | _optional_ | blind carbon copy recipients |
| `reply_to` | _optional_ | recipient of the email response |
| `in_reply_to` | _optional_ | Message ID this message is replying to |
| ` ignore_cert` | _optional_(true/false) | unsigned/invalid certificates allowance |
| `convert_markdown` | _optional_ | converting Markdown to HTML (set content_type to text/html too) |
| `attachments` | _optional_ |  |
| `priority` | _optional_ | priority: 'high', 'normal' (default) or 'low' |

---

References:

1. [dawidd6/action-send-mail: A GitHub Action to send an email to multiple recipients](https://github.com/dawidd6/action-send-mail)
