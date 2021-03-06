.NET Framework 4.6.2 List of Changes
============================================

.NET Framework 4.6.2 contains dozens of bug fixes and improvements. 
This list details those changes, grouped by feature area. 
Each change includes our TFS bug numbers at the end of the line. Please include those numbers in your communication if you wish to contact us to obtain more information.

CLR
---

* Added Custom attribute to opt out of NGen with method granularity [186172]
* Support .NET in packaged desktop apps. [191774]
* Fixed incorrect result generation while comparing 16-bit signed values. [187325]
* Fixed a JIT optimization bug [174983]
* Fixed crashes due to JIT32 inlining�s handling of struct [171773]
* Fixed issue with incomplete PDB information when invoking ildasm. [150267]
* Fixed a performance regression in debug start [164437]
* Fixed an issue in CLR type loader that causes type load failures in rare conditions. [185570]
* Fixed usability issues with error message received when System.BitConverter.ToString(Byte[] value, Int32 startIndex, Int32 length) is called [100012]
* Performance fixes in GC [162854]
* Fixed stress issues in GC [161104]
* Fixed crashes in EventListener.DisposeOnShutdown [156238]
* Implement EventCounter support [150674]
* Fixed System.Diagnostics.Tracing.EventSource does not serialize byte[] correctly [153224]
* Fixed RelatedActivityID is not set properly when using EventSource's ActivityTracker [154432]
* Fixed [EventSource] .WriteEvent handles null strings inconsistently depending on the overload getting called [95999]
* Added the event name to ThrowEventSourceException message [112066]
* Fixed typo in EventSource resource string [118799]
* Fixed unexpected exceptions thrown during OnEventSourceCreated [121699]
* In .NET 4.6 if two event names in EventSource differ by a suffix of Start or Stop, then the EventSource will fail to construct and never emit any logging. This is now fixed. [121820]
* Improve Diagnostic when using RelatedActivityID in EventSource [128437]
* User-defined subclasses named "EventSource" can be allowed by checking that the EventSource's type is not equal to typeof(EventSource) which is the type of the built in EventSource. [125529]
* When a byte array is written to an Event a spurious warning is generated by EventSource, claiming that the event has a mismatch in parameter count when it does not. [166228]
* Fixed erroneous removal of IF condition in a finally or catch handler if the condition check exists in the exit from the try-body and entry to the try-body. [149697]
* Fixed a codegen bug when encountering an unbox instruction while the evaluation stack has pending evaluations that side-effect arguments of the unbox. [150586]
* Fix for optimization bug in the JIT component of .NET 4.6.1 may incorrectly combine branches that test bit patterns into a single branch incorrectly leading to program failure. [168744]
* Fix for hang in GC when ETW happens to request to walk the heap at the end of a background server GC [179589]
* Fixed NullReferenceException in EventSource if activity tracking is enabled. [182896]
* Fixed an EventSource exception indicating the maximum number of arguments has been exceeded. [191686]
* Added support for memory limit specified by job objects to GC. [194795]
* Fixed JIT Optimizer bug causing structs to be treated as reference objects instead of values objects in .Net 4.6 when targeting amd64. [194809]
* Fixed potential crash when the JIT generates an incorrect initialization value for an initblk and initializes memory incorrectly. [199169]
* Added VariableHome API for NullReferenceException improvements. [199851]
* Fixed [EventSource] Tags field is ignored for complex types. [205969]
* Allowed the debugger to determine the layout of types without an instance of the type. [211562]
* Reduced events are being sent for telemetry to the CLR for Windows Server OSes. [211794]
* Support resolving Windows Runtime references through simple name in .NET SDK. [219126]

