---
title: '&lt;authentication&gt; w &lt;serviceCertificate&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 163a035c667c25be4f780daf85c50d96816bd0f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a>&lt;authentication&gt; w &lt;serviceCertificate&gt;, element
Określa ustawienia używane przez serwer proxy klienta do uwierzytelniania certyfikatów usługi, które są uzyskiwane przy użyciu negocjacji SSL/TLS.  
  
 \<System. ServiceModel >  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials >  
\<serviceCertificate >  
\<Uwierzytelnianie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|customCertificateValidatorType|Ciąg. Typ i zestaw używany do walidacji typu niestandardowego.|  
|tryb certificateValidationMode|Określa jeden z trzech trybów używanych do walidacji poświadczenia. Jeśli ustawiono `Custom`, a następnie należy dostarczyć także customCertificateValidator. Wartość domyślna to `ChainTrust`.|  
|revocationMode|Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL). Wartość domyślna to `Online`.|  
|trustedStoreLocation|Jeden z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`. Ta wartość jest używana, gdy negocjowane jest certyfikat usługi do klienta. Sprawdzanie poprawności jest wykonywane przed **zaufane osoby** są przechowywane w lokalizacji określonej magazynu. Wartość domyślna to `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Określa nazwę typu i zestawu i innych danych można znaleźć typu.|  
  
## <a name="certificatevalidationmode-attribute"></a>tryb certificateValidationMode atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedną z następujących wartości: None, uległ awarii, ChainTrust, PeerOrChainTrust, niestandardowe.<br /><br /> Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedną z następujących wartości: NoCheck, Online, w trybie Offline.<br /><br /> Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedną z następujących wartości: LocalMachine lub CurrentUser. Wartość domyślna to CurrentUser. Jeśli aplikacja kliencka jest uruchomiona na koncie systemu, następnie certyfikat jest zwykle w obszarze LocalMachine. Jeśli aplikacja kliencka jest uruchomiona na koncie użytkownika, następnie certyfikat ten jest zwykle w CurrentUser.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Określa certyfikat używany podczas uwierzytelniania usługi do klienta.|  
  
## <a name="remarks"></a>Uwagi  
 `certificateValidationMode` Atrybut ten element konfiguracji określa poziom zaufania używany do uwierzytelniania certyfikatów. Domyślnie po ustawieniu poziomu `ChainTrust`, który określa, że każdy certyfikat musi zostać znaleziony w hierarchii kończy się za zaufany urząd certyfikacji w górnej części łańcucha certyfikatów. Jest to najbardziej bezpieczny tryb. Można również ustawić wartość `PeerOrChainTrust`, która określa, że certyfikaty wystawionej samodzielnie (relacja zaufania elementów równorzędnych) są akceptowane oraz certyfikaty, które znajdują się w łańcuchu zaufanego. Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawione certyfikaty nie muszą można zakupić z zaufanego urzędu. Podczas wdrażania klienta, użyj `ChainTrust` wartość zmiennej. Można również ustawić wartość `Custom` lub `None`. Aby użyć `Custom` wartości, należy także ustawić `customCertificateValidator` atrybutu zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć własnego niestandardowego modułu weryfikacji, musi dziedziczyć z klasy abstrakcyjnej obiektu X509CertificateValidator. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi korzystającej z niestandardowego moduł weryfikacji certyfikatów](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 `revocationMode` Atrybut określa, jak certyfikaty są sprawdzane pod kątem odwołań. Wartość domyślna to `online` co oznacza, że certyfikaty będzie sprawdzana automatycznie odwołania. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ma dwa zadania. Określa pierwszy certyfikat usługi dla klienta podczas komunikacji z punktami końcowymi, których nazwa domeny jest www.contoso.com za pośrednictwem protokołu HTTP. Po drugie go określa lokalizację trybu i magazynu odwołania używany podczas uwierzytelniania.  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Porady: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [\<Uwierzytelnianie >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
