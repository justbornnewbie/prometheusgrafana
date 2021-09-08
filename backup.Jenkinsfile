pipeline
{
    agent
    {
        label 'local'
    }

    stages
    {
        stage('take-backup')
        {
            
            steps{
                   sh '''
                   cname=$(docker ps| grep mysql | grep 3306 | awk '{print $1}')
                   d=$(date +%s)
                   docker exec -it $cname mysqldump -u root -proot --all-databases > /tmp/all_databases_$d.sql
                   docker cp $cname:/tmp/all_databases.sql /tmp
                   #aws s3 cp /tmp/all_databases.sql s://bucketname
                   #delete logic
                   '''
               }
        
        }
    }
}