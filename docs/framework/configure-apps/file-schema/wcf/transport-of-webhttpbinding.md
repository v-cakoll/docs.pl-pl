---
title: '&lt;transport&gt; w &lt;webHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 385831b820de77006dffb6206c34baa8620ca5da
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a>&lt;transport&gt; w &lt;webHttpBinding&gt;
Definiuje ustawienia zabezpieczeń na poziomie transportu dla punktu końcowego skonfigurowanego do odbierania żądań HTTP.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<webHttpBinding>  
\<Powiązanie >  
\<security>  
\<transport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`clientCredentialType`|Określa poświadczenia używane do uwierzytelniania klienta do usługi. Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Określa poświadczenia używane do uwierzytelniania klienta na serwerze proxy domeny. Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Ciąg określający obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego. Wartość domyślna to ciąg pusty.<br /><br /> Obszar uwierzytelniania określa co najmniej nazwę hosta, który przeprowadza uwierzytelnianie. Można również określić zbiór użytkowników, które ma dostęp. Użytkownik może zapytania obszaru uwierzytelniania, aby upewnić się, co kilka możliwych nazwy użytkownika i hasła może służyć.|  
|`policyEnforcement`|To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.<br /><br /> 1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).<br />2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.<br />3.  Zawsze — zasady zawsze są wymuszane. Klienci, którzy nie obsługują ochrony rozszerzonej będzie mogło uwierzytelnić.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Zabezpieczenia są wyłączone.|  
|`Basic`|Korzysta z uwierzytelniania podstawowego.|  
|`Certificate`|Używa certyfikatów X.509 do uwierzytelniania klienta.|  
|`Digest`|Uwierzytelnianie szyfrowane używa.|  
|`Ntlm`|Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeny systemu Windows.|  
|`Windows`|Używa zintegrowanego uwierzytelniania systemu Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Zabezpieczenia są wyłączone.|  
|`Basic`|Korzysta z uwierzytelniania podstawowego.|  
|`Digest`|Uwierzytelnianie szyfrowane używa.|  
|`Ntlm`|Używa protokołu NTLM jako rezerwowe z domeny systemu Windows.|  
|`Windows`|Używa zintegrowanego uwierzytelniania systemu Windows.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
