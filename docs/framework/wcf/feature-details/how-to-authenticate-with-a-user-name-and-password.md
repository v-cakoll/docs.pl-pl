---
title: "Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73ef3c3f4f4aeb9295cedbbf56635454869b3f4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="1b0fa-102">Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła</span><span class="sxs-lookup"><span data-stu-id="1b0fa-102">How to: Authenticate with a User Name and Password</span></span>
<span data-ttu-id="1b0fa-103">W tym temacie przedstawiono sposób włączania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi do uwierzytelniania klienta z nazwę i hasło użytkownika domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-103">This topic demonstrates how to enable a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="1b0fa-104">Zakłada się, że masz pracy, usługa hostowania samoobsługowego WCF.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="1b0fa-105">Na przykład tworzenia podstawowych hostowania samoobsługowego WCF usługi, zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1b0fa-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="1b0fa-106">W tym temacie założono, że usługa jest skonfigurowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="1b0fa-107">Jeśli chcesz zobaczyć Zobacz przykład konfigurowania podobne usługi przy użyciu pliku konfiguracji [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="1b0fa-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="1b0fa-108">Aby skonfigurować usługę do uwierzytelniania klientów przy użyciu nazwy użytkownika i hasła domeny systemu Windows, użyj <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> i ustaw jej `Security.Mode` właściwości `Message`.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="1b0fa-109">Ponadto należy określić X509 certyfikat używany do szyfrowania nazwy użytkownika i hasła są wysyłane z klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="1b0fa-110">Na komputerze klienckim możesz monit o podanie nazwy użytkownika i hasła i określić poświadczenia użytkownika na serwerze proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
### <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="1b0fa-111">Aby skonfigurować usługi WCF w celu uwierzytelnienia przy użyciu nazwy użytkownika domeny systemu Windows i hasło.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-111">To configure a WCF service to authenticate using Windows domain username and password.</span></span>  
  
1.  <span data-ttu-id="1b0fa-112">Utwórz wystąpienie <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, ustawianie trybu zabezpieczeń powiązania `SecurityMode.Message`ustaw `ClientCredentialType` powiązania `MessageCredentialType.UserName`i Dodaj punkt końcowy usługi przy użyciu skonfigurowanego powiązania do hosta usługi, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="1b0fa-112">Create an instance of the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, set the security mode of the binding to `SecurityMode.Message`, set the `ClientCredentialType` of the binding to `MessageCredentialType.UserName`, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  <span data-ttu-id="1b0fa-113">Określ certyfikat używany do szyfrowania nazwy użytkownika i hasła informacje przesyłane przez sieć.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="1b0fa-114">Ten kod powinna występować zaraz po powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="1b0fa-115">W poniższym przykładzie użyto certyfikatu, który jest tworzony przy użyciu pliku pliku setup.bat z [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md) próbki:</span><span class="sxs-lookup"><span data-stu-id="1b0fa-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="1b0fa-116">Można użyć własnego certyfikatu, po prostu zmodyfikuj kod do odwoływania się do certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="1b0fa-117">Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów Zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1b0fa-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="1b0fa-118">Upewnij się, że certyfikat znajduje się w magazynie certyfikatów zaufanych osób na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="1b0fa-119">Aby to zrobić, mmc.exe uruchomienie i wybranie **pliku**, **Dodaj/Usuń przystawkę...**  elementu menu.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="1b0fa-120">W **Dodawanie lub usuwanie przystawek** okno dialogowe, wybierz opcję **certyfikatów przystawki** i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="1b0fa-121">W oknie dialogowym przystawki Certyfikaty wybierz **konto komputera**.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="1b0fa-122">Domyślnie certyfikat generowane na podstawie próbki nazwa użytkownika zabezpieczeń komunikatów będą się znajdować w folderze osobiste/certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="1b0fa-123">Będzie on wyświetlany jako "localhost" w obszarze wystawiony dla kolumny w oknie konsoli MMC.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="1b0fa-124">Przeciągnij i upuść certyfikatu do **zaufane osoby** folderu.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="1b0fa-125">Pozwoli to WCF zaliczenie certyfikatu zaufanego certyfikatu podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
### <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="1b0fa-126">Do wywołania tej usługi przekazywania nazwy użytkownika i hasła</span><span class="sxs-lookup"><span data-stu-id="1b0fa-126">To call the service passing username and password</span></span>  
  
1.  <span data-ttu-id="1b0fa-127">Aplikacja kliencka musi Monituj użytkownika o nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="1b0fa-128">Poniższy kod monituje użytkownika o nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="1b0fa-129">Ten kod nie należy używać w środowisku produkcyjnym, ponieważ hasło jest wyświetlane podczas wprowadzania.</span><span class="sxs-lookup"><span data-stu-id="1b0fa-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2.  <span data-ttu-id="1b0fa-130">Utwórz wystąpienie serwera proxy klienta określania poświadczeń klienta, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="1b0fa-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1b0fa-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b0fa-131">See Also</span></span>  
 <span data-ttu-id="1b0fa-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="1b0fa-132"><<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`></span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [<span data-ttu-id="1b0fa-133">Zabezpieczenia transportu z uwierzytelnianiem podstawowym</span><span class="sxs-lookup"><span data-stu-id="1b0fa-133">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [<span data-ttu-id="1b0fa-134">Rozproszone zabezpieczenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="1b0fa-134">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="1b0fa-135">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="1b0fa-135">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
