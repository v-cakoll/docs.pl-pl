---
title: Tryby uwierzytelniania elementu SecurityBindingElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: d55bc0e1ccd45409c09ddeba820ed74d00ae86f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949342"
---
# <a name="securitybindingelement-authentication-modes"></a>Tryby uwierzytelniania elementu SecurityBindingElement
Windows Communication Foundation (WCF) oferuje kilka trybów, za pomocą których klienci i usługi mogą się wzajemnie uwierzytelniać. Można utworzyć elementy powiązań zabezpieczeń dla tych trybów uwierzytelniania przy użyciu metod statycznych w <xref:System.ServiceModel.Channels.SecurityBindingElement> klasie lub przez konfigurację. W tym temacie krótko opisano 18 trybów uwierzytelniania.  
  
 Przykład korzystania z elementu dla jednego z trybów uwierzytelniania można znaleźć w temacie [How to: Utwórz elementu SecurityBindingElement dla określonego trybu](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)uwierzytelniania.  
  
## <a name="basic-configuration-programming"></a>Podstawowe programowanie konfiguracji  
 Poniższa procedura opisuje sposób ustawiania trybu uwierzytelniania w pliku konfiguracji.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Aby ustawić tryb uwierzytelniania w konfiguracji  
  
1. Do elementu [powiązań > Dodaj niestandardowy >Binding. \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
  
2. Jako element podrzędny Dodaj `<customBinding>` [ \<element > powiązania](../../../../docs/framework/misc/binding.md) do elementu.  
  
3. `<security>` Dodaj element`<binding>` do elementu.  
  
4. `authenticationMode` Ustaw atrybut na jedną z wartości opisanych poniżej. Na przykład poniższy kod ustawia tryb na `AnonymousForCertificate`.  
  
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
  
1. Określ zwracany typ, który może mieć jedną z następujących wartości <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>:, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, lub <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2. Wywoływanie odpowiedniej statycznej metody <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. Na przykład poniższy kod wywołuje <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metodę.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3. Użyj elementu Binding, aby utworzyć niestandardowe powiązanie. Aby uzyskać więcej informacji, zobacz [niestandardowe powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Opisy trybu  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 W przypadku tego trybu uwierzytelniania klient jest anonimowy i usługa jest uwierzytelniana przy użyciu certyfikatu X. 509. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> przez metodę. Alternatywnie Ustaw `authenticationMode` atrybut <`security`elementu > na `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 W tym trybie uwierzytelniania klient jest anonimowy i usługa jest uwierzytelniana przy użyciu certyfikatu X. 509, który jest negocjowany w czasie wykonywania. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> przez `false` metodę, gdy wartość jest przekazana dla pierwszego parametru. Alternatywnie możesz ustawić `authenticationMode` atrybut na `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 W tym trybie uwierzytelniania klient jest uwierzytelniany przy użyciu certyfikatu X. 509, który pojawia się na warstwie protokołu SOAP jako tokenu pomocniczego. oznacza to token, który podpisze komunikat. Usługa jest uwierzytelniana przy użyciu certyfikatu X. 509 w warstwie transportowej. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 W przypadku tego trybu uwierzytelniania klient nie jest uwierzytelniany w usłudze w taki sposób; Zamiast tego klient jest uwierzytelniany w usłudze tokenu zabezpieczającego i odbiera token SAML, który następnie przedstawia serwer, aby udowodnić swoją wiedzę o kluczu współdzielonym. Usługa nie jest uwierzytelniana klientowi w taki sposób, że usługa tokenu zabezpieczającego szyfruje klucz współużytkowany jako część wystawionego tokenu, dzięki czemu tylko usługa może odszyfrować klucz. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 W przypadku tego trybu uwierzytelniania klient nie jest uwierzytelniany w usłudze w taki sposób; Zamiast tego klient jest uwierzytelniany w usłudze tokenu zabezpieczającego i odbiera token SAML, który następnie przedstawia serwer, aby udowodnić swoją wiedzę o kluczu współdzielonym. Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako token pomocniczy lub token okaziciela; oznacza to token, który podpisze komunikat. Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 W przypadku tego trybu uwierzytelniania klient nie jest uwierzytelniany w usłudze w taki sposób; Zamiast tego klient jest uwierzytelniany w usłudze tokenu zabezpieczającego i odbiera token SAML, który następnie przedstawia serwer, aby udowodnić swoją wiedzę o kluczu współdzielonym. Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako token pomocniczy lub token okaziciela; oznacza to token, który podpisze komunikat. Usługa jest uwierzytelniana przy użyciu certyfikatu X. 509. Element powiązania zabezpieczeń jest <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 W przypadku tego trybu uwierzytelniania klient nie jest uwierzytelniany w usłudze w taki sposób; Zamiast tego klient jest uwierzytelniany w usłudze tokenu zabezpieczającego i odbiera token SAML, który następnie przedstawia serwer, aby udowodnić swoją wiedzę o kluczu współdzielonym. Wystawiony token jest wyświetlany w warstwie protokołu SOAP jako token pomocniczy lub token okaziciela; oznacza to token, który podpisze komunikat. Usługa jest uwierzytelniana przy użyciu certyfikatu X. 509 w warstwie transportowej. Element powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Kerberos  
 W tym trybie uwierzytelniania klient jest uwierzytelniany w usłudze przy użyciu biletu protokołu Kerberos. Ten sam bilet zapewnia również uwierzytelnianie serwera. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `Kerberos`.  
  
> [!NOTE]
> Aby można było korzystać z tego trybu uwierzytelniania, konto usługi musi być skojarzone z główną nazwą usługi (SPN). W tym celu należy uruchomić usługę w ramach konta usługi sieciowej lub lokalnego konta SYSTEMowego. Alternatywnie możesz utworzyć nazwę SPN dla konta usługi za pomocą narzędzia SetSpn. exe. W obu przypadkach klient musi używać prawidłowej nazwy SPN w <xref:System.ServiceModel.EndpointAddress> [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elemencie ServicePrincipalName > lub przy użyciu konstruktora. Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
> Gdy jest używany tryb <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> uwierzytelniania, poziomy personifikacji nie są obsługiwane. `Kerberos`  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 W tym trybie uwierzytelniania klient jest uwierzytelniany w usłudze przy użyciu biletu protokołu Kerberos. Token Kerberos jest wyświetlany w warstwie protokołu SOAP jako token pomocniczy. oznacza to token, który podpisze komunikat. Usługa jest uwierzytelniana przy użyciu certyfikatu X. 509 w warstwie transportowej. Element powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `KerberosOverTransport`.  
  
> [!NOTE]
> Aby można było korzystać z tego trybu uwierzytelniania, konto usługi musi być skojarzone z nazwą SPN. W tym celu należy uruchomić usługę w ramach konta usługi sieciowej lub lokalnego konta SYSTEMowego. Alternatywnie możesz utworzyć nazwę SPN dla konta usługi za pomocą narzędzia SetSpn. exe. W obu przypadkach klient musi używać prawidłowej nazwy SPN w <xref:System.ServiceModel.EndpointAddress> [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elemencie ServicePrincipalName > lub przy użyciu konstruktora. Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 W tym trybie uwierzytelniania klient jest uwierzytelniany przy użyciu certyfikatu X. 509, który pojawia się na warstwie protokołu SOAP jako tokenu pomocniczego. oznacza to token, który podpisze komunikat. Usługa jest również uwierzytelniana przy użyciu certyfikatu X. 509. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 W tym trybie uwierzytelniania klient jest uwierzytelniany przy użyciu certyfikatu X. 509, który pojawia się na warstwie protokołu SOAP jako tokenu pomocniczego. oznacza to token, który podpisze komunikat. Usługa jest również uwierzytelniana przy użyciu certyfikatu X. 509. Powiązanie jest `AsymmetricSecurityBindingElement` zwracane <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `MutualCertificateDuplex`.  
  
### <a name="mutualsslnegotiated"></a>MutualSslNegotiated  
 W przypadku tego trybu uwierzytelniania klient i usługa uwierzytelniają się za pomocą certyfikatów X. 509. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> przez `true` metodę, gdy wartość jest przekazana dla pierwszego parametru. Alternatywnie możesz ustawić `authenticationMode` atrybut na `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> przez metodę. Ta metoda przyjmuje <xref:System.ServiceModel.Channels.SecurityBindingElement> jako parametr, który jest używany podczas inicjowania w celu ustanowienia bezpiecznej sesji. Alternatywnie możesz ustawić `authenticationMode` atrybut na `SecureConversation`.  
  
 Jeśli nie określono powiązania uruchamiania, `SspiNegotiated` tryb uwierzytelniania jest używany na potrzeby ładowania początkowego.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 W przypadku tego trybu uwierzytelniania do uwierzytelniania klienta i serwera jest używany protokół negocjacji. Protokół Kerberos jest używany, jeśli jest to możliwe; w przeciwnym razie jest używane polecenie NT LanMan (NTLM). Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 W przypadku tego trybu uwierzytelniania do uwierzytelniania klienta i serwera jest używany protokół negocjacji. Protokół Kerberos jest używany, jeśli jest to możliwe; w przeciwnym razie jest używane uwierzytelnianie NTLM. Otrzymany token pojawia się na warstwie protokołu SOAP jako token pomocniczy oznacza to token, który podpisze komunikat. Usługa jest również uwierzytelniana w warstwie transportowej przez certyfikat X. 509. Element powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 W tym trybie uwierzytelniania klient jest uwierzytelniany w usłudze przy użyciu tokenu nazwy użytkownika, który pojawia się w warstwie protokołu SOAP jako podpisanego tokenu pomocniczego; oznacza to token podpisany przez sygnaturę wiadomości. Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `UserNameForCertificate`.  
  
 W przypadku trybu uwierzytelniania zarówno klient, jak i usługa muszą korzystać z protokołu WS-Security 1,1. `UserNameForCertificate`  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 W tym trybie uwierzytelniania klient jest uwierzytelniany przy użyciu tokenu nazwy użytkownika, który jest wyświetlany w warstwie protokołu SOAP jako podpisany token pomocniczy; oznacza to token podpisany przez sygnaturę wiadomości. Usługa jest uwierzytelniana przy użyciu certyfikatu X. 509. Element powiązania zabezpieczeń jest `SymmetricSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 W tym trybie uwierzytelniania klient jest uwierzytelniany przy użyciu tokenu nazwy użytkownika, który jest wyświetlany na warstwie protokołu SOAP jako podpisanego tokenu pomocniczego; oznacza to token podpisany przez sygnaturę wiadomości. Usługa jest uwierzytelniana przy użyciu certyfikatu X. 509 w warstwie transportowej. Element powiązania zabezpieczeń jest `TransportSecurityBindingElement` zwracany <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> przez metodę. Alternatywnie możesz ustawić `authenticationMode` atrybut na `UserNameOverTransport`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Instrukcje: Utwórz elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
