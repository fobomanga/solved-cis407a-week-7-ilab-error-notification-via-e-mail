Download Link: https://assignmentchef.com/product/solved-cis407a-week-7-ilab-error-notification-via-e-mail
<br>
<header class="entry-header"></header>

5/5 - (2 votes)

In this lab, we will incorporate error handling into the login process so that a notice of each invalid login is automatically e-mailed to the technical support staff.

<strong>Deliverables</strong>When you try to log in, if your user name is not Mickey, Minnie, or another user you added (that is, if the user name is not found in tblUserLogin), then an e-mail should be sent to the <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="78191c1c0a1d0b0b0a1d1b1108111d160c380a1d1b1108111d160c1c1715191116561b171556">[email protected]</a> If the user attempts to bypass the login page by typing a page name in the URL, your web application should redirect the user back to the login page. Once you have verified that it works, save your project, zip up all files, and submit in the Dropbox.<strong>NOTE:</strong> E-mails may be blocked due to firewalls, antivirus software, or even Internet service providers that turned off SMTP because of some known security issues. If the code works (does not produce an error when submitting), you will get full credit for this project even if no e-mail message is actually transmitted. Consult with your instructor before submitting if an error occurs or if no e-mail is generated, to be sure.

<strong>iLAB STEPS</strong><strong>STEP 1:</strong> Business Layer Functionality1. Open Microsoft Visual Studio.NET 2008.2. Click the ASP.NET website named PayrollSystem to open it.3. Create a new class called clsBusiness Layer.4. Add the following code in the clsBusinessLayer class:

<strong>STEP 2:</strong> Integration5. Open the frmLogin web form code behind file and add the following code to the body of the if (dsUserLogin.tblUserLogin.Count &lt; 1) statement, just above the return statement: [php light=”true”] // Add your comments here // Add your comments here if (clsBusinessLayer.SendEmail(“<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="b2cbddc7c0d7dfd3dbdef2cbddc7c0d6dddfd3dbdc9cd1dddf">[email protected]</a>”, “<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="0d7f686e68647b687f4d7f686e68647b687f6962606c6463236e6260">[email protected]</a>”, “”, “”, “Login Incorrect”, “The login failed for UserName: ” + Login1.UserName + ” Password: ” + Login1.Password)) { Login1.FailureText = Login1.FailureText + ” Your incorrect login information was sent to <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="c3b1a6a0a6aab5a6b183b1a6a0a6aab5a6b1a7acaea2aaadeda0acae">[email protected]</a>”; } [/php] 6. NOTE: Change the <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="0a73657f786f676b63664a73657f786e65676b636424696567">[email protected]</a> and <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="691b0c0a0c001f0c1b291b0c0a0c001f0c1b0d0604080007470a0604">[email protected]</a> to your e-mail and someone else’s e-mail for testing. 7. Optional: Perform this step only if you are doing this lab using Visual Studio 2008 installed on your own computer, your computer has Internet Information Services (IIS) installed, and you have administrative rights to IIS. If you are doing this lab using the iLab (Citrix) server, or if you do not have access to IIS, skip to step 8. Open IIS (Start &gt; Control Panel &gt; Administrative Tools &gt; Internet Information Services), navigate to the Default SMTP Virtual Server, right-click on it, and left-click on Properties.

8. Click here for text description of this image.9. Click the Access tab, then the Relay button, then Add, and add the IP 127.0.0.1. Click OK, OK, and APPLY when finished.

10. Click here for text description of this image.11. We have a security hole in our web application. If you start the web application by going to the login page, you can bypass the login page by simply typing the name of a form in the URL (try it). There is some limited protection because of the check we are doing for user role, but it still allows a user to get to pages we don’t want them to get to unless the role is set properly. Add a security check in the Page_Load of each sensitive page (Manage Users, Add New Employee, View User Activity, Edit Employees), check for the Session role item with a value of “A,” and, if the user is accessing these pages without the proper permissions, redirect back to the frmLogin.aspx page.12. This still leaves the possibility of a person bypassing the login page. We will fix that by using forms authentication. Add the following to the web.config file. (There should already be an authentication section – replace it with this.)

13. This will redirect users to the login page if they have not yet gone through it for login. This process will use a cookie – when the user successfully logs in in a cookie is set that allows the user to go to other pages. If that cookie is not set then the user is redirected to the login page if they try to go to any other page. Add the cookie code by adding this code in the frmLogin.aspx C# code after each place that you have e.Authenticated = true:FormsAuthentication.RedirectFromLoginPage(Login1.UserName, false);14. Hints: Make sure you reestablish your database connection if you copied the files from a previous lab. Also, make sure to update the web.config file with the database connection string.Update any DataSource controls you added with the new payroll database location.When you manually try to go to a second page by skipping the login page, a cookie is set specifying the name of the page you were attempting to go to. Once you login successfully, ASP.Net will automatically attempt to navigate back to that page. You can reset the cookie so that the next page is frmMain, as expected, by typing that page in the URL for the browser before logging in.

