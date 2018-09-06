---
title: '&lt;transport&gt; w &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 771866a83d54ca9e4fc7f3ed6d351b4a6c755b4c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733225"
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a>&lt;transport&gt; w &lt;wsHttpBinding&gt;
Definiuje ustawienia uwierzytelniania dla protokołu HTTP.  
  
 \<system.serviceModel>  
\<powiązania >  
\<wsHttpBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
\<transport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`clientCredentialType`|Określa poświadczenia używane do uwierzytelniania klienta do usługi. Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Określa poświadczenia używane do uwierzytelniania klienta do domeny serwera proxy. Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Ciąg, który określa obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego. Wartość domyślna to ciąg pusty.<br /><br /> Obszar uwierzytelniania co najmniej Określa nazwę hosta, który przeprowadza uwierzytelnianie. Można również określić zbiór użytkowników, które ma dostęp. Użytkownika można badać obszaru uwierzytelniania, aby upewnić się, co kilka możliwych nazw użytkowników i haseł może służyć.|  
|`policyEnforcement`|To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.<br /><br /> 1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrony rozszerzonej jest wyłączone).<br />2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.<br />3.  Zawsze — zasady zawsze są wymuszane. Klienci, którzy nie obsługują ochrony rozszerzonej zakończy się niepowodzeniem do uwierzytelniania.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Zabezpieczenia są wyłączone.|  
|`Basic`|Korzysta z uwierzytelniania podstawowego.|  
|`Digest`|Uwierzytelnianie szyfrowane używa.|  
|`Ntlm`|Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeną systemu Windows.|  
|`Windows`|Używa zintegrowanego uwierzytelniania Windows.|  
|`Certificate`|Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Zabezpieczenia są wyłączone.|  
|`Basic`|Korzysta z uwierzytelniania podstawowego.|  
|`Digest`|Uwierzytelnianie szyfrowane używa.|  
|`Ntlm`|Wykorzystuje NTLM jako rezerwowe z domeną systemu Windows.|  
|`Windows`|Używa zintegrowanego uwierzytelniania Windows.|  
|`Certificate`|Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Reprezentuje możliwości zabezpieczeń [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