BCL
---
* Fix RunContinuationsAscynchronously flag for all continuation types. [146618]
* Fixed NullReference exception if  "sha1RSA" is passed to RSACryptoServiceProvider.SignHash(). [147247]
* Fixed �Unhandled Exception: System.Security.SecurityException: Unable to retrieve security descriptor for this frame.� in System.Security.Principal.WindowsIdentity.RunImpersonated() [149685]
* Removed the System.Numerics.Vectors fa�ade from the targeting pack. If this fa�ade is needed, add a reference to the System.Numerics.Vectors NuGet package. [120400]
* SignedXml now supports SHA256/384/512 signing. [125387]
* Added a new type called DSACng. [180229]
* Fixed Warnings generated during build that before required a global disable. [185846]
* Fixed potential threading issues with inconsistent values returned from the calls to AppContext. [181890]
* Framework support Unicode 8.0 for character categories. [176613]
* Improved interoperability with PFX files created with OpenSSL in GetECDsaPrivateKey. [171017]
* The ECDiffieHellman base class has been updated to provide better exposure for the hash, HMAC, and TLS-PRF key derivation methods, and the parameters they accept. [171018]
* Fixed System.Security.Cryptography.RSAPKCS1SignatureFormatter.ComputeSignature() and VerifySignature() failures with a NotSupportedException when an RSACng key is specified. [162556]
* Fixed message decryption issues in System.Security.Cryptography.Pkcs.EnvelopedCMS if the recipient certificate's private key is stored in a CNG key container. [163800]
* The factory method now returns SHA256Cng in FIPS-only mode. [163804]
* Fixed behavioral inconsistencies between .NET Core and .NET Framework 4.6 implementations of RSACng [164390]
* Update .NET to support packaged desktop applications. [191801]
* Fixed app crashes related to CompatSortNLSVersion handler initializations [191561]
* System.Security.Cryptography RSAOAEPKeyExchangeDeformatter, RSAOAEPKeyExchangeFormatter, RSAPKCS1KeyExchangeDeformatters and RSAPKCS1KeyExchangeFormatter no longer fail when used with a CNG key. [190217]
* Added support for AesCng and TripleDESCng. [187062]
* The DSA base class has been updated in the same manner as RSA in 4.6, and ECDsa in 4.6.1.  Accessing the public/private key of a DSA certificate can be done in a type-safe manner via cert.GetDSAPublicKey()/cert.GetDSAPrivateKey(), and signing and verification operations can be done without further casting. [167883]
* Improved usability of error message for System.BitConverter.ToString(Byte[] value, Int32 startIndex, Int32 length). [100012]
* Fix in bulletin MS16-019. [145386]
* Fix in bulletin MS16-035. [171029]
* AesCng() and TripleDEScng() updated to honor optional provider value. [176670]
* Fixes in System.Security.Cryptography [190217]
   RSAOAEPKeyExchangeDeformatter
   RSAOAEPKeyExchangeFormatter
   RSAPKCS1KeyExchangeDeformatters
   RSAPKCS1KeyExchangeFormatter 
* Localized RegionInfo object "BW". [194531]
* Fixed SignedXml.CheckSignature(X509Certificate2) will fail for DSA certs with large keys. [194760]
* Added support for long path names on Windows. [195340]
* Fixed EncryptedXml not supporting CNG certificates. [196759]
* Fixed AppContext switch default. [198124]
* Fixed string comparison hitting before the AppDomain is fully initialized. [198570]
* Fixed potential errors with String comparison hitting before the AppDomain is fully initialized. [199217]
* Added validation that AppContext defaults are correctly enabled. [200028]
* Fixed potential errors with String comparison hitting before the AppDomain is fully initialized. [200330] and [201338]
* Fixed file path syntax to correctly handle device path syntaxes (\\.\, \\?\) [202926]
* Fix for StringBuilder overflow and the length becoming negative when > 2GB of data is added/inserted. [216203]

Networking
----------
* Fixed a crash with Null Reference in PinnableBufferCache.Free. [144864]
* Fix in bulletin MS16-065. [186985]
* Added CNG certificate support to NCL code in System.dll. [195318]
* An AccessViolationException gets thrown in HttpListenerRequest.GetTlsTokenBindingRequestInfo() if the RequestBuffer of the HttpListenerRequest has been moved by the garbage collector. This AccessViolation is caused by the fact that HttpListenerRequest is dereferencing a pointer inside RequestBuffer, without adjusting the pointer address the way other HttpListenerRequest methods do. This is now fixed. [204580]

ASP.NET
-------
* Fixed deadlock in AspNetSynchronizationContext [152944]
* Add support for sorting Model binding items by nested property names [173528]
* Fix Unhandled non-serializable exceptions in ASP.NET [160528]
* Fixed Non-interlocked update/read of 64-bit variable leads to wrong behavior. [92099]
* Since .NET 4.5 ASP.NET cache reports invalid size of the cache. This has been fixed. [154451]
* Fixed client side project compilation failure [156379]
* Fixed an issue with missing ".NET Memory Cache 4.0" performance counter [145677]
* Improve error message localization for DataAnnotationValidiation in ASP.NET model binding and Dynamic data. [176731]
* Enable customers using the Session State Store Providers with task returning methods. [179604]
* Enabling task returning methods to be used with the OutputCache Providers, to allow ASP.Net customers to get the scalability benefits of async. [187841]

