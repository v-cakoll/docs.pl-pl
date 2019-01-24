---
title: 'Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 2fb384fe0012b5c0a72e961f027c3db629891e09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532295"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a>Instrukcje: Uwierzytelnianie za pomocą nazwy użytkownika i hasła

W tym temacie pokazano, jak włączyć usługę Windows Communication Foundation (WCF) do uwierzytelniania klienta przy użyciu Windows domena nazwa użytkownika i hasła. Założono, że masz pracy, obsługiwanej samodzielnie usługi WCF. Aby uzyskać przykład tworzenia podstawowych Self-Hosted WCF service, zobacz [Samouczek wprowadzający](../../../../docs/framework/wcf/getting-started-tutorial.md). W tym temacie założono, że usługa jest skonfigurowana w kodzie. Jeśli chcesz zobaczyć przykład konfigurowania podobnej usługi przy użyciu pliku konfiguracji, zobacz [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
  
 Aby skonfigurować usługi w celu uwierzytelnienia klientów przy użyciu nazwy użytkownika i hasła domeny Windows, użyj <xref:System.ServiceModel.WSHttpBinding> i ustaw jego `Security.Mode` właściwość `Message`. Ponadto należy określić X509 certyfikat używany do szyfrowania nazwę użytkownika i hasło są wysyłane z klienta do usługi.  
  
 Na komputerze klienckim możesz monitować użytkownika o nazwę użytkownika i hasło i określ poświadczenia użytkownika na serwerze proxy klienta WCF.  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a>Aby skonfigurować usługi WCF w celu uwierzytelnienia przy użyciu Windows domena nazwa użytkownika i hasło
  
1.  Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding>, ustawianie trybu zabezpieczeń wiązania `SecurityMode.Message`ustaw `ClientCredentialType` wiązania `MessageCredentialType.UserName`i Dodaj punkt końcowy usługi za pomocą skonfigurowanego powiązania host usługi, jak pokazano w poniższym kodzie:  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  Określ certyfikat używany do szyfrowania nazwy użytkownika i hasło informacje przesyłane przez sieć. Ten kod powinien natychmiast wykonaj powyższy kod. W poniższym przykładzie użyto certyfikatu, który jest tworzony przez plik setup.bat z [nazwa użytkownika zabezpieczeń komunikatów](../../../../docs/framework/wcf/samples/message-security-user-name.md) próbki:  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     Możesz użyć własnego certyfikatu, po prostu zmodyfikuj kod do odwoływania się do certyfikatu. Aby uzyskać więcej informacji na temat tworzenia i wykorzystywania certyfikatów Zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Upewnij się, że certyfikat znajduje się w magazynie certyfikatów zaufanych osób na lokalnym komputerze. Można to zrobić, uruchamiając mmc.exe i wybierając **pliku**, **Dodaj/Usuń przystawkę...**  elementu menu. W **Dodawanie lub usuwanie przystawek** okno dialogowe, wybierz opcję **certyfikatów w przystawce** i kliknij przycisk **Dodaj**. W przystawce Certyfikaty w oknie dialogowym wybierz **konto komputera**. Domyślnie certyfikat wygenerowany na podstawie próbki nazwa użytkownika zabezpieczeń komunikatów będą znajdować się w folderze Personal/Certificates.  Będzie ono wyświetlane jako "localhost", w obszarze wystawiony dla kolumn w oknie konsoli MMC. Przeciąganie i upuszczanie certyfikat do **zaufane osoby** folderu. Umożliwi to WCF do traktowania certyfikatu jako zaufanego certyfikatu podczas uwierzytelniania.  
  
## <a name="to-call-the-service-passing-username-and-password"></a>Aby wywołać usługę, przekazując nazwę użytkownika i hasło  
  
1.  Aplikacja kliencka musi monit o wprowadzenie nazwy użytkownika i hasła. Poniższy kod monituje użytkownika o nazwę użytkownika i hasło.  
  
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
  
2.  Utwórz wystąpienie obiektu serwera proxy klienta, określając poświadczenia klienta, jak pokazano w poniższym kodzie:  
  
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
