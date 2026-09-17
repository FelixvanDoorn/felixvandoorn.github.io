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

TODO: architecture, components, the interesting technical decisions.

## What I learned

TODO: findings, gotchas, next steps.
