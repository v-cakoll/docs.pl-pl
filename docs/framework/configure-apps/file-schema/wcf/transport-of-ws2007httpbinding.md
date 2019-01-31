---
title: <transport> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: b8f84d0ed6c6248e72e3353675c9da96a0678ae6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273309"
---
# <a name="transport-of-ws2007httpbinding"></a>\<transport > z \<ws2007HttpBinding >
Definiuje ustawienia uwierzytelniania dla protokołu HTTP.  
  
 \<system.serviceModel>  
\<powiązania >  
\<ws2007HttpBinding>  
\<Powiązanie >  
\<security>  
\<transport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
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
|`realm`|Obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego. Wartość domyślna to ciąg pusty.<br /><br /> Obszar uwierzytelniania co najmniej Określa nazwę hosta, który przeprowadza uwierzytelnianie. Można również określić zbiór użytkowników, którzy mają dostęp. Użytkownika można badać obszaru uwierzytelniania, aby określić jedną z kilku możliwych nazw użytkowników i haseł może służyć.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Podstawowy|Korzysta z uwierzytelniania podstawowego.|  
|Podsumowanie|Uwierzytelnianie szyfrowane używa.|  
|Ntlm|Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeną systemu Windows.|  
|Windows|Używa zintegrowanego uwierzytelniania Windows.|  
|Certyfikat|Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Podstawowy|Korzysta z uwierzytelniania podstawowego.|  
|Podsumowanie|Uwierzytelnianie szyfrowane używa.|  
|Ntlm|Wykorzystuje NTLM jako rezerwowe z domeną systemu Windows.|  
|Windows|Używa zintegrowanego uwierzytelniania Windows.|  
|Certyfikat|Przy użyciu certyfikatów X.509 do uwierzytelniania klienta.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Reprezentuje możliwości zabezpieczeń [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
