# hello-world
package com.Ecommerce.BaseClass;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.Properties;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class TestBase {

	public static WebDriver driver;
	public static Properties prop;
	
	public TestBase() {
		try {
			
		 prop=new Properties();
		 FileInputStream fp=new FileInputStream("E:\\Practice progtams\\Live_Project\\src\\main\\java\\com\\Ecommerce\\qa\\Config\\config.properties");
		 prop.load(fp);
		  
				
				
		}
		
		catch(FileNotFoundException e) {
			e.printStackTrace();
		}
		
		catch(IOException e) {
			e.printStackTrace();
		}
	}
	
	
	public static void Initialisation() {
		
		String Browser =prop.getProperty("Browser");
		if(Browser.equals("Chrome")) {
			System.setProperty("webdriver.chrome.driver", "E:/Selenium/chromedriver_win32/chromedriver.exe");
			driver=new ChromeDriver();
			
			
		}
		
		
		driver.manage().window().maximize();
		driver.manage().deleteAllCookies();
		driver.manage().timeouts().pageLoadTimeout(40, TimeUnit.SECONDS);
		driver.manage().timeouts().implicitlyWait(40, TimeUnit.SECONDS);
		
		driver.get(prop.getProperty("URL"));
		
		
	}
	
	
	
}

