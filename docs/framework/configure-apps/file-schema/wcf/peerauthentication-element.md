---
title: '&lt;peerAuthentication&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3cc625f5fdb20505f2e36c5a2d37fca0676bbb37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeerauthenticationgt-element"></a>&lt;peerAuthentication&gt;, element
Określa opcje uwierzytelniania dla klientów peer-to-peer.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]Zobacz programowania, peer-to-peer [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 \<System. ServiceModel >  
\<zachowania >  
\<endpointBehaviors >  
\<zachowanie >  
\<clientCredentials >  
\<peer >  
\<PeerAuthentication >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Opcjonalny ciąg. Typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiane podczas `certificateValidationMode` ma ustawioną wartość `Custom`.|  
|`certifcateValidationMode`|Opcjonalne wyliczenie. Określa jeden z trzech trybów używanych do walidacji poświadczenia. Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` należy dostarczyć także. Wartość domyślna to `ChainTrust`.|  
|`revocationMode`|Opcjonalne wyliczenie. Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL). Wartość domyślna to `Online`.|  
|`trustedStoreLocation`|Opcjonalne wyliczenie. Jeden z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`. Ta wartość jest używana, gdy negocjowane jest certyfikat usługi do klienta. Sprawdzanie poprawności jest wykonywane przed **zaufane osoby** są przechowywane w lokalizacji określonej magazynu. Wartość domyślna to `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Określa nazwę typu i zestawu i innych danych można znaleźć typu. Co najmniej nazwę przestrzeni nazw i typ są wymagane. Zawiera dodatkowe informacje: Nazwa zestawu, numer wersji, kultury i tokenu klucza publicznego.|  
  
## <a name="certificatevalidationmode-attribute"></a>tryb certificateValidationMode atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`. Wartość domyślna to `ChainTrust`.<br /><br /> Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`. Wartość domyślna to `Online`.<br /><br /> Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`. Wartość domyślna to `CurrentUser`. Jeśli aplikacja kliencka jest uruchomiona na koncie systemu, a następnie certyfikat jest zwykle w obszarze `LocalMachine`. Jeśli aplikacja kliencka jest uruchomiona na koncie użytkownika, a następnie certyfikat jest zwykle w `CurrentUser`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<peer >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Określa poświadczenie używane w celu uwierzytelniania klienta usługi elementu równorzędnego.|  
  
## <a name="remarks"></a>Uwagi  
 `<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy. Ten element Określa moduł weryfikacji, który jest wywoływany podczas uwierzytelniania sąsiada sąsiada w siatce. Próba nawiązania połączenia z elementem sąsiednim przez nowego elementu równorzędnego przekazaniem własną poświadczeń do nieodpowiadający węzłem równorzędnym. Moduł sprawdzania poprawności obiektu odpowiadającego jest wywoływane w celu Sprawdź poświadczenia strona zdalna. Zawsze, gdy jest nawiązywane połączenie elementu równorzędnego w sieci, zarówno komputery są wzajemnie uwierzytelnione, znaczenie modułów sprawdzania poprawności po obu stronach są wywoływane.  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustawia tryb walidacji certyfikatu `PeerOrChainTrust`.  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
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
