---
title: 'Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła'
description: Dowiedz się, jak włączyć usługę WCF do uwierzytelniania klienta przy użyciu nazwy użytkownika i hasła domeny systemu Windows z przykładowym kodem.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 1f938f8041b2577b3705266948f29b42f23a6fd7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247250"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="34e28-103">Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła</span><span class="sxs-lookup"><span data-stu-id="34e28-103">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="34e28-104">W tym temacie przedstawiono sposób włączania usługi Windows Communication Foundation (WCF) do uwierzytelniania klienta przy użyciu nazwy użytkownika i hasła domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="34e28-104">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="34e28-105">Przyjęto założenie, że masz działającą, samoobsługową usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="34e28-105">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="34e28-106">Aby zapoznać się z przykładem tworzenia podstawowej samohostowanej usługi WCF, zobacz [samouczek wprowadzenie](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="34e28-106">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="34e28-107">W tym temacie przyjęto założenie, że usługa jest skonfigurowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="34e28-107">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="34e28-108">Jeśli chcesz zobaczyć przykład konfigurowania podobnej usługi za pomocą pliku konfiguracji, zobacz [Nazwa użytkownika zabezpieczeń wiadomości](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="34e28-108">If you would like to see an example of configuring a similar service using a configuration file, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>

<span data-ttu-id="34e28-109">Aby skonfigurować usługę do uwierzytelniania klientów przy użyciu nazwy użytkownika domeny systemu Windows i haseł, użyj <xref:System.ServiceModel.WSHttpBinding> i ustaw jej `Security.Mode` Właściwość na `Message` .</span><span class="sxs-lookup"><span data-stu-id="34e28-109">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="34e28-110">Ponadto należy określić certyfikat x509, który będzie używany do szyfrowania nazwy użytkownika i hasła, gdy są one wysyłane z klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="34e28-110">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="34e28-111">Na kliencie należy monitować użytkownika o podanie nazwy użytkownika i hasła oraz określić poświadczenia użytkownika na serwerze proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="34e28-111">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="34e28-112">Aby skonfigurować usługę WCF do uwierzytelniania przy użyciu nazwy użytkownika i hasła domeny systemu Windows</span><span class="sxs-lookup"><span data-stu-id="34e28-112">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="34e28-113">Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> , ustaw tryb zabezpieczeń powiązania z <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType> , ustaw `ClientCredentialType` powiązanie z <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType> i Dodaj punkt końcowy usługi przy użyciu skonfigurowanego powiązania z hostem usługi, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="34e28-113">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="34e28-114">Określ certyfikat serwera służący do szyfrowania informacji o nazwie użytkownika i hasła przesyłanej przez sieć.</span><span class="sxs-lookup"><span data-stu-id="34e28-114">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="34e28-115">Ten kod powinien natychmiast następować po powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34e28-115">This code should immediately follow the code above.</span></span> <span data-ttu-id="34e28-116">Poniższy przykład używa certyfikatu utworzonego przez plik setup.bat z przykładowej [nazwy użytkownika zabezpieczeń wiadomości](../samples/message-security-user-name.md) :</span><span class="sxs-lookup"><span data-stu-id="34e28-116">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="34e28-117">Możesz użyć własnego certyfikatu, po prostu zmodyfikuj kod, aby odwołać się do certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="34e28-117">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="34e28-118">Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Praca z certyfikatami](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="34e28-118">For more information about creating and using certificates see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="34e28-119">Upewnij się, że certyfikat znajduje się w magazynie certyfikatów osoby zaufane dla komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="34e28-119">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="34e28-120">Można to zrobić, uruchamiając mmc.exe i wybierając **plik**, **Dodaj/Usuń przystawkę...** .</span><span class="sxs-lookup"><span data-stu-id="34e28-120">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="34e28-121">W oknie dialogowym **Dodawanie lub usuwanie przystawek** wybierz **przystawkę Certyfikaty** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="34e28-121">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="34e28-122">W oknie dialogowym Przystawka certyfikatów wybierz pozycję **konto komputera**.</span><span class="sxs-lookup"><span data-stu-id="34e28-122">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="34e28-123">Domyślnie certyfikat wygenerowany na podstawie przykładowej nazwy użytkownika zabezpieczeń wiadomości zostanie umieszczony w folderze Personal/Certificates.</span><span class="sxs-lookup"><span data-stu-id="34e28-123">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="34e28-124">Będzie on wyświetlany jako "localhost" w kolumnie wystawiony dla w oknie programu MMC.</span><span class="sxs-lookup"><span data-stu-id="34e28-124">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="34e28-125">Przeciągnij i upuść certyfikat do folderu **zaufane osoby** .</span><span class="sxs-lookup"><span data-stu-id="34e28-125">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="34e28-126">Umożliwi to usłudze WCF traktowanie certyfikatu jako certyfikatu zaufanego podczas przeprowadzania uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="34e28-126">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="34e28-127">Aby wywołać usługę przekazującą nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="34e28-127">To call the service passing username and password</span></span>

1. <span data-ttu-id="34e28-128">Aplikacja kliencka musi monitować użytkownika o podanie nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="34e28-128">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="34e28-129">Poniższy kod prosi użytkownika o podanie nazwy użytkownika i hasła:</span><span class="sxs-lookup"><span data-stu-id="34e28-129">The following code asks the user for username and password:</span></span>

    > [!WARNING]
    > <span data-ttu-id="34e28-130">Tego kodu nie należy używać w środowisku produkcyjnym, ponieważ podczas wprowadzania hasła jest wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="34e28-130">This code should not be used in production as the password is displayed while being entered.</span></span>

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

2. <span data-ttu-id="34e28-131">Utwórz wystąpienie serwera proxy klienta określające poświadczenia klienta, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="34e28-131">Create an instance of the client proxy specifying the client's credentials as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34e28-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34e28-132">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="34e28-133">Zabezpieczenia transportu z uwierzytelnianiem podstawowym</span><span class="sxs-lookup"><span data-stu-id="34e28-133">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)
- [<span data-ttu-id="34e28-134">Rozproszone zabezpieczenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="34e28-134">Distributed Application Security</span></span>](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
