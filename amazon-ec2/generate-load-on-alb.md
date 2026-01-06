# Command to generate load on the ALB

***replace with your alb dns name***
```for i in {1..200}; do curl rafal-load-balancer-1820362999.eu-west-2.elb.amazonaws.com & done; wait```
