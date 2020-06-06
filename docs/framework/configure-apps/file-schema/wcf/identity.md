---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 15c9e38a141fc294c47863b1a932711444ac079a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855152"
---
# \<identity>
Element Identity pozwala deweloperowi klienta określić w czasie projektowania oczekiwaną tożsamość usługi. W procesie uzgadniania między klientem a usługą infrastruktura Windows Communication Foundation (WCF) zapewni, że tożsamość oczekiwanej usługi jest zgodna z wartościami tego elementu i w ten sposób może być uwierzytelniona. Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
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
|certyfikat|Określa ustawienia certyfikatu X. 509. Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateElement> . Zawiera atrybut `encodedValue` , który jest ciągiem, który określa wartość zakodowaną przez ten certyfikat.|  
|certificateReference|Określa ustawienia dla walidacji certyfikatu X. 509. Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .|  
|dns|Określa serwer DNS certyfikatu X. 509 używany do uwierzytelniania usługi. Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą tożsamość.|  
|rsa|Określa wartość pola RSA certyfikatu X. 509 używanego do uwierzytelniania usługi dla klienta. Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą tożsamość|  
|servicePrincipalName|Określa tożsamość głównej nazwy serwera (SPN), która jest główną nazwą używaną przez klienta do unikatowego identyfikowania wystąpienia usługi. Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą nazwę główną. Ten element jest typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> .|  
|userPrincipalName|Określa tożsamość głównej nazwy użytkownika (UPN), która jest typem nazwy logowania użytkownika w sieci. Główna nazwa użytkownika składa się z nazwy obiektu użytkownika używanej w Active Directory, a po niej symbol ( \@ ), a następnie zazwyczaj domena nadrzędna systemu nazw domen. Na przykład Jan w drzewie domeny Fabrikam.com może mieć główną nazwę użytkownika [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .  Ten element zawiera atrybut `value` , który jest ciągiem i zawiera rzeczywistą nazwę główną. Ten element jest typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<custom>](custom.md)|Określa niestandardowy program rozpoznawania elementów równorzędnych dla netPeerTcpBinding.|  
|[\<endpoint>](endpoint-element.md)|Konfiguruje punkty końcowe usługi.|  
|[\<endpoint>z\<client>](endpoint-of-client.md)|Konfiguruje punkty końcowe kanału.|  
|[\<issuer>](issuer.md)|Określa usługę tokenu zabezpieczającego (STS) dla usługi federacyjnej.|  
|[\<issuerMetadata>](issuermetadata.md)|Określa punkt końcowy metadanych usługi federacyjnej (Security Token Service).|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Definiuje parametry wystawionego tokenu w niestandardowym powiązaniu.|  
|[\<localIssuer>](localissuer.md)|Określa usługę lokalnego tokenu zabezpieczającego (STS).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [Uwierzytelnianie i tożsamość usług](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Punkty końcowe: Adresy, powiązania i kontrakty](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
