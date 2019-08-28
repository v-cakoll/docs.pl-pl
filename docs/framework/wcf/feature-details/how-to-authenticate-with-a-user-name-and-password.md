---
title: 'Instrukcje: uwierzytelnianie za pomocą nazwy użytkownika i hasła'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: e1db413dfdcfa18403e1b67361cea710b203fe5d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045955"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Instrukcje: uwierzytelnianie za pomocą nazwy użytkownika i hasła

W tym temacie przedstawiono sposób włączania usługi Windows Communication Foundation (WCF) do uwierzytelniania klienta przy użyciu nazwy użytkownika i hasła domeny systemu Windows. Przyjęto założenie, że masz działającą, samoobsługową usługę WCF. Aby zapoznać się z przykładem tworzenia podstawowej samohostowanej usługi WCF, zobacz [samouczek wprowadzenie](../../../../docs/framework/wcf/getting-started-tutorial.md). W tym temacie przyjęto założenie, że usługa jest skonfigurowana w kodzie. Jeśli chcesz zobaczyć przykład konfigurowania podobnej usługi za pomocą pliku konfiguracji, zobacz [Nazwa użytkownika zabezpieczeń wiadomości](../../../../docs/framework/wcf/samples/message-security-user-name.md)

Aby skonfigurować usługę do uwierzytelniania klientów przy użyciu nazwy użytkownika domeny systemu Windows i haseł, <xref:System.ServiceModel.WSHttpBinding> Użyj i ustaw `Security.Mode` jej właściwość `Message`na. Ponadto należy określić certyfikat x509, który będzie używany do szyfrowania nazwy użytkownika i hasła, gdy są one wysyłane z klienta do usługi.

Na kliencie należy monitować użytkownika o podanie nazwy użytkownika i hasła oraz określić poświadczenia użytkownika na serwerze proxy klienta WCF.

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Aby skonfigurować usługę WCF do uwierzytelniania przy użyciu nazwy użytkownika i hasła domeny systemu Windows

1. Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding>, ustaw tryb zabezpieczeń powiązania z <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, ustaw `ClientCredentialType` powiązanie <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>z i Dodaj punkt końcowy usługi przy użyciu skonfigurowanego powiązania z hostem usługi, jak pokazano w poniższym kodzie:

    ```csharp
    // ...
    WSHttpBinding userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. Określ certyfikat serwera służący do szyfrowania informacji o nazwie użytkownika i hasła przesyłanej przez sieć. Ten kod powinien natychmiast następować po powyższym kodzie. Poniższy przykład używa certyfikatu utworzonego przez plik Setup. bat z przykładowej [nazwy użytkownika zabezpieczeń wiadomości](../../../../docs/framework/wcf/samples/message-security-user-name.md) :

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    Możesz użyć własnego certyfikatu, po prostu zmodyfikuj kod, aby odwołać się do certyfikatu. Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Upewnij się, że certyfikat znajduje się w magazynie certyfikatów osoby zaufane dla komputera lokalnego. Można to zrobić, uruchamiając program MMC. exe i wybierając **plik**, **Dodaj/Usuń przystawkę...** . W oknie dialogowym **Dodawanie lub usuwanie** przystawek wybierz przystawkę **Certyfikaty** , a następnie kliknij przycisk **Dodaj**. W oknie dialogowym Przystawka certyfikatów wybierz pozycję **konto komputera**. Domyślnie certyfikat wygenerowany na podstawie przykładowej nazwy użytkownika zabezpieczeń wiadomości zostanie umieszczony w folderze Personal/Certificates.  Będzie on wyświetlany jako "localhost" w kolumnie wystawiony dla w oknie programu MMC. Przeciągnij i upuść certyfikat do folderu **zaufane osoby** . Umożliwi to usłudze WCF traktowanie certyfikatu jako certyfikatu zaufanego podczas przeprowadzania uwierzytelniania.

## <a name="to-call-the-service-passing-username-and-password"></a>Aby wywołać usługę przekazującą nazwę użytkownika i hasło

1. Aplikacja kliencka musi monitować użytkownika o podanie nazwy użytkownika i hasła. Poniższy kod prosi użytkownika o podanie nazwy użytkownika i hasła.

    > [!WARNING]
    > Tego kodu nie należy używać w środowisku produkcyjnym, ponieważ podczas wprowadzania hasła jest wyświetlane.

    ```csharp
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

2. Utwórz wystąpienie serwera proxy klienta określające poświadczenia klienta, jak pokazano w poniższym kodzie:

    ```csharp
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

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [Zabezpieczenia transportu z uwierzytelnianiem podstawowym](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [Rozproszone zabezpieczenia aplikacji](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
