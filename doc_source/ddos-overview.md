# How AWS Shield Works<a name="ddos-overview"></a>

A distributed denial of service \(DDoS\) attack is an attack in which multiple compromised systems attempt to flood a target, such as a network or web application, with traffic\. A DDoS attack can prevent legitimate users from accessing a service and can cause the system to crash due to the overwhelming traffic volume\. 

AWS provides two levels of protection against DDoS attacks: AWS Shield Standard and AWS Shield Advanced\. 

## AWS Shield Standard<a name="ddos-standard"></a>

AWS services and technologies are built from the ground up to provide resilience in the face of network and transport layer DDoS attacks\. For web application attacks, you also can use AWS WAF to configure web access control lists \(web ACLs\) that target network layer DDoS request patterns and help to minimize the effects of a DDoS attack\. This DDoS protection, known as AWS Shield Standard, is included with AWS WAF\. AWS Shield Standard is provided at no additional cost beyond what you are already paying for AWS WAF and your other AWS services\. 

## AWS Shield Advanced<a name="ddos-advanced"></a>

AWS Shield Advanced provides expanded DDoS attack protection for your Elastic Load Balancing load balancers, CloudFront distributions, and Amazon Route 53 hosted zones\.

AWS Shield Advanced includes intelligent DDoS attack detection and mitigation for not only for network layer \(layer 3\) and transport layer \(layer 4\) attacks, but also for application layer \(layer 7\) attacks\. As an AWS Shield Advanced customer, you can contact a 24x7 DDoS response team \(DRT\) for assistance during a DDoS attack\. You also have exclusive access to advanced, real\-time metrics and reports for extensive visibility into attacks on your AWS resources\. 

AWS Shield Advanced also offers some cost protection against spikes in your AWS bill that could result from a DDoS attack\. This cost protection is provided for your Elastic Load Balancing load balancers, CloudFront distributions, and Amazon Route 53 hosted zones\.