WPF
---
* Nested Markup Expressions scenarios, where the parent markup extension is locally defined, have been fixed now. Developers can use markup extension within their custom defined markup extensions without causing a compiler error. [117193]
* Fixed potential periodic hangs or poor performance of a WPF application running on a device that has touch support.  This is mostly seen when running over a touch-enabled remote desktop or other touch enabled remote access solutions.  [146399]
* Enable automatic invocation and dismissal of the touch keyboard in WPF applications without disabling WPF stylus/touch support on Windows 10 [178044]
* Fixed missing glyph symbol display issues for those WPF applications that render text in the following ranges using a font that does not contain these ranges. [165725]
  Ranges: 
  Unicode = "0000-052F, 0590-06FF, 0750-077F, 08A0-08FF, 1D00-1FFF, 2C60-2C7F, A720-A7FF, FB00-FB0F, FB1D-FBFF"
  Unicode = "FC00-FDCF, FDF0-FDFF, FE20-FE2F, FE70-FEFE"
* Developers of WPF applications on .NET 4.6.1 may notice that the number of promotions from a touch move event to a mouse move event do not correspond 1:1.  This change ensures that there is a corresponding mouse move promotion for every applicable touch move. [169470]
* Enable WPF Applications to look and feel great in multi DPI environments. This means crisper text, sharper images and general polish. [191569]
* WPF applications that allocate large numbers of bitmaps over time can possibly see performance issues such as frequent pauses and large numbers of garbage collections.  This fix changes the bitmap garbage collection strategy to help alleviate these issues. [121913]
* Enables enumeration of generic and themed ResourceDictionary instances, and provides a notification infrastructure for listening to loading and unloading of ResourceDictionary instances. [159740]
* Starting .NET 4.6, CurrentCulture or CurrentUICulture changes made by event handlers (or any other method that WPF orchestrates the dispatch for) are lost when the method completes. This can result in various unintended side-effects ranging from the selection of incorrect UI language by application code, to potential loss of state information. This fix addresses the bug described above. [157919]
* Fixed compilation error in situations when a locally defined custom type in a XAML resource dictionary is immediately followed by something like x:Array. [131561]
* Long runs of dashes are now displayed correctly, without spurious spaces. [92892]
* On environments where the secondary monitor is larger than the primary monitor, a WPF application won't maximize to the correct size. This is now fixed. [104034]
* Fixed Crash after refreshing a collection underlying a ComboBox. [125219]
* Fixed crash in DataGrid view. [150804]
* Fixed Groups not being sorted correctly after property changes.  [165198]
* Fixed RibbonGallery being disabled. [173053]
* Fixed memory usage issues with printing in Windows 8 and above. [174139]
* Fix in bulletin MS16-035. [176941]
* Developers can opt-in to receiving an exception when TextBoxBase controls fail to complete a Copy or Cut operation.  [177621]
* WPF applications being used via multi-touch enabled devices could sometimes lose mouse promotion after a multi-touch drag/drop.  This occurred when users removed touch points other than the primary (or dragging) touch point first.  Doing so would cause an incorrect count of active touch devices causing mouse promotion handling to be incorrect for future touch interaction.  This is now fixed. [185548]
* WPF would previously throw an ArgumentException when a UI Automation Client queried for an unknown TextAttribute.  This was causing performance issues in WPF applications on Windows 8 and above.  WPF will now simply return NotSupported in response to querying an unknown TextAttribute preserving the external behavior and helping alleviate performance issues. [187764]
* Fix for crash that occurs when:  App is running more than one dispatcher thread, First thread uses any ItemsControl, Second thread uses a Selector. While something is selected, the underlying collection raises a Reset event, or the ItemsSource changes. [190507]
* Per Monitor DPI Aware apps now can have their title bars scaled to the correct DPI when an app is moved from one DPI to a different one. [206796]
* Images created with BitmapCreateOptions=DelayCreation can now update their ImageSource by listening to the RoutedEvent DpiChanged on the Image. This event is fired before the Image is decoded, and thus the cost of decoding the image twice can be avoided. [206986]
* WPF apps which are Per monitor DPI aware, running on Windows 10 Anniversary Update, will not have their popup windows like Menus clipped the first time they are open on a monitor with a different DPI. [212426]
* Fixed for Wisptis doesn't support some scenarios in Windows 7, trying to load wisptis in certain scenarios can result in delays upon start or crashes. [215016]
* Fixed issues with the touch keyboard showing on controls when it should not. [222625]
* Fixed ArgumentException when scrolling a virtualized ItemsControl after adding new items [194726].
* Avoid unnecessary iteration through all items displayed in a virtualized ItemsControl with ScrollUnit=Item [202599].
* Fixed XPS printing crash when InvariantCulture is used. [143947]
* Fixed truncation of contents during copy & paste in HTML format when WPF�s DataGrid control contains full width characters, for e.g. Japanese. [104825]

