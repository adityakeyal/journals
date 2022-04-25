---
title: "Ghostscript Cheatsheet"
date: 2022-04-25T17:34:55+05:30
math: false
tags: [ghostscript]
categories: []
---

// Remove password protection

gswin64c -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=OUTPUT.pdf -sPDFPassword=PASSWORD -f ENCRYPTED.pdf

// Extract to text

gswin64c -q -dNOPAUSE -dBATCH -sDEVICE=txtwrite -sPDFPassword=A0084 -o output.txt 1Encrypt10665_202104.pdf
