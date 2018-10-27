---
title: '&lt;Tożsamość&gt;'
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 74c88df867efa82d48693a3df86b4c7813c40eba
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047049"
---
# <a name="ltidentitygt"></a>&lt;Tożsamość&gt;
Element tożsamości pozwala deweloperowi klienta określić w czasie projektu oczekiwaną tożsamość usługi. W procesu uzgadniania między klientem a usługą infrastruktury usług Windows Communication Foundation (WCF) gwarantuje, że tożsamość pasuje do oczekiwanej usługi wartości tego elementu i dlatego może zostać uwierzytelniony. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<Klient >  
\<punkt końcowy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<identity>  
    <certificate encodedValue="String"/>  
    <certificateReference findValue="String"   
       isChainIncluded="Boolean"  
       storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
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
|certificate|Określa ustawienia certyfikatu X.509. Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateElement>. Zawiera ona atrybut `encodedValue` oznacza to ciąg, który określa wartość zakodowany przez ten certyfikat.|  
|certificateReference|Określa ustawienia dla walidacji certyfikatu X.509. Ten element jest typu <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Określa certyfikat X.509 używany do uwierzytelniania usługi DNS. Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistej tożsamości.|  
|rsa|Określa wartość pola RSA certyfikat X.509 używany do uwierzytelniania usługi do klienta. Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistej tożsamości|  
|servicePrincipalName|Określa tożsamość główna nazwa (usługi SPN) serwera, jest to nazwa podmiotu zabezpieczeń używany przez klienta do jednoznacznego identyfikowania wystąpienia usługi. Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistą nazwę podmiotu zabezpieczeń. Ten element jest typu <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Określa tożsamość głównej nazwy (UPN) użytkownika, który jest typem nazwa logowania użytkownika w sieci. Główna nazwa użytkownika, który składa się z nazwą obiektu użytkownika, które są używane w usłudze Active Directory, a następnie na symbol (\@) i następnie zazwyczaj domeny nadrzędnej systemu nazw domen. Na przykład, Niewykluczone, główna nazwa użytkownika Jeff w drzewie domeny Fabrikam.com [ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com).  Ten element zawiera atrybut `value` jest ciągiem i zawiera rzeczywistą nazwę podmiotu zabezpieczeń. Ten element jest typu <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<niestandardowe >](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Określa niestandardowe elementu równorzędnego programu rozpoznawania nazw dla netPeerTcpBinding.|  
|[\<punkt końcowy >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)|Służy do konfigurowania różnych typów punktów końcowych.|  
|[\<Wystawca >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|Określa Usługa tokenu zabezpieczającego (STS) dla usługi federacyjnej.|  
|[\<issuerMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|Określa punkt końcowy metadanych dla Usługa tokenu zabezpieczającego (STS) z usługi federacyjnej.|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Definiuje parametry dla wystawiony token do niestandardowego powiązania.|  
|[\<localIssuer >](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|Określa lokalnym usługa tokenu zabezpieczającego (STS).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Punkty końcowe: adresy, powiązania i kontrakty](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
