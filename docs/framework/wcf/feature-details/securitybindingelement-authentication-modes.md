---
title: Tryby uwierzytelniania elementu SecurityBindingElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 715c813015fdb4b52444efca0bdcfc99acc92c21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="securitybindingelement-authentication-modes"></a>Tryby uwierzytelniania elementu SecurityBindingElement
Windows Communication Foundation (WCF) zapewnia kilka metod za pomocą których klienci usług uwierzytelniać się na siebie. Można utworzyć zabezpieczeń elementy powiązania dla tych trybach uwierzytelniania przy użyciu metod statycznych na <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy lub przy użyciu konfiguracji. W tym temacie opisano tryby uwierzytelniania 18.  
  
 Na przykład za pomocą elementu dla jednej z metod uwierzytelniania, zobacz [porady: Tworzenie elementu SecurityBindingElement dla trybu uwierzytelniania określone](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Programowanie konfiguracji podstawowej  
 W poniższej procedurze opisano sposób ustawiania trybu uwierzytelniania w pliku konfiguracji.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Aby ustawić tryb uwierzytelniania w konfiguracji  
  
1.  Aby [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu, Dodaj [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Jako element podrzędny dodać [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu `<customBinding>` elementu.  
  
3.  Dodaj `<security>` elementu `<binding>` elementu.  
  
4.  Ustaw `authenticationMode` atrybutu na jedną z wartości opisanych poniżej. Na przykład następujący kod ustawia tryb `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Aby ustawić tryb programowo  
  
1.  Określić typ zwracany może być jedną z następujących czynności: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, lub <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2.  Wywołanie odpowiedniej metody statycznej <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. Na przykład poniższy kod wywołania <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metody.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  Element powiązania umożliwia utworzenie niestandardowego powiązania. Aby uzyskać więcej informacji, zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Tryb opisów  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 Z tego trybu uwierzytelniania klienta jest anonimowy i Usługa uwierzytelniania za pomocą certyfikatu X.509. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybut <`security`> elementu `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 Z tego trybu uwierzytelniania klienta jest anonimowy i Usługa uwierzytelniania za pomocą certyfikatu X.509, który jest negocjowane w czasie wykonywania. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> metody, gdy wartość `false` jest przekazywana jako pierwszy parametr. Możesz również ustawić `authenticationMode` atrybutu `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie za pomocą certyfikatu X.509, który pojawia się w warstwie protokołu SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Z tego trybu uwierzytelniania klienta nie uwierzytelniania usługi Zamiast tego klient uwierzytelnia do usługi tokenu zabezpieczeń i otrzymuje token SAML, który stanowi następnie do serwera w celu potwierdzenia jej wiedzy klucza wspólnego. Usługi nie jest uwierzytelniony do klienta tak, ale usługi tokenu zabezpieczającego szyfruje klucz udostępniony jako część wystawionego tokenu, aby tylko usługa może odszyfrować klucza. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 Z tego trybu uwierzytelniania klienta nie uwierzytelniania usługi Zamiast tego klient uwierzytelnia do usługi tokenu zabezpieczeń i otrzymuje token SAML, który stanowi następnie do serwera w celu potwierdzenia jej wiedzy klucza wspólnego. Wystawiony token, który znajduje się w warstwie protokołu SOAP jako tokenu pomocniczego lub tokenu elementu nośnego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa uwierzytelnia klienta, za pomocą certyfikatu X.509. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 Z tego trybu uwierzytelniania klienta nie uwierzytelniania usługi Zamiast tego klient uwierzytelnia do usługi tokenu zabezpieczeń i otrzymuje token SAML, który stanowi następnie do serwera w celu potwierdzenia jej wiedzy klucza wspólnego. Wystawiony token, który znajduje się w warstwie protokołu SOAP jako tokenu pomocniczego lub tokenu elementu nośnego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 Z tego trybu uwierzytelniania klienta nie uwierzytelniania usługi Zamiast tego klient uwierzytelnia do usługi tokenu zabezpieczeń i otrzymuje token SAML, który stanowi następnie do serwera w celu potwierdzenia jej wiedzy klucza wspólnego. Wystawiony token, który znajduje się w warstwie protokołu SOAP jako tokenu pomocniczego lub tokenu elementu nośnego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Element powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Kerberos  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu biletu protokołu Kerberos. Korzystając z tego samego biletu także uwierzytelniania serwera. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `Kerberos`.  
  
> [!NOTE]
>  Aby można było używać tego trybu uwierzytelniania, musi być skojarzony z główną nazwę usługi (SPN) konta usługi. W tym celu należy uruchomić usługę w ramach konta Usługa sieciowa lub konta SYSTEM lokalny. Można również użyć narzędzia SetSpn.exe, aby utworzyć nazwę SPN konta usługi. W obu przypadkach klient musi używać poprawną nazwę SPN w [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elementu, lub za pomocą <xref:System.ServiceModel.EndpointAddress> konstruktora. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  Gdy `Kerberos` tryb uwierzytelniania jest używany, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> i <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> poziomy personifikacji nie są obsługiwane.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu biletu protokołu Kerberos. Token protokołu Kerberos jest wyświetlany w warstwie protokołu SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Element powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `KerberosOverTransport`.  
  
> [!NOTE]
>  Aby można było używać tego trybu uwierzytelniania, konto usługi musi być skojarzony z główną nazwą usługi. W tym celu należy uruchomić usługę w ramach konta Usługa sieciowa lub konta SYSTEM lokalny. Można również użyć narzędzia SetSpn.exe, aby utworzyć nazwę SPN konta usługi. W obu przypadkach klient musi używać poprawną nazwę SPN w [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elementu, lub za pomocą <xref:System.ServiceModel.EndpointAddress> konstruktora. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie za pomocą certyfikatu X.509, który pojawia się w warstwie protokołu SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest również uwierzytelniony za pomocą certyfikatu X.509. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie za pomocą certyfikatu X.509, który pojawia się w warstwie protokołu SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa jest również uwierzytelniony za pomocą certyfikatu X.509. Powiązanie jest `AsymmetricSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `MutualCertificateDuplex`.  
  
### <a name="mutalsslnegotiation"></a>MutalSslNegotiation  
 Z tego trybu uwierzytelniania klient i Usługa uwierzytelniania za pomocą certyfikatów X.509. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> metody, gdy wartość `true` jest przekazywana jako pierwszy parametr. Możesz również ustawić `authenticationMode` atrybutu `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> metody. Ta metoda przyjmuje <xref:System.ServiceModel.Channels.SecurityBindingElement> jako parametr, który jest używany podczas inicjowania do nawiązywania bezpiecznej sesji. Możesz również ustawić `authenticationMode` atrybutu `SecureConversation`.  
  
 Jeśli określono nie powiązania uruchamiania, a następnie `SspiNegotiated` tryb uwierzytelniania jest używany do ładowania początkowego.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 Z tego trybu uwierzytelniania protokół negocjacji służy do uwierzytelniania klienta i serwera. Protokół Kerberos jest używany, jeśli to możliwe. w przeciwnym razie jest używana LanMan NT (NTLM). Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 Z tego trybu uwierzytelniania protokół negocjacji służy do uwierzytelniania klienta i serwera. Protokół Kerberos jest używany, jeśli to możliwe. w przeciwnym razie uwierzytelnianie NTLM jest używany. Wynikowy token zostanie wyświetlony w warstwie protokołu SOAP jako tokenu pomocniczego; oznacza to, że token, który podpisuje podpisu wiadomości. Usługa Ponadto jest uwierzytelniany w przypadku warstwy transportu za pomocą certyfikatu X.509. Element powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie usługi przy użyciu tokenu nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego; oznacza to, że token, który został podpisany przez podpisu wiadomości. Usługa uwierzytelnia klienta, za pomocą certyfikatu X.509. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `UserNameForCertificate`.  
  
 Aby uzyskać `UserNameForCertificate` tryb uwierzytelniania, klient i usługa muszą używać 1.1 WS-Security.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 Z tego trybu uwierzytelniania klienta jest uwierzytelniany przy użyciu Token nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego; oznacza to, że token, który został podpisany przez podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 Z tego trybu uwierzytelniania klient przeprowadza uwierzytelnianie przy użyciu tokenu nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego; oznacza to, że token, który został podpisany przez podpisu wiadomości. Usługa jest uwierzytelniany przy użyciu certyfikatu X.509 w warstwie transportowej. Element powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwrócony przez <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> metody. Możesz również ustawić `authenticationMode` atrybutu `UserNameOverTransport`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
