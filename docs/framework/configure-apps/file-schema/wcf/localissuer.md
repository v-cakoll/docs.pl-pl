---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8836d9e57dd7c4d9cfdc20c5e4856e384e6d67b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalissuergt"></a>&lt;localIssuer&gt;
Określa adres i powiązanie wystawcy lokalnego używanego do uzyskania tokenu zabezpieczającego.  
  
 \<System. ServiceModel >  
\<zachowania >  
sekcja endpointBehaviors  
\<zachowanie >  
\<clientCredentials >  
\<issuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|adres|Wymagany ciąg. Określa identyfikator URI wystawcy lokalnego.|  
|powiązanie|Opcjonalny ciąg. Jedno z powiązań dostarczane przez system. Aby uzyskać listę, zobacz [powiązania System-Provided](../../../../../docs/framework/wcf/system-provided-bindings.md).|  
|bindingConfiguration|Opcjonalny ciąg. Określa konfigurację powiązania w pliku konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<tożsamość >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Określa informacje o tożsamości wystawcy lokalnego.|  
|[\<nagłówki >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Kolekcja nagłówków adresowych, które są wymagane do prawidłowego adresowania wystawcy lokalnego. Można użyć `add` — słowo kluczowe, aby dodać nagłówek do tej kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|Określa niestandardowy token używany do uwierzytelniania klienta do usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas uzyskiwania wystawionego tokenu z zabezpieczeń tokenu usługi (STS), aplikacja klienta musi być skonfigurowana z adres i powiązanie na potrzeby komunikacji z STS. Gdy <xref:System.ServiceModel.WSFederationHttpBinding> nie dostarcza adres URL usługi tokenu zabezpieczeń, lub gdy adres wystawcy wiązania federacyjnego jest http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous lub `null`, klienta [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] kanał używane wartości określone przez `address` i `binding` do komunikacji z STS uzyskanie wystawionego tokenu. Aby uzyskać więcej informacji na temat konfigurowania wystawcy lokalnego, zobacz [porady: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `address`, `binding`, i `bindingConfiguration` atrybuty `localIssuer` elementu.  
  
```xml  
<system.serviceModel>  
 <behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <issuedToken cacheIssuedTokens="false"   
                 defaultKeyEntropyMode="ClientEntropy">  
     <localIssuer address="net.tcp://cohowinery/tokens"   
                  binding="netTcpBinding"  
                  bindingConfiguration="myTcpBindingConfig" />  
    </issuedToken>  
   </clientCredentials>  
  </behavior>  
  </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Porady: Konfigurowanie lokalnego wystawcy](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [Uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)  
 [Porady: Tworzenie klienta federacyjnego](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Federacja i wystawione tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
