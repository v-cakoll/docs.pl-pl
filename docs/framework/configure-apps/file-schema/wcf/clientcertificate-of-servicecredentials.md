---
title: <clientCertificate> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: 26ebac6439a90959e3a926e6a36c9044251a4aae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107993"
---
# <a name="clientcertificate-of-servicecredentials"></a>\<clientCertificate> of \<serviceCredentials>
Definiuje certyfikat X.509 używany do podpisywania i szyfrowania wiadomości dla formularza klienta usługi w paradygmacie komunikacji dupleksowej.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<clientCertificate>  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [Instrukcje: Tworzenie kontraktu dwukierunkowego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
