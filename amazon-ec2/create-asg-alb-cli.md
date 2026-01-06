
## create auto scaling group

aws autoscaling create-auto-scaling-group --auto-scaling-group-name ASG2 --launch-template "LaunchTemplateName=rafal-webserver" --min-size 1 --max-size 3 --desired-capacity 2 --availability-zones "eu-west-2a" "eu-west-2b" --vpc-zone-identifier "subnet-0bdf8abb7ea3097ff, subnet-09bfdec8be91455bf"

## create load balancer, create listener, and attach to TG1 to ASG2

aws elbv2 create-load-balancer --name ALB2 --subnets subnet-0bdf8abb7ea3097ff subnet-09bfdec8be91455bf --security-groups sg-018ede4e9bde771c6

aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:eu-west-2:367573295024:loadbalancer/app/ALB2/443efddf0edcd1aa --protocol HTTP --port 80 --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:eu-west-2:367573295024:targetgroup/rafal-target-group/7398cbbdfc90cf93

aws autoscaling attach-load-balancer-target-groups --auto-scaling-group-name ASG2 --target-group-arns arn:aws:elasticloadbalancing:eu-west-2:367573295024:targetgroup/rafal-target-group/7398cbbdfc90cf93

## delete ASG2 and ALB2

aws elbv2 delete-load-balancer --load-balancer-arn arn:aws:elasticloadbalancing:eu-west-2:367573295024:loadbalancer/app/ALB2/443efddf0edcd1aa

aws autoscaling delete-auto-scaling-group --auto-scaling-group-name ASG2 --force-delete