WCF
---
* Added a new option for client to find best matching WCF service endpoint using NetNamePipeBinding.[157498]
* CryptoConfig.CreateName(string algorithm) is now updated to understand SHA256 algorithms. [195341]
* Fixed a reliability issue in DataContractCriticalHelper which throws as a SerializationException when reading objects concurrently. [146940]
* Fixed System.ServiceModel.Activation.HostedAspNetEnvironment.get_WebSocketVersion failing during WP startup. [169409]
* Added support for OperationContext.Current with async. [171085]
* Added telemetry for WCF. [172127]
* Fixed a race in UnescapeDefaultValue in UriTemplate::Match when using Default Values [176590]
* Added Support for usage of X509 certificates which are stored using the CNG key storage provider. [182182]
* Fix for XmlSerializer not correctly serializing with XmlText's DataType set to "time". [184091]
* Removed Ssl3 from the WCF TransportDefaults. [186891]
* Fixed DataContractJsonSerializer producing wrong date/time data after having installed KB3093503 when the time zone is (UTC+2) Istanbul. [187509]
* Fixed Performance in AppServices Throughput. [201205]
* Fixed issue that could occur with tracing enabled on WCF async service; failed call generated double OperationFaulted traces. [208167]
* Fix for ArgumentException when opening service host when user�s certificate has invalid key usage data. [223670]
* Fixed WCF SslStreamSecurity DNS Identity Check failure while targeting .NET Framework 4.6 when Alt subject is not present [182336]

Workflow
--------
* Workflow designer now supports �prepared for update� dynamic update XAML [98185]
* Fixed a FIPS compliance issue when using workflow tracking in WF3. [181434]
* Added Workflow/System.Messaging/System.Transactions Telemetry. [198681]
* Fixed transaction failure for SQLCLR usage of System.Transactions to promote a local SQL transaction to a distributed transaction. [206276]

Windows Forms
-------------
* Fixed a crash in Windows Forms designer related to switching windows themes [172691]
* "Smart Tag" dialog processes "enter" key press properly and is same as in Visual Studio 2013 [174771]
* Enabled shortcut keys in the preferences dialog in mageui.exe tool [184655]
* A Windows Forms application that is using print preview dialog when printing to a network printer with certain non-default preferences set, can now opt in into a performance optimization that would considerably speed up the preview generation. [159091]
* Fixed a hang in Windows Forms app when Control.Invoke is called but the caller thread terminates before the invoke finishes [149183]
* Added an Application compatibility switch that fixes implementation of MemberDescriptor.Equals  function so that it compares the corresponding fields, instead of comparing description field to category field. [149471]
* Fixed potential race condition in System.Windows.Forms.Application.ThreadContext  [146065]
* Fixed a control in MageUI tool that is not accessible by a keyboard shortcut because the same shortcut letter is used for two controls [146678]
* Fixed a memory leak in Control.DrawToBitmap method. [188396]
* Fixed control text truncations issue in �Items Collection Editor� dialog in Visual Studio. [187716]
* Fixed a crash in Windows Forms Designer in Visual Studio related to adjusting TableLayoutPanel control. [190415]
* Fixed a crash in Windows Forms Designer in Visual Studio [190416]
* Fix in bulletin MS16-019. [174623]
* Added Long path support for Windows 10 Anniversary Update in Windows Forms. [191855]
* Improved reliability of Windows Forms applications [193532]
* Added support for CNG key providers to Mage and Mageui SDK tools [194373]
* Fixed printing delay in previewing the document with a network printer. [197824]
* Added Long path support for Windows 10 Anniversary Update in ClientConfigPath. [202970]
* Fixed X1 Professional Client "ok" button is gray and disabled after select Desktop in browse for folder. [207279]

SQL
---
* Added Parameter Caching and CEK TTL improvements. [200050]
* Removed connection pool blocking period for Azure SQL DBs. [200140]
* Fixed incorrect error message in SqlClient when a Command Execution fails on Azure. [201189]
* Disallowed WAM option in native ADAL for AAD authorization. [201411]
* Fix in bulletin MS16-091. [222831]
* Fix for a crash that may occur when the connection pool is being replenished and during replenishment of the pool, the connection to SQL server fails. [229717]

ClickOnce
---------
* Added support for TLS1.1/1.2 in ClickOnce runtime. [193676]
* Fixed string truncations issue on ClickOnce security dialog. [176656]
* Added ClickOnce support for installation from web-sites that require Client Certificate to be supplied. [197343]

Active Directory Services
-------------------------
* On calls made to System.DirectoryServices.AccountManagement UserPrincipal.GetAuthorizationGroups method against an Active Directory forest which contains SID History values for migrated users, an empty GroupPrincipal will be added to the list returned by GetAuthorizationGroups for every group with a migrated user SID. [191563]
