---
title: FAQ
pcx_content_type: faq
weight: 10
meta:
  title: FAQ — Bulk Redirects
---

# FAQ — Bulk Redirects

Below you will find answers to the most commonly asked questions regarding Bulk Redirects.

To troubleshoot runtime errors related to Bulk Redirects, refer to [Troubleshooting Cloudflare 10XXX Errors](https://support.cloudflare.com/hc/articles/4425107232525).

## What happens if the same source URL appears in two different Bulk Redirect Lists?

In this situation, Cloudflare will use the URL redirect of the first rule that triggers. This will be determined by the order of the Bulk Redirect Rules enabling each Bulk Redirect List in the `http_request_redirect` phase entry point ruleset.

## How can I solve the following error: "This account has reached the limit on the number of URL matching items on the same hostname/path"?

You may get this error when adding items to a Bulk Redirect List.

You can have any number of URL redirects with the same source hostname (with different paths) or same source path (with different hostnames). However, you can have a maximum of 16 source URLs with the same hostname and path across all lists, either enabled by a Bulk Redirect Rule or not.

If you receive this error, check if you have any unused Bulk Redirect Lists with the source hostname and path that caused the error, and remove such items from the list.

## How many URL redirects can I have in a single Bulk Redirect List?

Each account has a maximum number of URL redirects across all lists which depends on your Cloudflare plan. If you wish, you can use all the URL redirects available in your plan in a single Bulk Redirect List, but you will not be able to create any other URL redirects in a different list. Refer to [Availability](/rules/url-forwarding/#availability) for more information.

## How can I redirect based on the non-normalized version of a URL?

Use the `raw.http.request.full_uri` field both in the rule expression and in the key, instead of the default field `http.request.full_uri`. This will take the raw version of the URL into account, that is, the URL received on the Cloudflare global network before applying {{<glossary-tooltip term_id="URL normalization">}}normalization{{</glossary-tooltip>}}. Refer to [Concepts: Bulk Redirect Rules](/rules/url-forwarding/bulk-redirects/concepts/#bulk-redirect-rules) for more information on using a custom rule expression and a custom key.

## Do Bulk Redirects take precedence over Page Rules?

Yes. Bulk Redirects take precedence over Page Rules redirects. For more information on the execution order of Rules products, refer to [Execution order](/rules/url-forwarding/#execution-order).