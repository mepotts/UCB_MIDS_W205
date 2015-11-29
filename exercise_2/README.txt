This is a step-by-step guide to run the Twitter streaming application for W205 exercise 2.

This guide assumes a user starts a fresh instance from ucbw205_complete_plus_postgres_PY2.7.

1. Install Python 2.7 and change python version to 2.7
$ sudo yum install python27-devel -y
$ mv /usr/bin/python /usr/bin/python266
$ ln -s /usr/bin/python2.7 /usr/bin/python

2. Install ez_setup and pip:
$ sudo curl -o ez_setup.py https://bootstrap.pypa.io/ezsetup.py
$ sudo python ez_setup.py
$ sudo /usr/bin/easy_install-2.7 pip
$ sudo pip install virtualenv

3. Install lein
$ wget --directory-prefix=/usr/bin/ https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein
$ chmod a+x /usr/bin/lein
$ sudo /usr/bin/lein
$ lein version

4. Install streamparse
$ pip install streamparse

5. Install the dependencies for the Twitter streaming application
$ pip install psycopg2
$ pip install tweepy
$ git clone https://github.com/tweepy/tweepy.git
$ cd tweepy
$ python setup.py install

6. Start the postgres server
$ service postgresql initdb
$ sudo /etc/init.d/postgresql restart

7. Change the password for user 'postgres' and create the database Tcount
$ sudo -u postgres psql -c "ALTER USER postgres PASSWORD 'postgres';"
$ sudo /etc/init.d/postgresql reload (???)
$ sudo -u postgres createdb -O postgres Tcount

8. Checkout the code from Max's Github account
$ git clone https://github.com/maxyan/UCB_MIDS_W205.git

9. Enter the streaming application directory and run the application
$ cd UCB_MIDS_W205/exercise_2/EX2Tweetwordcount/
$ sparse run