---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 262ac9be6d5ce6466cf9aff33c0c2791c0e149dd
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988377"
---
# <a name="identity"></a>\<> tożsamości
Element Identity pozwala deweloperowi klienta określić w czasie projektowania oczekiwaną tożsamość usługi. W procesie uzgadniania między klientem a usługą infrastruktura Windows Communication Foundation (WCF) zapewni, że tożsamość oczekiwanej usługi jest zgodna z wartościami tego elementu i w ten sposób może być uwierzytelniona. Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<> klienta  
\<> punktu końcowego  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|certificate|Określa ustawienia certyfikatu X. 509. Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateElement>. Zawiera atrybut `encodedValue` , który jest ciągiem, który określa wartość zakodowaną przez ten certyfikat.|  
|certificateReference|Określa ustawienia dla walidacji certyfikatu X. 509. Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Określa serwer DNS certyfikatu X. 509 używany do uwierzytelniania usługi. Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą tożsamość.|  
|rsa|Określa wartość pola RSA certyfikatu X. 509 używanego do uwierzytelniania usługi dla klienta. Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą tożsamość|  
|servicePrincipalName|Określa tożsamość głównej nazwy serwera (SPN), która jest główną nazwą używaną przez klienta do unikatowego identyfikowania wystąpienia usługi. Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą nazwę główną. Ten element jest typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Określa tożsamość głównej nazwy użytkownika (UPN), która jest typem nazwy logowania użytkownika w sieci. Główna nazwa użytkownika składa się z nazwy obiektu użytkownika używanej w Active Directory, a po niej symbol (\@), a następnie zazwyczaj domena nadrzędna systemu nazw domen. Na przykład Jan w drzewie domeny Fabrikam.com może mieć główną nazwę [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)użytkownika.  Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą nazwę główną. Ten element jest typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> niestandardowe](custom.md)|Określa niestandardowy program rozpoznawania elementów równorzędnych dla netPeerTcpBinding.|  
|[\<> punktu końcowego](endpoint-element.md)|Konfiguruje punkty końcowe usługi.|  
|[\<> punktu końcowego \<> klienta](endpoint-of-client.md)|Konfiguruje punkty końcowe kanału.|  
|[\<> wystawcy](issuer.md)|Określa usługę tokenu zabezpieczającego (STS) dla usługi federacyjnej.|  
|[\<issuerMetadata>](issuermetadata.md)|Określa punkt końcowy metadanych usługi federacyjnej (Security Token Service).|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Definiuje parametry wystawionego tokenu w niestandardowym powiązaniu.|  
|[\<localIssuer >](localissuer.md)|Określa usługę lokalnego tokenu zabezpieczającego (STS).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [Uwierzytelnianie i tożsamość usług](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Punktów końcowych Adresy, powiązania i kontrakty](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