AWS WAF is included with AWS Shield Advanced at no extra cost\. For more information about AWS Shield Advanced pricing, see [AWS Shield Advanced Pricing](http://aws.amazon.com/shield/pricing/)\.

## Types of DDoS Attacks<a name="types-of-ddos-attacks"></a>

AWS Shield Advanced provides expanded protection against many types of attacks\. For example:

**User Datagram Protocol \(UDP\) reflection attacks**  
An attacker can spoof the source of a request and use UDP to elicit a large response from the server\. The extra network traffic directed towards the spoofed, attacked IP address can slow the targeted server and prevent legitimate users from accessing needed resources\.

**SYN flood**  
The intent of an SYN flood attack is to exhaust the available resources of a system by leaving connections in a half\-open state\. When a user connects to a TCP service like a web server, the client sends a SYN packet\. The server returns an acknowledgment, and the client returns its own acknowledgement, completing the three\-way handshake\. In an SYN flood, the third acknowledgment is never returned, and the server is left waiting for a response\. This can prevent other users from connecting to the server\. 

**DNS query flood**  
In a DNS query flood, an attacker uses multiple DNS queries to exhaust the resources of a DNS server\. AWS Shield Advanced can help provide protection against DNS query flood attacks on Amazon Route 53 DNS servers\.

**HTTP flood/cache\-busting \(layer 7\) attacks**  
With an HTTP flood, including GET and POST floods, an attacker sends multiple HTTP requests that appear to be from a real user of the web application\. Cache\-busting attacks are a type of HTTP flood that uses variations in the HTTP request's query string that prevent use of edge\-located cached content and forces the content to be served from the origin web server, causing additional and potentially damaging strain on the origin web server\. 

## About the AWS DDoS Response Team \(DRT\)<a name="ddos-drt"></a>

With AWS Shield Advanced, complex DDoS events can be escalated to the AWS DDoS Response team \(DRT\), which has deep experience in protecting AWS, Amazon\.com, and its subsidiaries\.

For layer 3 and layer 4 attacks, AWS provides automatic attack detection and proactively applies mitigations on your behalf\. For layer 7 DDoS attacks, AWS attempts to detect and notify AWS Shield Advanced customers through CloudWatch alarms, but does not apply mitigations proactively\. This is to avoid inadvertently dropping valid user traffic\.

AWS Shield Advanced customers have two options to mitigate layer 7 attacks:

+ **Provide your own mitigations:** AWS WAF is included with AWS Shield Advanced at no extra cost\. You can create your own AWS WAF rules to mitigate the DDoS attacks\. AWS provides preconfigured templates to get you started quickly\. The templates include a set of AWS WAF rules that are designed to block common web\-based attacks\. You can customize the templates to fit your business needs\. For more information, see [AWS WAF Security Automations](https://aws.amazon.com/answers/security/aws-waf-security-automations/)\.

  In this case, the DRT is not involved\. You can, however, engage the DRT for guidance on implementing best practices such as AWS WAF common protections\.

+ **Engage the DRT:** If you want additional support in addressing an attack, you can contact the [AWS Support Center](https://console.aws.amazon.com/support/home#/)\. Critical and urgent cases are routed directly to DDoS experts\. With AWS Shield Advanced, complex cases can be escalated to the DRT, which has deep experience in protecting AWS, Amazon\.com, and its subsidiaries\. If you are an AWS Shield Advanced customer, you also can request special handling instructions for high severity cases\.

  The response time for your case depends on the severity that you select and the response times, which are documented on the [AWS Support Plans](https://aws.amazon.com/premiumsupport/compare-plans/) page\.

  The DRT helps you triage the DDoS attack to identify attack signatures and patterns\. With your consent, the DRT creates and deploys AWS WAF rules to mitigate the attack\.

When AWS Shield Advanced detects a large layer 7 attack against one of your applications, the DRT might proactively contact you\. The DRT triages the DDoS incident and creates AWS WAF mitigations\. The DRT then contacts you for consent to apply the AWS WAF rules\. 

**Important**  
The DRT can help you to analyze suspicious activity and assist you to mitigate the issue\. This mitigation often requires the DRT to create or update web access control lists \(web ACLs\) in your account\. However, they need your permission to do so\. We recommend that as part of enabling AWS Shield Advanced, you follow the steps in [Step 3: Authorize the DDoS Response Team to Create Rules and Web ACLs on Your Behalf](authorize-DRT.md) to proactively provide the DRT with the needed permissions\. Providing permission ahead of time helps prevent any delays in the event of an actual attack\.

## Help Me Choose a Protection Plan<a name="ddos-help-me-choose"></a>

In many cases, AWS Shield Standard protection is sufficient for your needs\. AWS services and technologies are built to provide resilience in the face of the most common DDoS attacks\. Supplementing this built\-in protection with AWS WAF and a combination of other AWS services as a defense\-in\-depth strategy typically provides adequate attack protection and mitigation\. Further, if you have the technical expertise and want full control over monitoring for and mitigating layer 7 attacks, AWS Shield Standard is likely the appropriate choice\. For additional resources to help you design your own DDoS protection, see our [Tutorials](tutorials.md)\. 

If your business or industry is a likely target of DDoS attacks, or if you prefer to let AWS handle the majority of DDoS protection and mitigation responsibilities for layer 3, layer 4, and layer 7 attacks, AWS Shield Advanced might be the best choice\. AWS Shield Advanced not only provides layer 3 and layer 4 protection and mitigation, but also includes AWS WAF at no extra charge and DRT assistance for layer 7 attacks\. If you use AWS WAF and AWS Shield Standard, you must design your own layer 7 protection and mitigation processes\.

AWS Shield Advanced customers also benefit from detailed information about DDoS attacks against their AWS resources\. While AWS Shield Standard provides automatic protection for the most common layer 3 and layer 4 attacks, visibility into the details of those attacks is limited\. AWS Shield Advanced provides you with extensive data about the details of both layer 3, layer 4, and layer 7 DDoS attacks\. 

AWS Shield Advanced also offers cost protection for DDoS attacks against your AWS resources\. This valuable feature helps prevent unexpected spikes in your bill caused by DDoS attacks\. If cost predictability is important to you, AWS Shield Advanced can offer that stability\.

The following table shows a comparison of AWS Shield Standard and AWS Shield Advanced\.


| Feature | AWS Shield Standard | AWS Shield Advanced | 
| --- | --- | --- | 
| Active Monitoring | 
| Network flow monitoring | Yes | Yes | 
| Automatic always\-on detection | Yes | Yes | 
| Automated application \(layer 7\) traffic monitoring |  | Yes | 
| DDoS Mitigations | 
| Helps protect against common DDoS attacks, such as SYN flood and UDP reflection attacks | Yes | Yes | 
| Access to additional DDoS mitigation capacity |  | Yes | 
| Custom application layer \(layer 7\) mitigations | Yes, through user\-created AWS WAF ACLs\. Incurs standard AWS WAF charges\. | Yes, through user\-created or DRT\-created AWS WAF ACLs\. Included as part of the AWS Shield Advanced subscription\. | 
| Instant rule updates | Yes, through user\-created AWS WAF ACLs\. Incurs standard AWS WAF charges\. | Yes | 
| AWS WAF for app vulnerability protection | Yes, through user\-created AWS WAF ACLs\. Incurs standard AWS WAF charges\. | Yes | 
| Visibility and Reporting | 
| Layer 3/4 attack notification |  | Yes | 
| Layer 3/4 attack forensics reports \(source IP, attack vector, and more\) |  | Yes | 
| Layer 7 attack notification | Yes, through AWS WAF\. Incurs standard AWS WAF charges\. | Yes | 
| Layer 7 attack forensics reports \(Top talkers report, sampled requests, and more\) | Yes, through AWS WAF\. Incurs standard AWS WAF charges\. | Yes | 
| Layer 3/4/7 attack historical report |  | Yes | 
| DDoS Response Team Support | 
| Incident management during high severity events |  | Yes | 
| Custom mitigations during attacks |  | Yes | 
| Post\-attack analysis |  | Yes | 
| Cost Protection | 
| Reimburse Amazon Route 53 DNS DDoS charges |  | Yes | 
| Reimburse CloudFront DDoS charges |  | Yes | 
| Reimburse Elastic Load Balancing \(ELB\) DDoS charges |  | Yes | 

**Note**  
Although both AWS Shield Standard and AWS Shield Advanced provide significant protection against DDoS attacks, we recommend that you also use Amazon CloudWatch and AWS CloudTrail to monitor all of your AWS services\. For information about monitoring AWS WAF by using CloudWatch and CloudTrail, see [Monitoring AWS WAF and AWS Shield Advanced](monitoring_overview.md) and [Logging AWS WAF API Calls with AWS CloudTrail](logging-using-cloudtrail.md)\. 