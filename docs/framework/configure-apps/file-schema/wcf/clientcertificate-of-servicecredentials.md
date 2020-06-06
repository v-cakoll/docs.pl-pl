---
title: <clientCertificate> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: a8a78bbfcd9dfbf6975503a845d5bb4e2d24b13d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398135"
---
# <a name="clientcertificate-of-servicecredentials"></a>\<clientCertificate> dla \<serviceCredentials>
Definiuje certyfikat X. 509 używany do podpisywania i szyfrowania komunikatów na kliencie, który tworzy usługę we wzorcu komunikacji dwukierunkowej.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|Określa opcje uwierzytelniania dla certyfikatu klienta.|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|Określa certyfikat, który ma być używany.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Określa poświadczenia, które mają być używane w uwierzytelnianiu usługi oraz ustawienia powiązane z walidacją poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest używany, gdy usługa musi uzyskać certyfikat klienta z wyprzedzeniem w celu bezpiecznego komunikowania się z klientem. Dzieje się tak w przypadku używania wzorca komunikacji dupleksowej. W przypadku bardziej typowego wzorca żądania/odpowiedzi klient zawiera swój certyfikat w żądaniu, którego usługa używa do szyfrowania i podpisywania odpowiedzi z powrotem do klienta. W przypadku wzorca komunikacji dupleksowej usługa nie ma jednak żądania od klienta i w związku z tym potrzebuje certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć komunikat do klienta. W związku z tym należy uzyskać certyfikat klienta w negocjacji poza pasmem i określić certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usług dupleksowych, zobacz [How to: Create a Duplex kontraktu](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
 Certyfikat ustawiony w tym elemencie jest używany do szyfrowania komunikatów na kliencie tylko dla powiązań skonfigurowanych przy użyciu `MutualCertificateDuplex` trybu uwierzytelniania zabezpieczeń wiadomości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
