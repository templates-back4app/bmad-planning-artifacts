---
title: "Product Brief: Community Library Borrowing Log"
status: draft
created: 2026-09-23
updated: 2026-09-23
---

# Product Brief: Community Library Borrowing Log

## Executive Summary

A neighbourhood library of roughly 1,200 donated books is run by six volunteers on rotating shifts. Borrowing is recorded in a paper notebook at the desk: name, title, date out, date back. The notebook works while a volunteer is standing next to it and fails the moment anyone needs to answer a question away from the desk — who has this book, what is overdue, which titles never come back.

This product replaces the notebook with a single shared record that any volunteer can read from their phone. It does not attempt to be a library management system. It records loans and returns, shows what is out and what is late, and survives the handover between one volunteer's shift and the next.

The reason to build it now is that the library has just been given a second room and expects the collection to roughly double. The notebook is already the slowest part of a shift; at twice the volume it stops working entirely.

## The Problem

The notebook has one copy and one location. A volunteer at home cannot check whether a book is out. Two volunteers on the same shift cannot both write in it. When a page is full, the history is effectively gone — nobody re-reads old pages.

Overdue books are the concrete cost. Nobody can tell what is late without reading every open line in the notebook and doing date arithmetic by hand, so in practice nobody does. The volunteers' own estimate is that they lose 30 to 50 books a year, which at donated-replacement effort is several weekends of sorting and shelving.

The coping mechanism today is memory and goodwill. It works because the volunteers know most of the borrowers personally. That is exactly what stops working as the collection and the borrower list grow.

## The Solution

A phone-first web page with three things on it: a search box over the collection, a list of what is currently out, and a list of what is overdue. Recording a loan takes two taps and a name. Recording a return takes one.

The volunteer never sees a form with fifteen fields. The system holds the small number of facts that matter — which copy, which borrower, out when, due when, back when — and computes everything else.

Nothing is required of the borrower. There is no borrower login, no app to install, no card to carry. The volunteer at the desk is the only user, because that is the only workflow the library actually has.

## What Makes This Different

Nothing about this is technically novel, and the brief should not pretend otherwise. The advantage is fit: existing library software assumes a cataloguer, a barcode scanner and a membership database, and the setup cost of any of them exceeds the value of solving this library's actual problem.

The honest moat is scope discipline. This is a product that stays small on purpose, and the risk to it is feature creep from well-meaning volunteers rather than competition.

## Who This Serves

The six volunteers, on shift, standing up, one-handed, on their own phones. Half of them are over seventy. The interface has to work at arm's length with large text and no training.

The library coordinator is a secondary user with one extra need: a weekly view of what is overdue so she can send reminders. She is the only person who will ever use this sitting down.

## Success Criteria

The notebook is not used for four consecutive weeks. That is the single signal that the product replaced the thing rather than sitting alongside it.

Supporting measures: recording a loan takes under fifteen seconds from unlocked phone to confirmation; the overdue list is accurate enough that the coordinator sends reminders from it without cross-checking; and the number of books unaccounted for after a year is materially below the current 30 to 50.

## Scope

In, for the first version: search the collection, record a loan, record a return, list what is out, list what is overdue, and a weekly overdue summary for the coordinator.

Out, explicitly: borrower accounts, reservations, fines, barcodes, acquisition and cataloguing workflows, reporting beyond the overdue list, and any notification the system sends by itself. Adding the collection is a one-time import from the existing spreadsheet, not a feature.

## Open Questions

Whether the existing spreadsheet of the collection is accurate enough to import as-is is unknown and needs checking before any build starts — if it is not, the first version's real work is data cleanup rather than software.

It is also unresolved whether two volunteers editing the same loan at the same time is a real scenario or a theoretical one. The answer changes whether conflict handling is needed in version one.

## Vision

If it works, the same record becomes the library's memory: which books actually circulate, which sit untouched for three years, what the collection should accept and what it should decline. That turns a borrowing log into an acquisitions argument, which is the thing the coordinator actually wants and cannot get today.
