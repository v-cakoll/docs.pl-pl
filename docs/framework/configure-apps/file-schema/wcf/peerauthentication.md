---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd18acaf76b2d5ccceb12b62398357b0b1655cb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeerauthenticationgt"></a>&lt;peerAuthentication&gt;
Określa ustawienia uwierzytelniania dla elementu równorzędnego certyfikat używany przez węzeł równorzędny.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceCredentials >  
\<peer >  
\<peerAuthentication >  
  
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
|`certificateValidationMode`|Opcjonalne wyliczenie. Określa jeden z trzech trybów używanych do walidacji poświadczenia. Ten atrybut jest typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` należy dostarczyć także.|  
|`customCertificateValidatorType`|Opcjonalny ciąg. Określa typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiane podczas `certificateValidationMode` ma ustawioną wartość `Custom`. Ten atrybut jest typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]udostępnia element równorzędny domyślny moduł weryfikacji certyfikatów, która sprawdza równorzędnej certyfikatu w magazynie zaufanych osób. Sprawdza także, że certyfikat powiązany prawidłowy katalog główny. Można zaimplementować niestandardowego modułu weryfikacji, aby określić różne zachowania i wskaż niestandardowego modułu weryfikacji za pomocą tego atrybutu.|  
|`revocationMode`|Opcjonalne wyliczenie. Określa tryb odwołania certyfikatu. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. System sprawdza, czy certyfikatu elementu równorzędnego nie został odwołany przez wyszukiwanie z listy odwołania certyfikatów. Tego wyboru można przeprowadzić sprawdzania w trybie online lub z listą odwołania pamięci podręcznej. Sprawdzanie odwołania można wyłączyć, ustawiając tego atrybutu na NoCheck.|  
|`trustedStoreLocation`|Opcjonalne wyliczenie. Określa lokalizację magazynu zaufanych, gdy certyfikat elementu równorzędnego jest zweryfikowany przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zabezpieczeń systemu. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<peer >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Określa bieżące poświadczenia dla węzła równorzędnego.|  
  
## <a name="remarks"></a>Uwagi  
 `<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy. Ten element Określa moduł weryfikacji, który jest wywoływany podczas uwierzytelniania sąsiada sąsiada w siatce. Próba nawiązania połączenia z elementem sąsiednim przez nowego elementu równorzędnego przekazaniem własną poświadczeń do nieodpowiadający węzłem równorzędnym. Moduł sprawdzania poprawności obiektu odpowiadającego jest wywoływane w celu Sprawdź poświadczenia strona zdalna. Zawsze, gdy jest nawiązywane połączenie elementu równorzędnego w sieci, zarówno komputery są wzajemnie uwierzytelnione, znaczenie modułów sprawdzania poprawności po obu stronach są wywoływane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Sieci peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Uwierzytelnianie wiadomości kanału równorzędnego](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Niestandardowe uwierzytelnianie kanału równorzędnego](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Zabezpieczanie aplikacji kanałów równorzędnych](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
