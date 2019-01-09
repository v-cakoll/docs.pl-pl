---
title: '&lt;clientCertificate&gt; w &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 7f777fd0e09a1bb9491f346a8e9806627aa63441
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145500"
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a>&lt;clientCertificate&gt; w &lt;serviceCredentials&gt;
Definiuje certyfikat X.509 używany do podpisywania i szyfrowania wiadomości dla formularza klienta usługi w paradygmacie komunikacji dupleksowej.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<clientCertificate >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Uwierzytelnianie >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|Określa opcje uwierzytelniania certyfikatu klienta.|  
|[\<certyfikat >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|Określa certyfikat do użycia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenia, które mają być użyte w uwierzytelnianiu usługi i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest używany, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem do bezpiecznego komunikowania się z klientem. Dzieje się tak, korzystając z paradygmacie komunikacji dupleksowej. We wzorcu bardziej typowego żądanie/odpowiedź klient dołącza swój certyfikat w żądaniu, w której usługa Szyfruj i podpisz jego odpowiedź z powrotem do klienta. W paradygmacie komunikacji dupleksowej jednak usługa ma żądania z klienta i w związku z tym potrzebny certyfikat klienta z wyprzedzeniem, aby zabezpieczyć wiadomość do klienta. W związku z tym należy uzyskać certyfikat klienta w negocjacji out-of-band i Określ certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [jak: Tworzenie kontraktu dwukierunkowego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
 Certyfikat, w tym elemencie jest używany do szyfrowania wiadomości do klienta tylko w przypadku powiązania, które są skonfigurowane przy użyciu `MutualCertificateDuplex` trybu uwierzytelniania zabezpieczeń wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [Instrukcje: Tworzenie kontraktu dwukierunkowego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
