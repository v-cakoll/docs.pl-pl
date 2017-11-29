---
title: '&lt;clientCertificate&gt; w &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc4b3251a85a6926c93f418c154b4eabbd44092f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a>&lt;clientCertificate&gt; w &lt;serviceCredentials&gt;
Definiuje certyfikat X.509 używany do podpisywania i szyfrowania wiadomości dla formularza klienta usługi we wzorcu komunikację dupleksową.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceCredentials >  
\<clientCertificate >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
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
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenia, które mają być użyte w uwierzytelnianiu usługi, i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element jest używany, gdy usługa musi mieć certyfikat klienta z wyprzedzeniem do bezpiecznego komunikowania się z klientem. Dzieje się tak podczas używania wzorca komunikację dupleksową. We wzorcu bardziej typowego żądania/odpowiedzi klienta obejmuje jego certyfikat w żądaniu, usługa używa do szyfrowania i podpisywania odpowiedzi do klienta. We wzorcu komunikację dupleksową jednak usługa ma żądania z klienta i dlatego wymaga certyfikatu klienta z wyprzedzeniem, aby zabezpieczyć wiadomość do klienta. W związku z tym należy uzyskać certyfikat klienta w negocjacji poza pasmem oraz określić certyfikat przy użyciu tego elementu. Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [porady: tworzenie kontraktu dwukierunkowego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
 Certyfikat w tym elemencie jest używany do szyfrowania wiadomości do klienta tylko dla powiązania, które są skonfigurowane przy użyciu `MutualCertificateDuplex` trybu uwierzytelniania zabezpieczeń wiadomości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [Porady: tworzenie kontraktu dwukierunkowego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
