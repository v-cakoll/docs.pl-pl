---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931738"
---
# <a name="localissuer"></a>\<localIssuer >
Określa adres i powiązanie wystawcy lokalnego używanego do uzyskania tokenu zabezpieczającego.  
  
 \<system.ServiceModel>  
\<> zachowań  
Sekcja endpointBehaviors  
\<> zachowania  
\<clientCredentials>  
\<issuedToken >  
\<localIssuer >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|adres|Wymagany ciąg. Określa identyfikator URI wystawcy lokalnego.|  
|powiązanie|Opcjonalny ciąg. Jedno z powiązań dostarczonych przez system. Aby uzyskać listę, zobacz [powiązania dostarczone przez system](../../../wcf/system-provided-bindings.md).|  
|bindingConfiguration|Opcjonalny ciąg. Określa konfigurację powiązania znalezioną w pliku konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> tożsamości](identity.md)|Określa informacje o tożsamości dla wystawcy lokalnego.|  
|[\<nagłówki >](headers-element.md)|Kolekcja nagłówków adresów, które są wymagane w celu prawidłowego adresowania wystawcy lokalnego. Możesz użyć słowa kluczowego, `add` aby dodać nagłówek do tej kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedToken >](issuedtoken.md)|Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku uzyskiwania wystawionego tokenu z usługi tokenu zabezpieczającego (STS), aplikacja kliencka musi być skonfigurowana przy użyciu adresu i powiązania, które ma być używane do komunikacji z usługą STS. Gdy program `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null`nie poda adresu URL usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego to lub, kanał Windows Communication Foundation (WCF) klienta używa wartości określonych przez <xref:System.ServiceModel.WSFederationHttpBinding> `address` i`binding` aby komunikować się z usługą STS w celu uzyskania wystawionego tokenu. Aby uzyskać więcej informacji na temat konfigurowania wystawcy [lokalnego, zobacz How to: Konfigurowanie lokalnego wystawcy](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Przykład  
 W `address`poniższym przykładzie ustawiono atrybuty, `binding` `bindingConfiguration` , i `localIssuer` elementu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Instrukcje: Konfigurowanie lokalnego wystawcy](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Uwierzytelnianie i tożsamość usług](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Federacja i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Zabezpieczanie klientów](../../../wcf/securing-clients.md)
- [Instrukcje: Tworzenie klienta federacyjnego](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Federacja i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
