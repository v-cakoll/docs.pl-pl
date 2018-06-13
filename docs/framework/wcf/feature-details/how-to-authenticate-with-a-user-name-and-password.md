---
title: 'Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: b37d296312be4c7694a2db55d85dd618e3252f14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493317"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła

W tym temacie przedstawiono sposób włączania usługi Windows Communication Foundation (WCF) do uwierzytelniania klienta z nazwę i hasło użytkownika domeny systemu Windows. Zakłada się, że masz pracy, usługa hostowania samoobsługowego WCF. Na przykład tworzenia podstawowych hostowania samoobsługowego WCF usługi, zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md). W tym temacie założono, że usługa jest skonfigurowana w kodzie. Jeśli chcesz zobaczyć Zobacz przykład konfigurowania podobne usługi przy użyciu pliku konfiguracji [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Aby skonfigurować usługę do uwierzytelniania klientów przy użyciu nazwy użytkownika i hasła domeny systemu Windows, użyj <xref:System.ServiceModel.WSHttpBinding> i ustawić jej `Security.Mode` właściwości `Message`. Ponadto należy określić X509 certyfikat używany do szyfrowania nazwy użytkownika i hasła są wysyłane z klienta do usługi.  
  
 Na komputerze klienckim możesz monit o podanie nazwy użytkownika i hasła i określić poświadczenia użytkownika na serwerze proxy klienta WCF.  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Aby skonfigurować usługi WCF w celu uwierzytelnienia przy użyciu nazwy użytkownika domeny systemu Windows i hasło
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding>, ustawianie trybu zabezpieczeń powiązania `SecurityMode.Message`ustaw `ClientCredentialType` powiązania `MessageCredentialType.UserName`i Dodaj punkt końcowy usługi przy użyciu skonfigurowanego powiązania do hosta usługi, jak pokazano w poniższym kodzie:  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  Określ certyfikat używany do szyfrowania nazwy użytkownika i hasła informacje przesyłane przez sieć. Ten kod powinna występować zaraz po powyższym kodzie. W poniższym przykładzie użyto certyfikatu, który jest tworzony przy użyciu pliku pliku setup.bat z [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md) próbki:  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Można użyć własnego certyfikatu, po prostu zmodyfikuj kod do odwoływania się do certyfikatu. Aby uzyskać więcej informacji na temat tworzenia i używania certyfikatów Zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Upewnij się, że certyfikat znajduje się w magazynie certyfikatów zaufanych osób na komputerze lokalnym. Aby to zrobić, mmc.exe uruchomienie i wybranie **pliku**, **Dodaj/Usuń przystawkę...**  elementu menu. W **Dodawanie lub usuwanie przystawek** okno dialogowe, wybierz opcję **certyfikatów przystawki** i kliknij przycisk **Dodaj**. W oknie dialogowym przystawki Certyfikaty wybierz **konto komputera**. Domyślnie certyfikat generowane na podstawie próbki nazwa użytkownika zabezpieczeń komunikatów będą się znajdować w folderze osobiste/certyfikaty.  Będzie on wyświetlany jako "localhost" w obszarze wystawiony dla kolumny w oknie konsoli MMC. Przeciągnij i upuść certyfikatu do **zaufane osoby** folderu. Pozwoli to WCF zaliczenie certyfikatu zaufanego certyfikatu podczas uwierzytelniania.  
  
## <a name="to-call-the-service-passing-username-and-password"></a>Do wywołania tej usługi przekazywania nazwy użytkownika i hasła  
  
1.  Aplikacja kliencka musi Monituj użytkownika o nazwę użytkownika i hasło. Poniższy kod monituje użytkownika o nazwę użytkownika i hasło.  
  
    > [!WARNING]
    >  Ten kod nie należy używać w środowisku produkcyjnym, ponieważ hasło jest wyświetlane podczas wprowadzania.  
  
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
  
2.  Utwórz wystąpienie serwera proxy klienta określania poświadczeń klienta, jak pokazano w poniższym kodzie:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.SecurityMode>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>  
 [Zabezpieczenia transportu z uwierzytelnianiem podstawowym](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 [Rozproszone zabezpieczenia aplikacji](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
