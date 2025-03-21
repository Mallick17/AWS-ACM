## **Terraform for ACM**
Below is a Terraform script to request an SSL certificate:

```hcl
resource "aws_acm_certificate" "my_cert" {
  domain_name       = "example.com"
  validation_method = "DNS"

  lifecycle {
    create_before_destroy = true
  }
}
```

To validate using Route 53:

```hcl
resource "aws_route53_record" "cert_validation" {
  for_each = {
    for dvo in aws_acm_certificate.my_cert.domain_validation_options : dvo.domain_name => {
      name  = dvo.resource_record_name
      type  = dvo.resource_record_type
      value = dvo.resource_record_value
    }
  }

  zone_id = aws_route53_zone.example.id
  name    = each.value.name
  type    = each.value.type
  records = [each.value.value]
  ttl     = 60
}
```

#### **Deploy Using Terraform**
1. Save as `acm.tf`.
2. Run:
   ```sh
   terraform init
   terraform apply -auto-approve
   ```
3. ACM certificate will be issued and validated.

---
