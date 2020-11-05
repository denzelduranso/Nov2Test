//Nov2and3
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
            driver.Manage().Window.Maximize();



        }

        //initialize chrome driver
        //Alocate memory to the chrome


        [Test]
        public void VerifyUserCanLogInIntoIC()
        {
            driver.Navigate().GoToUrl("http://horse.industryconnect.io/Account/Login?ReturnUrl=%2f");

            //Link of website : Horse Portal - Navigate to the House Portal It's Url

           //Username 
            var username = driver.FindElement(By.Id("UserName"));

            username.SendKeys("hari");
            

            var password = driver.FindElement(By.Id("Password"));
            password.SendKeys("123123");



            var loginBtn = driver.FindElement(By.CssSelector("input[type=submit]"));

            loginBtn.Click();


            var dropwdowns = driver.FindElements(By.CssSelector("li[class=dropdown] a[data-toggle=dropdown]"));

            var isHariPresent = false;

            foreach (var dropdown in dropwdowns)

            {
                if (dropdown.Text == "Hello hari!")
                {
                    isHariPresent = true;
                    break;
                }
            }




            //var dropdownTime = new Select(driver.FindElement(By.XPath("//span[@class='k-widget k-dropdown k-header text-box single-line']")));
            //dropdownTime.selectByValue("Time");
            Assert.IsTrue(isHariPresent);

           


            var dropddownAdmin = driver.FindElement(By.XPath("//a[@class='dropdown-toggle' and text()='Administration ']"));
            dropddownAdmin.Click();


            var TimeAndMaterials = driver.FindElement(By.XPath("//a[text()='Time & Materials']"));
            TimeAndMaterials.Click();

            var CreateNew = driver.FindElement(By.XPath("//a[@class='btn btn-primary']"));

            CreateNew.Click();


            //var dropdownTime = new Select(driver.FindElement(By.XPath("//span[@class='k-widget k-dropdown k-header text-box single-line']")));
            //dropdownTime.selectByValue("Time");

            var Code = driver.FindElement(By.Id("Code"));
            Code.SendKeys("22131");

            var Desc = driver.FindElement(By.Id("Description"));
            Desc.SendKeys("Cute");

            var PricePerUnit = driver.FindElement(By.Id("Price"));
            PricePerUnit.SendKeys("30000");


            var Save = driver.FindElement(By.XPath("#SaveButton"));
            Save.Click();

            

        }




        [TearDown]
        public void CloseDriver()
        {

            driver.Close();
            driver.Dispose();
        }



    }
}
