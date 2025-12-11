# 🐝 Why Yahoo Emails Were Marked as Spam (and How We Fixed It)

## Symptoms
- Emails from `@yahoo.com` → Rspamd `SPAM` flag, score > 15  
- Headers showed `ARC-Seal`, `ARC-Message-Signature`, but no `DKIM-Result: pass`

## Root Cause
- Yahoo uses **aggressive ARC validation**  
- Missing `local.d/multimap.conf` rule to whitelist Yahoo ARC chains  
- Rspamd Bayesian DB trained mostly on Gmail/Outlook → false positives

## Fix (Rspamd 3.8+)
```nginx
# /etc/rspamd/local.d/multimap.conf
YAHOO_ARC_WHITELIST {
  type = "header";
  header = "ARC-Authentication-Results";
  value = "yahoo.*?spf=pass.*?dkim=pass";
  description = "Whitelist Yahoo ARC-passed mail";
  score = -2.0;
  action = "no action";
}
