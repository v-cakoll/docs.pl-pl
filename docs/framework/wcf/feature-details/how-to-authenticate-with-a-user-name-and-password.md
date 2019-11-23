---
title: 'Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 33205f9e12fcee53f2f29b63b836ea0cbc792025
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834734"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="c7f28-102">Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła</span><span class="sxs-lookup"><span data-stu-id="c7f28-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="c7f28-103">W tym temacie przedstawiono sposób włączania usługi Windows Communication Foundation (WCF) do uwierzytelniania klienta przy użyciu nazwy użytkownika i hasła domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c7f28-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="c7f28-104">Przyjęto założenie, że masz działającą, samoobsługową usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="c7f28-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="c7f28-105">Aby zapoznać się z przykładem tworzenia podstawowej samohostowanej usługi WCF, zobacz [samouczek wprowadzenie](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="c7f28-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="c7f28-106">W tym temacie przyjęto założenie, że usługa jest skonfigurowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c7f28-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="c7f28-107">Jeśli chcesz zobaczyć przykład konfigurowania podobnej usługi za pomocą pliku konfiguracji, zobacz [Nazwa użytkownika zabezpieczeń wiadomości](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="c7f28-107">If you would like to see an example of configuring a similar service using a configuration file, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>

<span data-ttu-id="c7f28-108">Aby skonfigurować usługę do uwierzytelniania klientów przy użyciu nazwy użytkownika domeny systemu Windows i haseł, użyj <xref:System.ServiceModel.WSHttpBinding> i ustaw jej Właściwość `Security.Mode` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="c7f28-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="c7f28-109">Ponadto należy określić certyfikat x509, który będzie używany do szyfrowania nazwy użytkownika i hasła, gdy są one wysyłane z klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="c7f28-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="c7f28-110">Na kliencie należy monitować użytkownika o podanie nazwy użytkownika i hasła oraz określić poświadczenia użytkownika na serwerze proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="c7f28-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="c7f28-111">Aby skonfigurować usługę WCF do uwierzytelniania przy użyciu nazwy użytkownika i hasła domeny systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c7f28-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="c7f28-112">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding>, ustaw tryb zabezpieczeń powiązania na <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, ustaw `ClientCredentialType` powiązania na <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>i Dodaj punkt końcowy usługi przy użyciu skonfigurowanego powiązania z hostem usługi, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c7f28-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="c7f28-113">Określ certyfikat serwera służący do szyfrowania informacji o nazwie użytkownika i hasła przesyłanej przez sieć.</span><span class="sxs-lookup"><span data-stu-id="c7f28-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="c7f28-114">Ten kod powinien natychmiast następować po powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c7f28-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="c7f28-115">Poniższy przykład używa certyfikatu utworzonego przez plik Setup. bat z przykładowej [nazwy użytkownika zabezpieczeń wiadomości](../samples/message-security-user-name.md) :</span><span class="sxs-lookup"><span data-stu-id="c7f28-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="c7f28-116">Możesz użyć własnego certyfikatu, po prostu zmodyfikuj kod, aby odwołać się do certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="c7f28-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="c7f28-117">Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="c7f28-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="c7f28-118">Upewnij się, że certyfikat znajduje się w magazynie certyfikatów osoby zaufane dla komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c7f28-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="c7f28-119">Można to zrobić, uruchamiając program MMC. exe i wybierając **plik**, **Dodaj/Usuń przystawkę...** .</span><span class="sxs-lookup"><span data-stu-id="c7f28-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="c7f28-120">W oknie dialogowym **Dodawanie lub usuwanie przystawek** wybierz **przystawkę Certyfikaty** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="c7f28-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="c7f28-121">W oknie dialogowym Przystawka certyfikatów wybierz pozycję **konto komputera**.</span><span class="sxs-lookup"><span data-stu-id="c7f28-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="c7f28-122">Domyślnie certyfikat wygenerowany na podstawie przykładowej nazwy użytkownika zabezpieczeń wiadomości zostanie umieszczony w folderze Personal/Certificates.</span><span class="sxs-lookup"><span data-stu-id="c7f28-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="c7f28-123">Będzie on wyświetlany jako "localhost" w kolumnie wystawiony dla w oknie programu MMC.</span><span class="sxs-lookup"><span data-stu-id="c7f28-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="c7f28-124">Przeciągnij i upuść certyfikat do folderu **zaufane osoby** .</span><span class="sxs-lookup"><span data-stu-id="c7f28-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="c7f28-125">Umożliwi to usłudze WCF traktowanie certyfikatu jako certyfikatu zaufanego podczas przeprowadzania uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c7f28-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="c7f28-126">Aby wywołać usługę przekazującą nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="c7f28-126">To call the service passing username and password</span></span>

1. <span data-ttu-id="c7f28-127">Aplikacja kliencka musi monitować użytkownika o podanie nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="c7f28-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="c7f28-128">Poniższy kod prosi użytkownika o podanie nazwy użytkownika i hasła:</span><span class="sxs-lookup"><span data-stu-id="c7f28-128">The following code asks the user for username and password:</span></span>

    > [!WARNING]
    > <span data-ttu-id="c7f28-129">Tego kodu nie należy używać w środowisku produkcyjnym, ponieważ podczas wprowadzania hasła jest wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="c7f28-129">This code should not be used in production as the password is displayed while being entered.</span></span>

    ```csharp
    public static void GetPassword(out string username, out string password)
    {
        Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");
        Console.WriteLine("   Enter username:");
        username = Console.ReadLine();
        Console.WriteLine("   Enter password:");
        password = Console.ReadLine();
    }
    ```

2. <span data-ttu-id="c7f28-130">Utwórz wystąpienie serwera proxy klienta określające poświadczenia klienta, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c7f28-130">Create an instance of the client proxy specifying the client's credentials as shown in the following code:</span></span>

    ```csharp
    string username;
    string password;

    // Instantiate the proxy.
    var proxy = new Service1Client();

    // Prompt the user for username & password.
    GetPassword(out username, out password);

    // Set the user's credentials on the proxy.
    proxy.ClientCredentials.UserName.UserName = username;
    proxy.ClientCredentials.UserName.Password = password;

    // Treat the test certificate as trusted.
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;
    // Call the service operation using the proxy
    ```

## <a name="see-also"></a><span data-ttu-id="c7f28-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7f28-131">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="c7f28-132">Zabezpieczenia transportu z uwierzytelnianiem podstawowym</span><span class="sxs-lookup"><span data-stu-id="c7f28-132">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)
- [<span data-ttu-id="c7f28-133">Rozproszone zabezpieczenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7f28-133">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="c7f28-134">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c7f28-134">\<wsHttpBinding></span></span>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
