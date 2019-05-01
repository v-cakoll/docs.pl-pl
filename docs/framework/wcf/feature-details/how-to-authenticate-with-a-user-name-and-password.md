---
title: 'Instrukcje: uwierzytelnianie za pomocą nazwy użytkownika i hasła'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 11a146e387171d6af95a7710fe96d6f35f6c611f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000873"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="f312f-102">Instrukcje: uwierzytelnianie za pomocą nazwy użytkownika i hasła</span><span class="sxs-lookup"><span data-stu-id="f312f-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="f312f-103">W tym temacie pokazano, jak włączyć usługę Windows Communication Foundation (WCF) do uwierzytelniania klienta przy użyciu Windows domena nazwa użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="f312f-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="f312f-104">Założono, że masz pracy, obsługiwanej samodzielnie usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="f312f-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="f312f-105">Aby uzyskać przykład tworzenia podstawowych Self-Hosted WCF service, zobacz [Samouczek wprowadzający](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f312f-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="f312f-106">W tym temacie założono, że usługa jest skonfigurowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f312f-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="f312f-107">Jeśli chcesz zobaczyć przykład konfigurowania podobnej usługi przy użyciu pliku konfiguracji, zobacz [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="f312f-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="f312f-108">Aby skonfigurować usługi w celu uwierzytelnienia klientów przy użyciu nazwy użytkownika i hasła domeny Windows, użyj <xref:System.ServiceModel.WSHttpBinding> i ustaw jego `Security.Mode` właściwość `Message`.</span><span class="sxs-lookup"><span data-stu-id="f312f-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="f312f-109">Ponadto należy określić X509 certyfikat używany do szyfrowania nazwę użytkownika i hasło są wysyłane z klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="f312f-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="f312f-110">Na komputerze klienckim możesz monitować użytkownika o nazwę użytkownika i hasło i określ poświadczenia użytkownika na serwerze proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="f312f-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="f312f-111">Aby skonfigurować usługi WCF w celu uwierzytelnienia przy użyciu Windows domena nazwa użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="f312f-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>
  
1. <span data-ttu-id="f312f-112">Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding>, ustawianie trybu zabezpieczeń wiązania <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>ustaw `ClientCredentialType` wiązania <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>i Dodaj punkt końcowy usługi za pomocą skonfigurowanego powiązania host usługi, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f312f-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2. <span data-ttu-id="f312f-113">Określ certyfikat używany do szyfrowania nazwy użytkownika i hasło informacje przesyłane przez sieć.</span><span class="sxs-lookup"><span data-stu-id="f312f-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="f312f-114">Ten kod powinien natychmiast wykonaj powyższy kod.</span><span class="sxs-lookup"><span data-stu-id="f312f-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="f312f-115">W poniższym przykładzie użyto certyfikatu, który jest tworzony przez plik setup.bat z [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md) próbki:</span><span class="sxs-lookup"><span data-stu-id="f312f-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="f312f-116">Możesz użyć własnego certyfikatu, po prostu zmodyfikuj kod do odwoływania się do certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="f312f-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="f312f-117">Aby uzyskać więcej informacji na temat tworzenia i wykorzystywania certyfikatów Zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f312f-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="f312f-118">Upewnij się, że certyfikat znajduje się w magazynie certyfikatów zaufanych osób na lokalnym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f312f-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="f312f-119">Można to zrobić, uruchamiając mmc.exe i wybierając **pliku**, **Dodaj/Usuń przystawkę...**  elementu menu.</span><span class="sxs-lookup"><span data-stu-id="f312f-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="f312f-120">W **Dodawanie lub usuwanie przystawek** okno dialogowe, wybierz opcję **certyfikatów w przystawce** i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f312f-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="f312f-121">W przystawce Certyfikaty w oknie dialogowym wybierz **konto komputera**.</span><span class="sxs-lookup"><span data-stu-id="f312f-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="f312f-122">Domyślnie certyfikat wygenerowany na podstawie próbki nazwa użytkownika zabezpieczeń komunikatów będą znajdować się w folderze Personal/Certificates.</span><span class="sxs-lookup"><span data-stu-id="f312f-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="f312f-123">Będzie ono wyświetlane jako "localhost", w obszarze wystawiony dla kolumn w oknie konsoli MMC.</span><span class="sxs-lookup"><span data-stu-id="f312f-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="f312f-124">Przeciąganie i upuszczanie certyfikat do **zaufane osoby** folderu.</span><span class="sxs-lookup"><span data-stu-id="f312f-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="f312f-125">Umożliwi to WCF do traktowania certyfikatu jako zaufanego certyfikatu podczas uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="f312f-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="f312f-126">Aby wywołać usługę, przekazując nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="f312f-126">To call the service passing username and password</span></span>  
  
1. <span data-ttu-id="f312f-127">Aplikacja kliencka musi monit o wprowadzenie nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="f312f-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="f312f-128">Poniższy kod monituje użytkownika o nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="f312f-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="f312f-129">Ten kod nie należy używać w środowisku produkcyjnym, ponieważ hasło jest wyświetlane podczas wprowadzania.</span><span class="sxs-lookup"><span data-stu-id="f312f-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
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
  
2. <span data-ttu-id="f312f-130">Utwórz wystąpienie obiektu serwera proxy klienta, określając poświadczenia klienta, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="f312f-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f312f-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f312f-131">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="f312f-132">Zabezpieczenia transportu z uwierzytelnianiem podstawowym</span><span class="sxs-lookup"><span data-stu-id="f312f-132">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [<span data-ttu-id="f312f-133">Rozproszone zabezpieczenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="f312f-133">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="f312f-134">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f312f-134">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
