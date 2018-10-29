---
title: Tryby uwierzytelniania elementu SecurityBindingElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: 2b1601bd84e92b5a39c5c4c91fdfe67537720430
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198400"
---
# <a name="securitybindingelement-authentication-modes"></a>Tryby uwierzytelniania elementu SecurityBindingElement
Windows Communication Foundation (WCF) udostępnia kilka tryby, według których klientów i usług uwierzytelniania ze sobą. Możesz utworzyć zabezpieczeń elementy powiązania dla tych trybów uwierzytelniania przy użyciu metody statycznej na <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy lub przy użyciu konfiguracji. W tym temacie krótko opisano tryby uwierzytelniania 18.  
  
 Przykład użycia elementu jeden z trybów uwierzytelniania, zobacz [porady: Tworzenie elementu SecurityBindingElement dla trybu uwierzytelniania określone](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Konfiguracja podstawowa programowania  
 Poniższa procedura opisuje sposób ustawiania trybu uwierzytelniania w pliku konfiguracji.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Aby ustawić konfigurację trybu uwierzytelniania  
  
1.  Aby [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu Dodawanie [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Dodanie elementu podrzędnego [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu `<customBinding>` elementu.  
  
3.  Dodaj `<security>` elementu `<binding>` elementu.  
  
4.  Ustaw `authenticationMode` atrybutu do jednej z wartości opisanych poniżej. Na przykład, poniższy kod ustawia tryb `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Aby programowo ustawić tryb  
  
1.  Określić zwracany typ, który może być jednym z następujących czynności: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, lub <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2.  Wywołanie odpowiedniej metody statycznej z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. Na przykład, poniższy kod wywoła <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metody.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  Element powiązania służy do tworzenia niestandardowego powiązania. Aby uzyskać więcej informacji, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Tryb opisów  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 W tym trybie uwierzytelniania klienta jest anonimowa, a usługa jest uwierzytelniany przy użyciu certyfikatu X.509. Elementu powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu <`security`> elementu `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 W tym trybie uwierzytelniania klienta jest anonimowa, a usługa jest uwierzytelniany przy użyciu certyfikatu X.509, który jest negocjowane w czasie wykonywania. Elementu powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> metody, gdy wartość `false` jest przekazywany jako pierwszy parametr. Alternatywnie, ustawić `authenticationMode` atrybutu `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Elementu powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 W tym trybie uwierzytelniania klienta nie są uwierzytelniane usługi Zamiast tego klient uwierzytelnia się usługi tokenów zabezpieczeń i odbiera token SAML, który następnie przedstawia na serwer, aby potwierdzić swoją wiedzę na temat klucza współużytkowanego. Usługa nie jest uwierzytelniony do klienta jako takie, ale usługi tokenu zabezpieczającego szyfruje klucz współużytkowany jako część wystawiony token dzięki temu tylko usługa może odszyfrować klucz. Elementu powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 W tym trybie uwierzytelniania klienta nie są uwierzytelniane usługi Zamiast tego klient uwierzytelnia się usługi tokenów zabezpieczeń i odbiera token SAML, który następnie przedstawia na serwer, aby potwierdzić swoją wiedzę na temat klucza współużytkowanego. Wystawiony token jest wyświetlana jako tokenu pomocniczego lub tokenu elementu nośnego; w warstwie protokołu SOAP oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509. Elementu powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 W tym trybie uwierzytelniania klienta nie są uwierzytelniane usługi Zamiast tego klient uwierzytelnia się usługi tokenów zabezpieczeń i odbiera token SAML, który następnie przedstawia na serwer, aby potwierdzić swoją wiedzę na temat klucza współużytkowanego. Wystawiony token jest wyświetlana jako tokenu pomocniczego lub tokenu elementu nośnego; w warstwie protokołu SOAP oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509. Elementu powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 W tym trybie uwierzytelniania klienta nie są uwierzytelniane usługi Zamiast tego klient uwierzytelnia się usługi tokenów zabezpieczeń i odbiera token SAML, który następnie przedstawia na serwer, aby potwierdzić swoją wiedzę na temat klucza współużytkowanego. Wystawiony token jest wyświetlana jako tokenu pomocniczego lub tokenu elementu nośnego; w warstwie protokołu SOAP oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Elementu powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Kerberos  
 W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu biletu protokołu Kerberos. Korzystając z tego samego biletu zapewnia również uwierzytelnianie serwera. Elementu powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `Kerberos`.  
  
> [!NOTE]
>  Aby można było używać ten tryb uwierzytelniania, konto usługi musi być skojarzony z główną nazwę usługi (SPN). Aby to zrobić, należy uruchomić usługi w ramach konta Usługa sieciowa lub konta SYSTEM lokalny. Alternatywnie można użyć narzędzia SetSpn.exe Aby utworzyć nazwę SPN dla konta usługi. W obu przypadkach klient musi używać poprawną nazwę SPN w [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elementu, lub za pomocą <xref:System.ServiceModel.EndpointAddress> konstruktora. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  Gdy `Kerberos` tryb uwierzytelniania jest używany, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> poziomy personifikacji nie są obsługiwane.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 W tym trybie uwierzytelniania klient uwierzytelnia się w usłudze przy użyciu biletu protokołu Kerberos. Token protokołu Kerberos jest wyświetlany w warstwie SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Elementu powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `KerberosOverTransport`.  
  
> [!NOTE]
>  Aby można było używać ten tryb uwierzytelniania, konto usługi musi być skojarzone z nazwy SPN. Aby to zrobić, należy uruchomić usługi w ramach konta Usługa sieciowa lub konta SYSTEM lokalny. Alternatywnie można użyć narzędzia SetSpn.exe Aby utworzyć nazwę SPN dla konta usługi. W obu przypadkach klient musi używać poprawną nazwę SPN w [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elementu, lub za pomocą <xref:System.ServiceModel.EndpointAddress> konstruktora. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest również uwierzytelniany przy użyciu certyfikatu X.509. Elementu powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 W tym trybie uwierzytelniania klient uwierzytelnia się przy użyciu certyfikatu X.509, który pojawia się w warstwie SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest również uwierzytelniany przy użyciu certyfikatu X.509. Powiązanie jest `AsymmetricSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `MutualCertificateDuplex`.  
  
### <a name="mutualsslnegotiated"></a>MutualSslNegotiated  
 W tym trybie uwierzytelniania klienta i usługę uwierzytelniania przy użyciu certyfikatów X.509. Elementu powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> metody, gdy wartość `true` jest przekazywany jako pierwszy parametr. Alternatywnie, ustawić `authenticationMode` atrybutu `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>Mechanizmu SecureConversation  
 Elementu powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> metody. Ta metoda przyjmuje <xref:System.ServiceModel.Channels.SecurityBindingElement> jako parametr, który jest używany podczas inicjowania nawiązywania bezpiecznej sesji. Alternatywnie, ustawić `authenticationMode` atrybutu `SecureConversation`.  
  
 Jeśli określono nie powiązania uruchamiania, a następnie `SspiNegotiated` tryb uwierzytelniania jest używany do ładowania początkowego.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 W tym trybie uwierzytelniania protokół negocjacji służy do uwierzytelniania klienta i serwera. Protokół Kerberos jest używany, jeśli jest to możliwe. w przeciwnym razie LanMan NT (NTLM) jest używany. Elementu powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 W tym trybie uwierzytelniania protokół negocjacji służy do uwierzytelniania klienta i serwera. Protokół Kerberos jest używany, jeśli jest to możliwe. w przeciwnym razie uwierzytelnianie NTLM jest używany. Wynikowy token zostanie wyświetlony w warstwie SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa również jest uwierzytelniany w warstwie transportowej przez certyfikatu X.509. Elementu powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 W tym trybie uwierzytelniania klient uwierzytelnia się do usługi przy użyciu Token nazwy użytkownika, który pojawia się w warstwie SOAP jako podpisany token pomocniczy; oznacza to, że token, który został podpisany przez podpisu wiadomości. Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509. Elementu powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `UserNameForCertificate`.  
  
 Aby uzyskać `UserNameForCertificate` tryb uwierzytelniania, klient i usługa musi używać protokołu WS-Security 1.1.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 W tym trybie uwierzytelniania klient jest uwierzytelniany przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie SOAP jako podpisany token pomocniczy; oznacza to, że token, który został podpisany przez podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509. Elementu powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 W tym trybie uwierzytelniania klient uwierzytelnia za pomocą Token nazwy użytkownika, który pojawia się w warstwie SOAP jako podpisany token pomocniczy; oznacza to, że token, który został podpisany przez podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Elementu powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwrócone przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> metody. Alternatywnie, ustawić `authenticationMode` atrybutu `UserNameOverTransport`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
