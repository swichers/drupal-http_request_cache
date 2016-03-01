# Introduction

Provides a wrapper around drupal_http_request() that will, by default, cache outgoing GET requests. Also defines an alter hook so that other modules can adjust if a request is cached or not.

## Requirements

No additional requirements.

## Installation

Install as usual, see [this guide][1] for further information.

## Usage

Just enable the module and it will start caching outgoing GET requests. More complex rules require implementing an alter hook.

Some basic configuration options are available under admin/config/system/request-cache.

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

[1]: http://drupal.org/documentation/install/modules-themes/modules-7
