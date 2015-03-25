# Introduction

Provides a wrapper around drupal_http_request() that will, by default, cache outgoing GET requests. Also defines an alter hook so that other modules can adjust if a request is cached or not.

## Requirements

No additional requirements.

## Usage

Just enable the module and it will start caching outgoing GET requests. More complex rules require implementing an alter hook.

### hook usage

```
/**
 * Implements hook_http_request_is_cacheable_alter().
 */
function MYMODULE_http_request_is_cacheable_alter(&$is_cacheable, $context) {

  // Try and limit to only Solr requests to minimize possible issues.
  $is_cacheable &= strpos($context['url'], '/solr/') !== FALSE;
}
```

## This project has been sponsored by:

**McMurry/TMG**

> McMurry/TMG is a world-leading, results-focused content marketing
> firm. We leverage the power of world-class content — in the form of
> the broad categories of video, websites, print and mobile — to keep
> our clients’ brands top of mind with their customers.  Visit
> [http://www.mcmurrytmg.com][1] for more information.

[1]: http://www.mcmurrytmg.com
