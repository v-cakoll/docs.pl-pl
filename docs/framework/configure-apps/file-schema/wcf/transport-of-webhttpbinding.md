---
title: <transport> dla <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732789"
---
# <a name="transport-of-webhttpbinding"></a>\<transport> dla \<webHttpBinding>
Definiuje ustawienia zabezpieczeń na poziomie transportu dla punktu końcowego usługi skonfigurowanego do odbierania żądań HTTP.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`clientCredentialType`|Określa poświadczenie używane do uwierzytelniania klienta w usłudze. Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType> .|  
|`proxyCredentialType`|Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny. Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType> .|  
|`realm`|Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego. Wartość domyślna to pusty ciąg.<br /><br /> Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie. Można również określić kolekcję użytkowników, którzy mają dostęp. Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.|  
|`policyEnforcement`|To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.<br /><br /> 1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).<br />2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.<br />3. zawsze — zasady są zawsze wymuszane. Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialtype — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Zabezpieczenia są wyłączone.|  
|`Basic`|Używa uwierzytelniania podstawowego.|  
|`Certificate`|Uwierzytelnia klienta za pomocą certyfikatów X. 509.|  
|`Digest`|Używa uwierzytelniania szyfrowanego.|  
|`Ntlm`|Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.|  
|`Windows`|Używa zintegrowanego uwierzytelniania systemu Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`None`|Zabezpieczenia są wyłączone.|  
|`Basic`|Używa uwierzytelniania podstawowego.|  
|`Digest`|Używa uwierzytelniania szyfrowanego.|  
|`Ntlm`|Używa protokołu NTLM jako rezerwy z domeną systemu Windows.|  
|`Windows`|Używa zintegrowanego uwierzytelniania systemu Windows.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|Reprezentuje możliwości zabezpieczeń [\<wsHttpBinding>](wshttpbinding.md) elementu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../wcf/feature-details/wcf-web-http-programming-model.md)
