---
title: '&lt;authentication&gt; w &lt;clientCertificate&gt;, element'
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 97c742cbcaeba10bc7fcf88a461360b96beebc22
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147112"
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a>&lt;authentication&gt; w &lt;clientCertificate&gt;, element
Określa zachowania uwierzytelnienia dla certyfikatów klienta używanych przez usługę.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<clientCertificate >  
\<Uwierzytelnianie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|customCertificateValidatorType|Opcjonalny ciąg. Typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`.|  
|tryb certificateValidationMode|Opcjonalne wyliczenie. Określa jeden z trybów używanych do walidacji poświadczenia. Ten atrybut jest <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu. Jeśli ustawiono <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, a następnie `customCertificateValidator` musi również zostać dostarczony. Wartość domyślna to <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.|  
|includeWindowsGroups|Opcjonalny atrybut typu wartość logiczna. Określa, jeśli grupy Windows znajdują się w kontekście zabezpieczeń. Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ powoduje ona rozszerzenia całej grupy. Ustaw ten atrybut na `false` Jeśli potrzebujesz nawiązać listy grup należy użytkownik.|  
|mapClientCertificateToWindowsAcccount|Wartość logiczna. Określa, czy klienta mogą być mapowane do tożsamości Windows przy użyciu certyfikatu. Usługi Active Directory musi być włączona w tym celu.|  
|revocationMode|Opcjonalne wyliczenie. Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (RCL). Wartość domyślna to `Online`. Ta wartość jest ignorowana, gdy za pomocą zabezpieczeń transportu HTTP.|  
|trustedStoreLocation|Opcjonalne wyliczenie. Jedną z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`. Ta wartość jest używana, gdy certyfikat usługi jest negocjowane do klienta. Sprawdzanie poprawności jest wykonywane względem **zaufane osoby** są przechowywane w lokalizacji określonego magazynu. Wartość domyślna to `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType atrybutu  
  
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
|Wyliczenie|Jeden z następujących wartości: NoCheck, Online, w trybie Offline. Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`. Wartość domyślna to `CurrentUser`. Jeśli aplikacja kliencka jest uruchomiona w ramach konta systemowego, a następnie certyfikatu wynosi zazwyczaj `LocalMachine`. Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, a następnie certyfikat znajduje się zwykle w `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|Definiuje certyfikat X.509 używany do uwierzytelniania klienta do usługi.|  
  
## <a name="remarks"></a>Uwagi  
 `<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy. Pozwala dostosować sposób uwierzytelniania klientów. Możesz ustawić `certificateValidationMode` atrybutu `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, lub `Custom`. Domyślnie ustawiono poziom `ChainTrust`, która określa, że każdy certyfikat musi zostać znaleziony w hierarchii certyfikatów kończy się rozszerzeniem *główny urząd* w górnej części łańcucha. Jest to najbezpieczniejsza opcja Tryb. Można również ustawić wartość, `PeerOrChainTrust`, która określa, że własnym wystawionych certyfikatów (relacja zaufania elementów równorzędnych) są akceptowane oraz certyfikaty, które znajdują się w zaufanym łańcuchem. Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawionych certyfikatów nie należy zakupić od zaufanego urzędu. Podczas wdrażania klienta, użyj `ChainTrust` jest wartość.  
  
 Można również ustawić wartość, `Custom`. Po ustawieniu `Custom` wartości, należy także ustawić `customCertificateValidatorType` atrybutu do zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć własny niestandardowy moduł sprawdzania poprawności, musi dziedziczyć abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod określa certyfikat X.509 i typu niestandardowego sprawdzania poprawności w `<authentication>` elementu.  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
