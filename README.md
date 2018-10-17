# Automated-Testing

var webdriver = require('selenium-webdriver'),
    By = webdriver.By,
    until = webdriver.until,
    username = "mbarron62",
    accessKey = "5ab48f59-6e64-4c85-ad27-2417db38a4a0";

var driver = new webdriver.Builder()-
    .withCapabilities({
      'browserName': 'chrome',
      'platform': 'Windows XP',
      'version': '43.0',
      'username': mbarron62,
      'accessKey': 5ab48f59-6e64-4c85-ad27-2417db38a4a0
    })
    .usingServer("https://" + username + ":" + accessKey +
          "@ondemand.saucelabs.com:443/wd/hub")
    .build();

driver.get('http://www.google.com');

driver.findElement(By.name('q')).sendKeys('webdriver');

driver.sleep(1000).then(function() {
  driver.findElement(By.name('q')).sendKeys(webdriver.Key.TAB);
});

driver.findElement(By.name('btnK')).click();

driver.sleep(2000).then(function() {
  driver.getTitle().then(function(title) {
    if(title === 'webdriver - Google Search') {
      console.log('Test passed');
    } else {
      console.log('Test failed');
    }
  });
});

driver.quit();
