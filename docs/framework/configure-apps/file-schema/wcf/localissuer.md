---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397864"
---
# \<localIssuer>
Określa adres i powiązanie wystawcy lokalnego używanego do uzyskania tokenu zabezpieczającego.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
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
|[\<identity>](identity.md)|Określa informacje o tożsamości dla wystawcy lokalnego.|  
|[\<headers>](headers-element.md)|Kolekcja nagłówków adresów, które są wymagane w celu prawidłowego adresowania wystawcy lokalnego. Możesz użyć `add` słowa kluczowego, aby dodać nagłówek do tej kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|Określa niestandardowy token używany do uwierzytelniania klienta w usłudze.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku uzyskiwania wystawionego tokenu z usługi tokenu zabezpieczającego (STS), aplikacja kliencka musi być skonfigurowana przy użyciu adresu i powiązania, które ma być używane do komunikacji z usługą STS. Jeśli nie <xref:System.ServiceModel.WSFederationHttpBinding> podasz adresu URL usługi tokenu zabezpieczającego lub gdy adres wystawcy powiązania federacyjnego to `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` lub `null` , kanał Windows Communication Foundation (WCF) klienta używa wartości określonych przez `address` i `binding` do komunikacji z usługą STS w celu uzyskania wystawionego tokenu. Aby uzyskać więcej informacji na temat konfigurowania wystawcy lokalnego, zobacz [How to: Configure a Local wystawca](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie ustawiono `address` atrybuty, `binding` , i `bindingConfiguration` `localIssuer` elementu.  
  
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
- [Instrukcje: tworzenie klienta federacyjnego](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Federacja i wystawione tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
