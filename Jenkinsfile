pipeline {
    agent { label 'slave' }
    stages {
            stage ('Download Required RPM') {
            steps { 
                echo 'Download Oracle Preinstallation RPM and the Oracle Database RPM packages'
                sh script: "sudo su - root bash -c 'curl -o oracle-database-preinstall-19c-1.0-1.el7.x86_64.rpm https://yum.oracle.com/repo/OracleLinux/OL7/latest/x86_64/getPackage/oracle-database-preinstall-19c-1.0-1.el7.x86_64.rpm'"
            }
        }
		    stage ('Install Required RPM') {
            steps { 
                echo 'Install Oracle Preinstallation RPM and the Oracle Database RPM packages'
                sh script: "sudo su - root bash -c 'yum -y install oracle-database-preinstall-19c'"
            }
        }
           stage ('Install Database Software') {
            steps { 
                echo 'Install Oracle Oracle RDBMS software'
                sh script: "sudo su - root bash -c 'cd /tmp; yum -y localinstall /u01/stage/oracle-database-ee-19c-1.0-1.x86_64.rpm'"
            }
        }
		    stage ('Delete RPM file') {
            steps { 
                echo 'Delete RPM and the Oracle Database RPM packages'
                sh script: "sudo su - root bash -c 'rm oracle-database-preinstall-19c-1.0-1.el7.x86_64.rpm'"
            }
        }
           stage ('Create Database') {
            steps { 
                echo 'Creating Oracle Oracle'
                sh script: "sudo su - root bash -c '/etc/init.d/oracledb_ORCLCDB-19c configure'"
            }
        }
      }
    }
