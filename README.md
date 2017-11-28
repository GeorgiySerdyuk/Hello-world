# Hello-world
Дом. задание3
public abstract class BaseTaste {

    public static void main(String[] args) {

        WebDriver driver = getConfiguredDriver() ;
        driver.get("http://prestashop-automation.qatestlab.com.ua/admin147ajyvk0/");
        WebElement field = driver.findElement(By.id("email"));
        field.sendKeys("webinar.test@gmail.com");
        WebElement field1 = driver.findElement(By.id("passwd"));
        field1.sendKeys(" Xcg7299bnSmMuRLp9ITw");
        WebElement button = driver.findElement(By.name("submitLogin"));
        button.click();
        driver.manage().timeouts().implicitlyWait(20, TimeUnit.SECONDS);
        WebElement katalog = driver.findElement (By.cssSelector("#subtab-AdminCatalog > a > span"));
        Actions actions = new Actions(driver);
        actions.moveToElement(katalog).build().perform();

        WebElement kategorii = driver.findElement
                (By.linkText("категории"));
        kategorii.click();
        WebElement dobavit = driver.findElement(By.className("process-icon-new"));
        dobavit.click();
        WebElement field2 = driver.findElement(By.id("name_1"));
        field2.sendKeys("Пальто");
        WebElement sohranit = driver.findElement(By.className("process-icon-save"));
        sohranit.click();
        WebElement name = driver.findElement(By.name("categoryFilter_name")) ;
        name.sendKeys("Пальто");
        WebElement button1 = driver.findElement(By.name("submitFilter"));
        button1.click();
      }

    public static WebDriver initChromeDriver() {
        System.setProperty("webdriver.chrome.driver", System.getProperty("user.dir") + "/drivers/chromedriver.exe");
        ChromeOptions options = new ChromeOptions();
        options.addArguments("--start-maximized");
        return  new ChromeDriver(options);
    }
    public static EventFiringWebDriver getConfiguredDriver() {
        EventFiringWebDriver driver = new EventFiringWebDriver(initChromeDriver());
        driver.register(new ConsoleLoggingEventListener());
        return driver;



    }

}


