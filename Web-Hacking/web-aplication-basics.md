
| Task 1 | = Introduction = |
| - | - |

\> Learning Objectives

> 1. Understand what a web application is and how it runs in a web browser.
> 2. Break down the components of a URL and see how it helps access web resources.
> 3. Learn how HTTP requests and responses work.
> 4. Get familiar with the different types of HTTP request methods.
> 5. Understand what different HTTP response codes mean.
> 6. Check out how HTTP headers work and why they matter for security.

----




| Task 2 | = Web Application Overview = |
| - | - |

\> Front End

> The Front End can be considered similar to the surface of the planet, the parts that an astronaut can see and interact with based on the laws of nature. A web application would have a user interact with it and use a number of technologies such as HTML, CSS, and JavaScript to do this.

+ *The main analogy used on the site is that of a planet, but I think it's not so difficult to see it as a system.*


> a) HTML (Hypertext Markup Language) is a foundational aspect of web applications. It is a set of instructions or code that instructs a web browser on what to display and how to display it.

+ *Basically the skeleton of any website, like a template*


> b) CSS (Cascading Style Sheets) in web applications describes a standard appearance, such as certain colours, types of text, and layouts.

+ *The responsible for all the graphic design and look of the page; before you could do it with just HTML, but it was very basic.*


> c) JS (JavaScript) is part of a web application front end that enables more complex activity in the web browser. Whereas HTML can be considered a simple set of instructions on what to display, JavaScript is a more advanced set of instructions that allows choices and decisions to be made on what to display.

+ *Let's imagine you want to get more out of your page with better logic, more interaction, in short, have more control over how your page works.*


\> Back End

> The Back End of a web application is things you don’t see within a web browser but are important for the web application to work.

+ *Think of it as all the external mechanical parts of the page; what came before was the container, this is the modular part of the page...*


> a) A Database is where information can be stored, modified, and retrieved. A web application may want to store and retrieve information about a visitor's preferences on what to show or not; this would be stored in a database.

+ *Like a hard drive, it gives you easy access to information within the page.*


> b) There are many other Infrastructure components underpinning Web Applications, such as web servers, application servers, storage, various networking devices, and other software that support the web application.

+ *Would it be like the page components? I don't know what kind of things fall under this section.*

> c) WAF (Web Application Firewall) is an optional component for web applications. It helps filter out dangerous requests away from the Web Server and provides an element of protection.

+ *The first line of control, which decides what type of connections to allow and which to filter.*

----




| Task 3 | = Uniform Resource Locator = |
| - | - |

> A Uniform Resource Locator (URL) is a web address that lets you access all kinds of online content—whether it’s a webpage, a video, a photo, or other media. It guides your browser to the right place on the Internet.

+ *Whether you've used a file browser (Windows) or navigated in the terminal (Linux/macOS), browsing web pages is the same.*


	[ http://  user:password  @tryhackme.com    :80    /view-room      ?id=1       #task3 ]

	   ^		 ^		^	     ^	        ^	     ^	          ^
	 Scheme	   --   User  --   Host/Domain	--  Port  --   Path --  Query Sting -- Fragment


\> Scheme
> The scheme is the protocol used to access the website. The most common are HTTP (HyperText Transfer Protocol) and HTTPS (Hypertext Transfer Protocol Secure).

\> User
> Some URLs can include a user’s login details (usually a username) for sites that require authentication. This happens mostly in URLs that need credentials to access certain resources.

\> Host/Domain
> The host or domain is the most important part of the URL because it tells you which website you’re accessing. Every domain name has to be unique and is registered through domain registrars.

\> Port
> The port number helps direct your browser to the right service on the web server. It’s like telling the server which doorway to use for communication.

\> Path
> The path points to the specific file or page on the server that you’re trying to access. It’s like a roadmap that shows the browser where to go.

\> Query String
> The query string is the part of the URL that starts with a question mark (?). It’s often used for things like search terms or form inputs.

\> Fragment
> The fragment starts with a hash symbol (#) and helps point to a specific section of a webpage—like jumping directly to a particular heading or table.




+ *Now that we know what makes up the URL, what measures can we take? In other words, you could easily navigate to any part of the page if you knew the directory.*

	1. Clean and sanitize everything! Set rules on what the user can do/write/etc, never rely on people's goodwill.

	2. Create security rules for the type of access a user can have. Follow the principle of least privilege.

	3. Just like passwords, Do not create simple structures that make it easy to move laterally (i.e., move between employee IDs by increasing a number).

	4. Take the time to scout your domain name; you don't want it to get lost among very common names or be so exotic that it's easy to create phishing sites (don't add 5 's's in a row).

	5. Use HTTPS and valid certificates, don't try to act like you're God, or make your own certificates, please.

----




| Task 4 | = HTTP Messages = |
| - | - |

> HTTP messages are packets of data exchanged between a user (the client) and the web server. These messages are very important for understanding how web applications work because they show how users' requests and the server's responses are communicated.


\> There are two types of HTTP messages:

> a) HTTP Request: Sent by the user to trigger actions on the web application.
> 
> b) HTTP Response: Sent by the server in response to the user’s request.


