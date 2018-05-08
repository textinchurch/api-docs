---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://textinchurch.com/developer' target="_blank>Sign up for an Authentication Key</a>
  - <a href='https://github.com/lord/slate' target="_blank">Documentation Powered by Slate</a>

includes:
  - authentication
  - people
  - groups
  - errors

search: true
---

# Introduction

Welcome to Text In Church's API! You can use this API to access all our API endpoints, such as the Person API to look up or create people, or the Groups API to create a new group.

The API is organized around REST. All requests should be made over SSL. All request and response bodies, including errors, are encoded in JSON.

# Rate Limiting

Usually the API is rate limited to 100 requests per 20 seconds per user, but that limit and time period are subject to change either up or down as necessary. If you think your app may be affected by rate limits, it should be developed to adjust dynamically inspecting the values of X-PCO-API-Request-Rate-Limit and X-PCO-API-Request-Rate-Period in the HTTP headers. Your current count is discoverable in the X-PCO-API-Request-Rate-Count key. Requests that exceed the current limit will return an HTTP status 429. The number of seconds to wait until you can retry those requests is in the key Retry-After.
