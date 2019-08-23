---
title: <transport> dla <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: ce8b2acb7d87b094958e20ca0b6cca9fc8266a8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911988"
---
# <a name="transport-of-ws2007httpbinding"></a>\<Transport > \<WS2007HttpBinding >
Definiuje ustawienia uwierzytelniania dla transportu HTTP.  
  
 \<system.serviceModel>  
\<> powiązań  
\<ws2007HttpBinding>  
\<> powiązania  
\<> zabezpieczeń  
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
|`clientCredentialType`|Określa poświadczenie używane do uwierzytelniania klienta w usłudze. Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny. Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego. Wartość domyślna to pusty ciąg.<br /><br /> Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie. Można również określić kolekcję użytkowników, którzy mają dostęp. Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby określić, która z kilku możliwych nazw użytkowników i haseł może być używana.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialtype — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Podstawowy|Używa uwierzytelniania podstawowego.|  
|Szyfrowane|Używa uwierzytelniania szyfrowanego.|  
|NTLM|Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.|  
|Windows|Używa zintegrowanego uwierzytelniania systemu Windows.|  
|Certyfikatu|Uwierzytelnia klienta za pomocą certyfikatów X. 509.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Podstawowy|Używa uwierzytelniania podstawowego.|  
|Szyfrowane|Używa uwierzytelniania szyfrowanego.|  
|NTLM|Używa protokołu NTLM jako rezerwy z domeną systemu Windows.|  
|Windows|Używa zintegrowanego uwierzytelniania systemu Windows.|  
|Certyfikatu|Uwierzytelnia klienta za pomocą certyfikatów X. 509.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zabezpieczeń](security-of-ws2007httpbinding.md)|Reprezentuje możliwości [ \<zabezpieczeń elementu > WS2007HttpBinding](ws2007httpbinding.md) .|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> powiązania](../../../misc/binding.md)
