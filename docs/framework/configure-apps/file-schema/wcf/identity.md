---
title: "&lt;tożsamości&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e583acee6309b6f8145cf8567cff12cea1c237e7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltidentitygt"></a>&lt;tożsamości&gt;
Element tożsamości pozwala deweloperowi klienta określić w czasie projektu oczekiwaną tożsamość usługi. W ramach procesu uzgadniania między klientem a usługą [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastruktury zapewnia, że odpowiada wartości tego elementu tożsamość oczekiwanej usługi i w związku z tym mogą być uwierzytelniane. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
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
|[\<custom>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|Określa program rozpoznawania nazw dla netPeerTcpBinding równorzędnej niestandardowej.|  
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