Submit Final Lab (includes all previous lab assignments)<strong>STEP 3:</strong> Test and Submit12. Run your project. When you try to log in, enter a user name that is not Mickey or Minnie (i.e., a user name that is not found in tblUserLogin). An e-mail should be sent to <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="47332f223522242e372e222933073522242e372e22293323282a262e296924282a">[email protected]</a> e-mail address.

Test that frmMain reconfigures properly based on user role. Make sure the user cannot bypass the login page.

Once you have verified that everything works, save your website, zip up all files, and submit in the Dropbox.<strong>NOTE:</strong> E-mails may be blocked due to firewalls, antivirus software, or even Internet service providers that turned SMTP off because of some known security issues. If the code works (does not produce an error when submitting), you will get full credit for this project even if no e-mail message is actually transmitted. Consult with your instructor before submitting if an error occurs or if no e-mail is generated. It is expected that no e-mail will be sent if you are using the DeVry iLab (Citrix) server for this lab or if you were not able to configure IIS in step 7.

Make sure you include comments in the code provided where specified (where the ” // Add your comments here” is mentioned), including code you wrote, or else a 5 point deduction per item (form, class, function) will be made.

<table border="0" cellspacing="0" cellpadding="0">

 <tbody>

  <tr>

   <td class="code"></td>

  </tr>

 </tbody>

</table>

<code class="php comments">// **** Add the following at the top of the class file,</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">using System.Net.Mail;</code>

<code class="php comments">//**** Add the following code inside the body of public class clsBusinessLayer ****</code>

<code class="php keyword">public</code> <code class="php keyword">static</code> <code class="php plain">bool SendEmail(string Sender, string Recipient, string bcc, string cc,</code>

<code class="php plain">string Subject, string Body)</code>

<code class="php plain">{</code>

<code class="php keyword">try</code> <code class="php plain">{</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MailMessage MyMailMessage = </code><code class="php keyword">new</code> <code class="php plain">MailMessage();</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MyMailMessage.From = </code><code class="php keyword">new</code> <code class="php plain">MailAddress(Sender);</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MyMailMessage.To.Add(</code><code class="php keyword">new</code> <code class="php plain">MailAddress(Recipient));</code>

<code class="php comments">// Add your comments here</code>

<code class="php keyword">if</code> <code class="php plain">(bcc != null &amp;&amp; bcc != string.</code><code class="php functions">Empty</code><code class="php plain">) {</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MyMailMessage.Bcc.Add(</code><code class="php keyword">new</code> <code class="php plain">MailAddress(bcc));</code>

<code class="php plain">}</code>

<code class="php comments">// Add your comments here</code>

<code class="php keyword">if</code> <code class="php plain">(cc != null &amp;&amp; cc != string.</code><code class="php functions">Empty</code><code class="php plain">) {</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MyMailMessage.CC.Add(</code><code class="php keyword">new</code> <code class="php plain">MailAddress(cc));</code>

<code class="php plain">}</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MyMailMessage.Subject = Subject;</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MyMailMessage.Body = Body;</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MyMailMessage.IsBodyHtml = true;</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MyMailMessage.Priority = MailPriority.Normal;</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">SmtpClient MySmtpClient = </code><code class="php keyword">new</code> <code class="php plain">SmtpClient();</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MySmtpClient.Port = 25;</code>

<code class="php plain">MySmtpClient.Host = </code><code class="php string">"127.0.0.1"</code><code class="php plain">;</code>

<code class="php comments">// Add your comments here</code>

<code class="php plain">MySmtpClient.Send(MyMailMessage);</code>

<code class="php comments">// Add your comments here</code>

<code class="php keyword">return</code> <code class="php plain">true;</code>

<code class="php plain">} </code><code class="php keyword">catch</code> <code class="php plain">(Exception ex) {</code>

<code class="php comments">// Add your comments here</code>

<code class="php keyword">return</code> <code class="php plain">false;</code>

<code class="php plain">}</code>

<code class="php plain">}</code>

<table border="0" cellspacing="0" cellpadding="0">

 <tbody>

  <tr>

   <td class="code"></td>

  </tr>

 </tbody>

</table>

<code class="php plain">&lt;authentication mode=</code><code class="php string">"Forms"</code><code class="php plain">&gt;</code>

<code class="php plain">&lt;forms loginUrl=</code><code class="php string">"frmLogin.aspx"</code> <code class="php plain">/&gt;</code>

<code class="php plain">&lt;/authentication&gt;</code>

<code class="php plain">&lt;authorization &gt;</code>

<code class="php plain">&lt;deny users=</code><code class="php string">"?"</code> <code class="php plain">/&gt;</code>