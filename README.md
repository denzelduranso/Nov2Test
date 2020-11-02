# Nov2Test
ChromeDriver
using NUnit.Framework;
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;

namespace ICTestProjectNov2020
{
    public class Tests
    {
        //It will run before the actual test will run.

        IWebDriver driver;

        [SetUp]
        public void Setup()
        {

            driver = new ChromeDriver();


            var chromeOptions = new ChromeOptions();
            chromeOptions.AddArguments("headless");

            using (var browser = new ChromeDriver(chromeOptions))
            {
                // add your code here

                chromeOptions.AddArguments(new List<string>() {
                        "--silent-launch",
                        --no-startup-window",
                            no-sandbox",
                            "headless",});
            }
        }

        //initialize chrome driver
        //Alocate memory to the chrome


        [Test]
        public void VerifyUserCanLogInIntoIC()
        {
            //Open a browser : Chrome
            driver.Navigate().GoToUrl("http://horse.industryconnect.io/Account/Login?ReturnUrl=%2f");

            //Link of website : Horse Portal - Navigate to the House Portal It's Url


            //Enter username  & password

            //Click Submit Button


            //Username : Hari



        }

        [TearDown]
        public void CloseDriver()
        {
            driver.Dispose();
        }


       
    }
}
