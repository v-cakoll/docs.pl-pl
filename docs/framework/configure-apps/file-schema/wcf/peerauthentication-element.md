---
title: <peerAuthentication>, element
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 09094c00b8faa28c37e202112251fee7cb4580be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934017"
---
# <a name="peerauthentication-element"></a>\<peerAuthentication, element >
Określa opcje uwierzytelniania dla klientów równorzędnych.  
  
 Aby uzyskać więcej informacji na temat programowania peer-to-peer, zobacz [sieci peer-to-](../../../wcf/feature-details/peer-to-peer-networking.md)peer.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
\<clientCredentials>  
\<> elementów równorzędnych  
\<PeerAuthentication>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Opcjonalny ciąg. Typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiony, `certificateValidationMode` gdy jest ustawiony `Custom`na.|  
|`certificateValidationMode`|Opcjonalne Wyliczenie. Określa jeden z trzech trybów używanych do walidacji poświadczeń. Jeśli jest ustawiona `Custom`na, należy `customCertificateValidator` również podać wartość. Wartość domyślna to `ChainTrust`.|  
|`revocationMode`|Opcjonalne Wyliczenie. Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL). Wartość domyślna to `Online`.|  
|`trustedStoreLocation`|Opcjonalne Wyliczenie. Jedna z dwóch lokalizacji magazynu systemowego: `LocalMachine` lub `CurrentUser`. Ta wartość jest używana podczas negocjowania certyfikatu usługi z klientem. Sprawdzanie poprawności jest wykonywane względem magazynu **osób zaufanych** w określonej lokalizacji magazynu. Wartość domyślna to `CurrentUser`.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|String|Określa nazwę typu i zestaw oraz inne dane używane do znajdowania typu. Minimalna nazwa przestrzeni nazw i typ są wymagane. Informacje opcjonalne obejmują: nazwę zestawu, numer wersji, kulturę i token klucza publicznego.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedna z następujących wartości: `None`, `PeerTrust`, `ChainTrust` `PeerOrChainTrust`,, `Custom`. Wartość domyślna to `ChainTrust`.<br /><br /> Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>Atrybut odwołania  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedna z następujących wartości: `NoCheck`, `Online`, `Offline`. Wartość domyślna to `Online`.<br /><br /> Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Wyliczenie|Jedna z następujących wartości: `LocalMachine` lub. `CurrentUser` Wartość domyślna to `CurrentUser`. Jeśli aplikacja kliencka jest uruchomiona na koncie systemowym, zwykle `LocalMachine`jest to certyfikat. Jeśli aplikacja kliencka jest uruchomiona w ramach konta użytkownika, certyfikat zazwyczaj znajduje się w `CurrentUser`temacie.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> elementów równorzędnych](peer-of-clientcredentials-element.md)|Określa poświadczenie używane do uwierzytelniania klienta w usłudze równorzędnej.|  
  
## <a name="remarks"></a>Uwagi  
 Element odnosi się do <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy. `<authentication>` Ten element określa moduł sprawdzania poprawności, który jest wywoływany podczas uwierzytelniania sąsiada-sąsiada w sieci. Gdy nowy element równorzędny podejmie próbę nawiązania połączenia sąsiada, przekazuje własne poświadczenie do elementu równorzędnego odpowiadającego. Moduł sprawdzania poprawności jest wywoływany w celu zweryfikowania poświadczeń strony zdalnej. Za każdym razem, gdy połączenie równorzędne jest nawiązane w sieci, oba elementy równorzędne są uwierzytelniane wzajemnie, co oznacza, że są wywoływane walidacje na obu końcach.  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustawia tryb `PeerOrChainTrust`walidacji certyfikatu.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
- [Sieci równorzędne](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpieczanie aplikacji kanałów równorzędnych](../../../wcf/feature-details/securing-peer-channel-applications.md)
