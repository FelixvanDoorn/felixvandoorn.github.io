---
title: "Bear Trap: Catching Bots, Scanners and Maybe an AI Agent or Two"
description: "Who shows up when you leave out an exposed server on the internet"
series: "tech"
pubDate: "Sep 15 2026"
---




## What it is

Bear Trap is an experimental honeypot setup, aimed at threat data collection and analyzing the effectiveness of specific honeypot configurations. It combines two Cowrie honeypot nodes: a vanilla version on AWS, and a version modified to attempt prompt injection on Azure. The logs of both honeypots are forwarded to a GCP sink node using Vector and transformed into analysis-ready data in BigQuery.

## Why I built it
When OpenClaw was having its 15 minutes of fame, I was really intrigued by the implications from a security perspective. The warnings from experts were clear and abundant, but I was interested to see actual data on how this was going to play out. 

I wanted to know if I could find who was trying to use agents for intrusion and who was trying to capitalize on the opportunity presented by the new wave of AI users and builders. What better way to answer that question than to collect and analyze the data yourself? 

## How it works

The intial version of this consists of three components: A "control node", configured to capture traffic using a "vanilla" Cowrie node in order for us to establish baseline behavior. The "agent-node" is also based on Cowrie, but is paired with custom Python scripts that attempt prompt injection once commands from a predfined list are attempted inside our honeypot node. 



## What I learned


I had not used Github Actions for CI/CD and was pleasantly surprised. 
Working with Vector for log forwarding was also a new experience. I had some initial trouble getting the structure of vector.toml to work, even with some heavy-handed Claude sessions but it was blazing fast afterwards. 


## What I want to learn after this project

Infrastructure as Code: This past few years I've had the luxury of working in Big Tech teams where world-class, dedicated infra teams took care of everything. While I was able to get this project off the ground in terms of setup, it doesn't scale very well to new nodes. Shifting to programmatic approaches offered by IaC tools such as Terraform or OpenTofu is a skill I was inspired to pick up after this project. 

