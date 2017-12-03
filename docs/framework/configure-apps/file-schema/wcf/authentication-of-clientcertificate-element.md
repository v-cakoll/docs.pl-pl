---
title: '&lt;authentication&gt; w &lt;clientCertificate&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bebbc8b5cc315e92645cbbf0321de53122c7b1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a>&lt;authentication&gt; w &lt;clientCertificate&gt;, element
Określa zachowania uwierzytelnienia dla certyfikatów klienta używanych przez usługę.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceCredentials >  
\<clientCertificate >  
\<Uwierzytelnianie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|customCertificateValidatorType|Opcjonalny ciąg. Typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiane podczas `certificateValidationMode` ma ustawioną wartość `Custom`.|  
|tryb certificateValidationMode|Opcjonalne wyliczenie. Określa jeden z trybów używanych do walidacji poświadczenia. Ten atrybut jest <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu. Jeśli ustawiono <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, a następnie `customCertificateValidator` należy dostarczyć także. Wartość domyślna to <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.|  
|właściwości includeWindowsGroups|Opcjonalna wartość logiczna. Określa, czy grupy systemu Windows znajdują się w kontekście zabezpieczeń. Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ jej wynikiem rozszerzenia całej grupy. Ten atrybut na `false` Jeśli nie musisz ustanowić listę grup należy użytkownik.|  
|mapClientCertificateToWindowsAcccount|Wartość logiczna. Określa, czy klient może być mapowany na tożsamość systemu Windows przy użyciu certyfikatu. W tym celu należy włączyć usługi Active Directory.|  
|revocationMode|Opcjonalne wyliczenie. Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (RCL). Wartość domyślna to `Online`. Ta wartość jest ignorowana w przypadku korzystania z zabezpieczeń transportu HTTP.|  
|trustedStoreLocation|Opcjonalne wyliczenie. Jeden z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`. Ta wartość jest używana, gdy negocjowane jest certyfikat usługi do klienta. Sprawdzanie poprawności jest wykonywane przed **zaufane osoby** są przechowywane w lokalizacji określonej magazynu. Wartość domyślna to `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType atrybutu  
  
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
|Wyliczenie|Jedną z następujących wartości: NoCheck, Online, w trybie Offline. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`. Wartość domyślna to `CurrentUser`. Jeśli aplikacja kliencka jest uruchomiona na koncie systemu, a następnie certyfikat jest zwykle w obszarze `LocalMachine`. Jeśli aplikacja kliencka jest uruchomiona na koncie użytkownika, a następnie certyfikat jest zwykle w `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|Definiuje certyfikat X.509 używany do uwierzytelniania klienta do usługi.|  
  
## <a name="remarks"></a>Uwagi  
 `<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy. Umożliwia dostosowanie sposobu uwierzytelniania klientów. Można ustawić `certificateValidationMode` atrybutu `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, lub `Custom`. Domyślnie po ustawieniu poziomu `ChainTrust`, który określa, że każdy certyfikat musi zostać znaleziony w hierarchii certyfikatów w *główny urząd* w górnej części łańcucha. Jest to najbardziej bezpieczny tryb. Można również ustawić wartość `PeerOrChainTrust`, która określa, że certyfikaty wystawionej samodzielnie (relacja zaufania elementów równorzędnych) są akceptowane oraz certyfikaty, które znajdują się w łańcuchu zaufanego. Ta wartość jest używana podczas opracowywania i debugowania klientów i usług, ponieważ własnym wystawione certyfikaty nie muszą można zakupić z zaufanego urzędu. Podczas wdrażania klienta, użyj `ChainTrust` wartość zmiennej.  
  
 Można również ustawić wartość `Custom`. Jeśli wartość `Custom` wartości, należy także ustawić `customCertificateValidatorType` atrybutu zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć własnego niestandardowego modułu weryfikacji, musi dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi korzystającej z niestandardowego moduł weryfikacji certyfikatów](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod określa certyfikat X.509 i niestandardowy typ walidacji w `<authentication>` elementu.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
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
 [Porady: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
