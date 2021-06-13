# AWSTasks

<!DOCTYPE html>
<html>
    <head>
        <title>Amazon Web Services | Task 3</title>
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css" crossorigin="anonymous">
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.min.js" crossorigin="anonymous"></script>
    </head>
    <body>
    <div class="container">           
        <h2 style="text-align: center; color: #28CCFD;">Deploy Wordpress on webserver using EC2</h2>
        <div class="list-group">
            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">1. First We need to configure command terminal for AWS cli -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ aws configure</pre></em>
            <span class="border border-warning"><img src="Media/1.JPG" class="img-fluid" alt="Login AWS" style="margin-bottom: 2px;"></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">2. Creating Security Key Pair for SSH -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ aws ec2 create-key-pair --key-name 'awstask5' --output text > filename.pem</pre></em>
            <span class="border border-warning"><img src="Media/2.JPG" class="img-fluid" alt="Security Key Creation"></span><br>
            <span class="border border-warning"><img src="Media/2A.JPG" class="img-fluid" alt="Security Key Creation"></span><br>
            <span class="border border-warning"><img src="Media/2B.JPG" class="img-fluid" alt="Security Key Creation""></span>
            
            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">3. Creating Security Group for Inbound and Outbound Traffic -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ aws ec2 create-security-group --group-name SG_task5 --description AWSTASK5</pre></em>
            <span class="border border-warning"><img src="Media/3.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/3A.JPG" class="img-fluid" alt="Security Group"></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">4. Assigning SSH : 22 and HTTP :80 inbound traffic  -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ aws ec2 authorize-security-group-ingress --group-name SG_task5 --protocol tcp --port 22 --cidr 0.0.0.0/0</pre></em>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ aws ec2 authorize-security-group-ingress --group-name SG_task5 --protocol tcp --port 80 --cidr 0.0.0.0/0</pre></em>
            <span class="border border-warning"><img src="Media/4.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/4A.JPG" class="img-fluid" alt="Security Group"></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">5. Launching EC2 Instance with above created Security Group and Key pair  -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ aws ec2 run-instances --image-id ami-0ad704c126371a549 --count 1 --instance-type t2.micro --key-name 'awstask5' --security-group-ids <br>sg-0b896d9c0aeff05d7 --subnet-id subnet-0f2f399c11b6bd931</pre></em>
            <span class="border border-warning"><img src="Media/5.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/5A.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/5B.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/5C.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/5D.JPG" class="img-fluid" alt="Security Group"></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">6. Retriving Public IP and Connect through PuTTY -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ aws ec2 describe-instances --filters "Name=image-id,Values=ami-0ad704c126371a549</pre></em>
            <span class="border border-warning"><img src="Media/5E.JPG" class="img-fluid" alt="Security Group"></span><br>
            <h4><span class="badge bg-danger">Login to EC2 instance through SSh or PuTYY</span></h4>
            <span class="border border-warning"><center><img src="Media/6.JPG" class="img-fluid" alt="Security Group"></center></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">7. Installation of Apache Webserver and PHP -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ sudo su <br>$ yum install httpd -y<br>$ yum install php -y<br>$ systemctl status httpd<br>$ systemctl start  httpd<br>$ systemctl enable httpd</pre></em>
            <span class="border border-warning"><img src="Media/7.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/7A.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/8B.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/8.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/8A.JPG" class="img-fluid" alt="Security Group"></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">8. Download Wordpress, Extract and copy to WWW Directory -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ wget https://wordpress.org/latest.zip <br>$ unzip latest.zip <br>$ cd wordpress<br>$ cp -r * /var/www/html</pre></em>
            <span class="border border-warning"><img src="Media/9.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/9A.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/9B.JPG" class="img-fluid" alt="Security Group"></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">9. Creating RDS (Free Tier) Using CMD CLI -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$ aws rds create-db-instance --db-instance-identifier wp-db --db-instance-class db.t2.micro --engine mysql --master-username admin<br> --master-user-password secret99 --allocated-storage 20</pre></em>
            <span class="border border-warning"><img src="Media/10.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/10A.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/10B.JPG" class="img-fluid" alt="Security Group"></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">10. Connecting to RDS and creating Database for Wordpress -</a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">$  mysql -h wp-db.cqep3u80wt6b.ap-south-1.rds.amazonaws.com -u admin -p<br>Enter Password: <br>mysql> show databases; <br>mysql> create database wp_db;</pre></em>
            <h4><span class="badge bg-danger">Login to Local Linux system to access MYSQL : </span></h4>
            <span class="border border-warning"><img src="Media/11.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/11A.JPG" class="img-fluid" alt="Security Group"></span>

            <a href="#" class="list-group-item list-group-item-action list-group-item-info" style="margin-top: 2em;">11. Setup Wordpress - </a>
            <em><pre style="margin-left: 2em; margin-top: 0.5em; color: grey; font-size: 1em;">Go to webbrowser and access the website site-<br>http://65.0.124.236/wp-admin/setup-config.php<br>Use database, username , password and endpoint or IP to connect and finalize setup.</pre></em>
            <span class="border border-warning"><img src="Media/12.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/12A.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/12B.JPG" class="img-fluid" alt="Security Group"></span><br>
            <span class="border border-warning"><img src="Media/12C.JPG" class="img-fluid" alt="Security Group"></span><br>
            <h4><span class="badge bg-success">Website Frontend or End user Interface : </span></h4>
            <span class="border border-warning"><img src="Media/12D FE.JPG" class="img-fluid" alt="Security Group"></span><br>
            <h4><span class="badge bg-success">Website Backend or Admin Panel : </span></h4>
            <span class="border border-warning"><img src="Media/12E BE.JPG" class="img-fluid" alt="Security Group"></span><br>
        </div>   
    </div>

        

    </body>
</html>
