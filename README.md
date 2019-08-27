
# rnd_syslog
Downloads random RFC-Files from the IETF-Webpage (<a href="https://tools.ietf.org/">https://tools.ietf.org/</a>) to generate/simulate some pseudo random "syslog"-Entries. Currently it don't uses the syslog-API directly, it just writes the generated messages to a MySQL/MariaDB-Database.
The purpose of this applicatation is to develop/test syslog Frontend which uses as backend a database.

Some example of such (Web-)Frontends:
* LogAnalyzer (<a href="https://loganalyzer.adiscon.com/download/">https://loganalyzer.adiscon.com/download/</a>)
* WebSysLog (<a href="https://github.com/SnipeLike/WebSysLog">https://github.com/SnipeLike/WebSysLog</a>)

## SQL
### Create DB and TABLE
    create database syslog;
    create table syslog.syslog (
     id int(10) AUTO_INCREMENT PRIMARY KEY,
     timestamp datetime,
     host varchar(60),
     tag varchar(60),
     level smallint(6),
     msg text
    ) ENGINE MyISAM;

### Add syslog-User
    create user syslog.'%' identified by '7f1$GRQ;MMGfhNXyElm';
    grant UPDATE,SELECT,INSERT,DELETE on syslog.* to syslog;
    flush privileges;
