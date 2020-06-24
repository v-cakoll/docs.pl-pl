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
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła

W tym temacie przedstawiono sposób włączania usługi Windows Communication Foundation (WCF) do uwierzytelniania klienta przy użyciu nazwy użytkownika i hasła domeny systemu Windows. Przyjęto założenie, że masz działającą, samoobsługową usługę WCF. Aby zapoznać się z przykładem tworzenia podstawowej samohostowanej usługi WCF, zobacz [samouczek wprowadzenie](../getting-started-tutorial.md). W tym temacie przyjęto założenie, że usługa jest skonfigurowana w kodzie. Jeśli chcesz zobaczyć przykład konfigurowania podobnej usługi za pomocą pliku konfiguracji, zobacz [Nazwa użytkownika zabezpieczeń wiadomości](../samples/message-security-user-name.md).

Aby skonfigurować usługę do uwierzytelniania klientów przy użyciu nazwy użytkownika domeny systemu Windows i haseł, użyj <xref:System.ServiceModel.WSHttpBinding> i ustaw jej `Security.Mode` Właściwość na `Message` . Ponadto należy określić certyfikat x509, który będzie używany do szyfrowania nazwy użytkownika i hasła, gdy są one wysyłane z klienta do usługi.

Na kliencie należy monitować użytkownika o podanie nazwy użytkownika i hasła oraz określić poświadczenia użytkownika na serwerze proxy klienta WCF.

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Aby skonfigurować usługę WCF do uwierzytelniania przy użyciu nazwy użytkownika i hasła domeny systemu Windows

1. Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> , ustaw tryb zabezpieczeń powiązania z <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType> , ustaw `ClientCredentialType` powiązanie z <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType> i Dodaj punkt końcowy usługi przy użyciu skonfigurowanego powiązania z hostem usługi, jak pokazano w poniższym kodzie:

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. Określ certyfikat serwera służący do szyfrowania informacji o nazwie użytkownika i hasła przesyłanej przez sieć. Ten kod powinien natychmiast następować po powyższym kodzie. Poniższy przykład używa certyfikatu utworzonego przez plik setup.bat z przykładowej [nazwy użytkownika zabezpieczeń wiadomości](../samples/message-security-user-name.md) :

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    Możesz użyć własnego certyfikatu, po prostu zmodyfikuj kod, aby odwołać się do certyfikatu. Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów, zobacz [Praca z certyfikatami](working-with-certificates.md). Upewnij się, że certyfikat znajduje się w magazynie certyfikatów osoby zaufane dla komputera lokalnego. Można to zrobić, uruchamiając mmc.exe i wybierając **plik**, **Dodaj/Usuń przystawkę...** . W oknie dialogowym **Dodawanie lub usuwanie przystawek** wybierz **przystawkę Certyfikaty** , a następnie kliknij przycisk **Dodaj**. W oknie dialogowym Przystawka certyfikatów wybierz pozycję **konto komputera**. Domyślnie certyfikat wygenerowany na podstawie przykładowej nazwy użytkownika zabezpieczeń wiadomości zostanie umieszczony w folderze Personal/Certificates.  Będzie on wyświetlany jako "localhost" w kolumnie wystawiony dla w oknie programu MMC. Przeciągnij i upuść certyfikat do folderu **zaufane osoby** . Umożliwi to usłudze WCF traktowanie certyfikatu jako certyfikatu zaufanego podczas przeprowadzania uwierzytelniania.

## <a name="to-call-the-service-passing-username-and-password"></a>Aby wywołać usługę przekazującą nazwę użytkownika i hasło

1. Aplikacja kliencka musi monitować użytkownika o podanie nazwy użytkownika i hasła. Poniższy kod prosi użytkownika o podanie nazwy użytkownika i hasła:

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
    }
    ```

2. Utwórz wystąpienie serwera proxy klienta określające poświadczenia klienta, jak pokazano w poniższym kodzie:

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

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [Zabezpieczenia transportu z uwierzytelnianiem podstawowym](transport-security-with-basic-authentication.md)
- [Rozproszone zabezpieczenia aplikacji](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
