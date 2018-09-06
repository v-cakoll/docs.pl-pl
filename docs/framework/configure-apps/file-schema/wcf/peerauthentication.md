---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: bb83d2badad609394a66246fc14c19a6602399e0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799190"
---
# <a name="ltpeerauthenticationgt"></a>&lt;peerAuthentication&gt;
Określa ustawienia uwierzytelniania dla elementów równorzędnych certyfikat używany przez węzeł równorzędny.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<elementu równorzędnego >  
\<peerAuthentication>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`certificateValidationMode`|Opcjonalne wyliczenie. Określa jeden z trzech trybów używanych do walidacji poświadczenia. Ten atrybut jest typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` musi również zostać dostarczony.|  
|`customCertificateValidatorType`|Opcjonalny ciąg. Określa typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiane podczas `certificateValidationMode` ustawiono `Custom`. Ten atrybut jest typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>. Windows Communication Foundation (WCF) zapewnia elementu równorzędnego domyślny moduł weryfikacji certyfikatów samodzielną sprawdzającą równorzędnej certyfikatu w magazynie zaufanych osób. Sprawdza także, że łączy się łańcuchem Certyfikat prawidłowy główny. Możesz zaimplementować niestandardowego modułu weryfikacji, aby określić różne zachowania i użyj tego atrybutu, aby wskazywał niestandardowego modułu weryfikacji.|  
|`revocationMode`|Opcjonalne wyliczenie. Określa tryb odwołania certyfikatu. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. System sprawdza certyfikat elementu równorzędnego nie został odwołany wyszukiwanie w listę odwołanych certyfikatów. Można wykonać ten test, sprawdzając w trybie online lub względem listę odwołanych pamięci podręcznej. Sprawdzanie odwołań może być wyłączona przez ustawienie tego atrybutu na NoCheck.|  
|`trustedStoreLocation`|Opcjonalne wyliczenie. Określa lokalizację magazynu zaufanych, gdzie certyfikat równorzędnej zostanie zweryfikowany przez system zabezpieczeń programu WCF. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<elementu równorzędnego >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Określa bieżące poświadczenia dla węzła równorzędnego.|  
  
## <a name="remarks"></a>Uwagi  
 `<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy. Ten element Określa moduł weryfikacji, który jest wywoływany podczas uwierzytelniania sąsiada sąsiada w siatce. Próba nawiązania połączenia sąsiada przez nowego elementu równorzędnego przekazuje swoje własne poświadczenia dla elementu równorzędnego działa prawidłowo. Modułu sprawdzania poprawności obiektu odpowiadającego jest wywoływana, aby zweryfikować poświadczenia zdalnego innych firm. Zawsze, gdy nawiązaniu połączenia równorzędnego w siatce, zarówno komputery są wzajemnie uwierzytelnione, znaczenie modułów sprawdzania poprawności na obu końcach są wywoływane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Sieci równorzędne](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Uwierzytelnianie wiadomości z kanału równorzędnego](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Kanał elementu równorzędnego uwierzytelniania niestandardowego](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
