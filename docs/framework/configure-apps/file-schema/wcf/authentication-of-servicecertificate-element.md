---
title: <authentication><serviceCertificate>elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398228"
---
# <a name="authentication-of-servicecertificate-element"></a>\<authentication>\<serviceCertificate>elementu
Określa ustawienia używane przez serwer proxy klienta do uwierzytelniania certyfikatów usługi, które są uzyskiwane przy użyciu negocjacji SSL/TLS.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|customCertificateValidatorType|Ciąg. Typ i zestaw używany do walidacji typu niestandardowego.|  
|certificateValidationMode|Określa jeden z trzech trybów używanych do walidacji poświadczeń. Jeśli jest ustawiona na `Custom` , należy również podać CustomCertificateValidator. Wartość domyślna to `ChainTrust`.|  
|odwołaniemode|Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL). Wartość domyślna to `Online`.|  
|trustedStoreLocation|Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser` . Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem. Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu. Wartość domyślna to `CurrentUser`.|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedna z następujących wartości: None, zaufania elementów równorzędnych, ChainTrust, PeerOrChainTrust, Custom.<br /><br /> Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>Atrybut odwołania  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedna z następujących wartości: NOCHECK, online i offline.<br /><br /> Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedna z następujących wartości: LocalMachine lub CurrentUser. Wartość domyślna to CurrentUser. Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, certyfikat jest zwykle w obszarze LocalMachine. Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w CurrentUser.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|Określa certyfikat, który ma być używany podczas uwierzytelniania usługi dla klienta.|  
  
## <a name="remarks"></a>Uwagi  
 `certificateValidationMode`Atrybut tego elementu konfiguracji określa poziom zaufania używany do uwierzytelniania certyfikatów. Domyślnie poziom jest ustawiony na `ChainTrust` , który określa, że każdy certyfikat musi znajdować się w hierarchii certyfikatów kończących się zaufanym urzędem certyfikacji w górnej części łańcucha. Jest to najbardziej bezpieczny tryb. Można również ustawić wartość na `PeerOrChainTrust` , która określa, że certyfikaty samodzielne (relacja równorzędna) są akceptowane, a także certyfikaty, które znajdują się w zaufanym łańcuchu. Ta wartość jest używana podczas tworzenia i debugowania klientów i usług, ponieważ certyfikaty wystawione przez siebie nie muszą zostać zakupione z zaufanego urzędu. Podczas wdrażania klienta należy `ChainTrust` zamiast tego użyć wartości. Możesz również ustawić wartość na `Custom` lub `None` . Aby użyć `Custom` wartości, należy również ustawić `customCertificateValidator` atrybut na zestaw i typ używany do walidacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej X509CertificateValidator. Aby uzyskać więcej informacji, zobacz [How to: Create a Service, która korzysta z niestandardowego modułu weryfikacji certyfikatu](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
 Ten `revocationMode` atrybut określa, jak certyfikaty są sprawdzane pod kątem odwołania. Wartość domyślna `online` wskazuje, że certyfikaty będą sprawdzane automatycznie w celu odwołania. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje dwa zadania. Najpierw określa certyfikat usługi, który ma być używany przez klienta podczas komunikowania się z punktami końcowymi, których nazwa domeny znajduje się `www.contoso.com` za pośrednictwem protokołu HTTP. Po drugie określa tryb odwołania i lokalizację magazynu używane podczas uwierzytelniania.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
- [Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [Zabezpieczanie klientów](../../../wcf/securing-clients.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
