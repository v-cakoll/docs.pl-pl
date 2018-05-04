---
title: '&lt;Tożsamości&gt;'
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 9cfd1d6cc7c278fd7e95c13df0a6f801cfabbc33
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltidentitygt"></a>&lt;Tożsamości&gt;
Element tożsamości pozwala deweloperowi klienta określić w czasie projektu oczekiwaną tożsamość usługi. W procesie uzgadniania między klientem a usługą infrastruktury usług Windows Communication Foundation (WCF) sprawdzi, czy tożsamość pasuje do oczekiwanej usługi wartości tego elementu i w związku z tym mogą być uwierzytelniane. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<Klient >  
\<punkt końcowy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"storeName="  
       storeLocation="LocalMachine/CurrentUser"  
       X509FindType= Enumeration./>  
    <dns value="String"/>  
    <rsa value="String"/>  
    <servicePrincipalName value="String"/>  
    <usePrincipalName value="String"/>  
</identity>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|certificate|Określa ustawienia certyfikatu X.509. Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateElement>. Zawiera ona atrybut `encodedValue` oznacza to ciąg, który określa wartość kodowane przez ten certyfikat.|  
|certificateReference|Określa ustawienia dla walidacji certyfikatu X.509. Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Określa certyfikat X.509 używany do uwierzytelniania usługi DNS. Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistej tożsamości.|  
|rsa|Określa wartość pola RSA certyfikat X.509 używany do uwierzytelniania usługi na kliencie. Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistej tożsamości|  
|servicePrincipalName|Określa tożsamość głównej nazwy (usługi SPN) serwera, który jest nazwa główna używana przez klienta do unikatowej identyfikacji wystąpienia usługi. Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistą nazwą podmiotu zabezpieczeń. Ten element jest typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Określa tożsamość głównej nazwy (UPN) użytkownika, który jest typem nazwa logowania użytkownika w sieci. Główna nazwa użytkownika zawiera nazwę obiektu użytkownika używane w usłudze Active Directory, a następnie na symbolu (@) i następnie zazwyczaj domeny nadrzędnej systemu nazw domen. Na przykład Jan w drzewie domeny Fabrikam.com może być nazwa główna użytkownika [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistą nazwą podmiotu zabezpieczeń. Ten element jest typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<niestandardowe >](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Określa program rozpoznawania nazw dla netPeerTcpBinding równorzędnej niestandardowej.|  
|[\<punkt końcowy >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)|Umożliwia skonfigurowanie różnych typów punktów końcowych.|  
|[\<Wystawca >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Określa zabezpieczeń tokenu usługi (STS) dla usługi federacyjnej.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Określa punktu końcowego metadanych dla zabezpieczeń tokenu usługi (STS) usługi federacyjnej.|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Definiuje parametry dla wystawionego tokenu do niestandardowego powiązania.|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Określa lokalne zabezpieczenia tokenu usługi (STS).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Punkty końcowe: adresy, powiązania i kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
