## Setting up the environment

1. Check out the `activerecord-jdbc-adapter` repository

        cd ~/rails
        git clone git@github.com:eazybi/activerecord-jdbc-adapter.git

2. Go to the `activerecord-jdbc-adapter` folder and create the `.rvmrc` file

        cd activerecord-jdbc-adapter
        cat > .rvmrc <<RVMRC
        rvm jruby-9.2.12.0@activerecord_jdbc_adapter --create
        RVMRC

3. Load RVM configuration

        cd ~/rails/activerecord-jdbc-adapter

4. Run the `bundle` command with the specified ActiveRecord version
        AR_VERSION=4.2.11 bundle


## Building the JAR file

1. Run the `jar` `rake` task to build `adapter_java.jar` file

        rake jar

2. Copy the `adapter_java.jar` file to the eazybi repository

        cp lib/arjdbc/jdbc/adapter_java.jar ../eazybi/lib/arjdbc/jdbc/


## Running AR-JDBC's Tests

1. Install MySQL 8.x database

2. Make sure that there is a database user `root` without a password or
   use environment variables MY_USER and MY_PASSWORD to run the tests rake task

3. Install required gems

        gem install bundler -v1.14.3
        BUNDLE_GEMFILE=gemfiles/rails42.gemfile bundle

4. Run MySQL adapter tests

        rake appraisal:rails42 test_mysql
