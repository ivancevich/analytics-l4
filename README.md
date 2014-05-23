# Analytics

Port of Laravel 3 bundle [lordcoste/analytics-s2s](https://github.com/lordcoste/analytics-s2s) for Laravel 4

## Installation

Add `ivancevich/analytics` to `composer.json`.

    "ivancevich/analytics": "dev-master"
    
Run `composer update` to pull down the latest version of Analytics.

Now open up `app/config/app.php` and add the service provider to your `providers` array.

    'providers' => array(
        'Ivancevich\Analytics\AnalyticsServiceProvider',
    )

Now add the alias.

    'aliases' => array(
        'Analytics' => 'Ivancevich\Analytics\AnalyticsFacade',
    )


## Configuration

Run `php artisan config:publish ivancevich/analytics` and modify the config file with your own informations.

## Usage
Querying the API for visits and pageviews in the last week.

More information about this calling the Google Analytics API can be found here https://developers.google.com/apis-explorer/#s/analytics/v3/analytics.data.ga.get
A list of all Google Analytics metrics can be found here https://developers.google.com/analytics/devguides/reporting/core/dimsmets
```php
$site_id = Analytics::getSiteIdByUrl('http://github.com/'); // return something like 'ga:11111111'

$stats = Analytics::query($siteID, '7daysAgo', 'yesterday', 'ga:visits,ga:pageviews');
```
