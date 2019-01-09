---
title: '&lt;authentication&gt; w &lt;serviceCertificate&gt;, element'
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 556310846f8ac307ff9c92c06784eae16937c92c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147957"
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a>&lt;authentication&gt; w &lt;serviceCertificate&gt;, element
Określa ustawienia używane przez serwer proxy klienta do uwierzytelniania certyfikatów usługi, które są uzyskiwane przy użyciu negocjacji SSL/TLS.  
  
 \<system.ServiceModel>  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials>  
\<serviceCertificate >  
\<Uwierzytelnianie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|customCertificateValidatorType|ciąg. Typ i zestaw używany do walidacji typu niestandardowego.|  
|tryb certificateValidationMode|Określa jeden z trzech trybów używanych do walidacji poświadczenia. Jeśli ustawiono `Custom`, a następnie customCertificateValidator musi również zostać dostarczony. Wartość domyślna to `ChainTrust`.|  
|revocationMode|Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL). Wartość domyślna to `Online`.|  
|trustedStoreLocation|Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`. Ta wartość jest używana, gdy certyfikat usługi jest negocjowane do klienta. Sprawdzanie poprawności jest wykonywane względem **zaufane osoby** są przechowywane w lokalizacji określonego magazynu. Wartość domyślna to `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Określa nazwę typu i zestawu i inne dane, używana do znajdowania typu.|  
  
## <a name="certificatevalidationmode-attribute"></a>tryb certificateValidationMode atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jeden z następujących wartości: Brak zaufania elementów równorzędnych, ChainTrust, PeerOrChainTrust, niestandardowe.<br /><br /> Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jeden z następujących wartości: NoCheck, Online, w trybie Offline.<br /><br /> Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jeden z następujących wartości: LocalMachine lub CurrentUser. Wartość domyślna to CurrentUser. Jeśli aplikacja kliencka jest uruchomiona w ramach konta systemowego, następnie certyfikat jest zazwyczaj w obszarze LocalMachine. Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, następnie certyfikat znajduje się zwykle w CurrentUser.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|Określa certyfikat używany podczas uwierzytelniania usługi dla klienta.|  
  
## <a name="remarks"></a>Uwagi  
 `certificateValidationMode` Atrybut ten element konfiguracji określa poziom zaufania, używany do uwierzytelniania certyfikatów. Domyślnie ustawiono poziom `ChainTrust`, która określa, że każdy certyfikat musi zostać znaleziony w hierarchii końcówce zaufanego urzędu certyfikacji w górnej części łańcucha certyfikatów. Jest to najbezpieczniejsza opcja Tryb. Można również ustawić wartość, `PeerOrChainTrust`, która określa, że własnym wystawionych certyfikatów (relacja zaufania elementów równorzędnych) są akceptowane oraz certyfikaty, które znajdują się w zaufanym łańcuchem. Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawionych certyfikatów nie należy zakupić od zaufanego urzędu. Podczas wdrażania klienta, użyj `ChainTrust` jest wartość. Można również ustawić wartość, `Custom` lub `None`. Aby użyć `Custom` wartości, należy także ustawić `customCertificateValidator` atrybutu do zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, musi dziedziczyć z klasy abstrakcyjnej X509CertificateValidator. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 `revocationMode` Atrybut określa, jak certyfikaty są sprawdzane pod kątem odwołań. Wartość domyślna to `online` co oznacza, że certyfikaty będą automatycznie sprawdzane dla odwołania. Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje dwa zadania. Najpierw Określa certyfikat usługi dla klienta do użycia podczas komunikowania się z punktami końcowymi, których nazwa domeny jest `www.contoso.com` za pośrednictwem protokołu HTTP. Po drugie określa wartości odwołania tryb i magazynem lokalizację używane podczas uwierzytelniania.  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
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
 [Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [\<Uwierzytelnianie >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
