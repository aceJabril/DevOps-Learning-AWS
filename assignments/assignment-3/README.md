# AWS Assignment 3
# S3 Static Website + CloudFront CDN + Route 53

---

# Project Overview

This project demonstrates a production-style static website deployment using core AWS services.

The objective was to design and implement a complete hosting architecture using:

- Amazon S3 for static website hosting
- Amazon CloudFront for CDN, HTTPS enforcement, and caching
- Amazon Route 53 for DNS routing

This assignment reflects a real-world DevOps workflow and strengthened my practical AWS implementation skills beyond theory.

---

# Architecture Overview

The final architecture follows this request flow:

User → Route 53 → CloudFront → S3 Static Website

Route 53 handles DNS resolution.
CloudFront acts as the CDN layer, providing HTTPS and caching.
S3 stores and serves the static website files.

This mirrors a real production-grade static hosting architecture.

Architecure diagram is shown here [Architecture](./architecture)

---

# S3 Static Website Configuration

A globally unique S3 bucket was created and configured for static website hosting.

Configuration included:

- Setting `index.html` as the index document
- Setting `error.html` as the error document
- Uploading website files
- Applying a bucket policy to allow public read access

This allowed the bucket to serve as a publicly accessible static website origin.

website data for index.html and error.html can be found here [website-data](./website-data)

---

# CloudFront Distribution Setup

A CloudFront distribution was created with the S3 website endpoint as the origin.

Configuration included:

- Viewer protocol policy set to redirect HTTP to HTTPS
- Allowed HTTP methods set to GET and HEAD
- Managed cache policy set to CachingOptimized
- Compress objects automatically enabled

The CloudFront distribution successfully routes traffic to the S3-hosted `index.html` file.

---

# Route 53 DNS Configuration

A hosted zone was created in Route 53.

An A record (Alias) was configured to point directly to the CloudFront distribution.

This completed the routing chain from domain → CDN → S3 origin.

---

# Testing and Validation

The deployment was validated by:

- Accessing the CloudFront distribution domain
- Confirming the static website loads correctly
- Verifying HTTPS redirection
- Confirming CloudFront is serving content from the S3 origin

This confirms the architecture functions as expected.

---

# What I Learned

This project significantly improved my understanding of:

- S3 bucket permissions and public access configuration
- CDN caching behaviour and CloudFront distribution settings
- DNS routing using Route 53 and alias records
- How AWS services integrate in a real-world deployment

The assignment helped bridge the gap between theoretical AWS knowledge and practical cloud implementation.

---

# Challenges Faced

- Understanding DNS resolution and hosted zone behaviour
- Configuring CloudFront origin settings correctly
- Managing S3 bucket policies without causing 403 access errors
- Navigating updated AWS console interfaces

Working through these challenges strengthened my troubleshooting and deployment skills.

---

# Evidence

All configuration screenshots, architecture visuals, routing validation, bucket policy setup, CloudFront distribution settings, and live deployment proof can be found in the [View Screenshots](screenshots/) directory of this repository.

