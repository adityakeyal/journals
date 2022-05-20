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

gswin64c -q -dNOPAUSE -dBATCH -sDEVICE=txtwrite-%d -sPDFPassword=PASSWORD -o output.txt <filename>.pdf
