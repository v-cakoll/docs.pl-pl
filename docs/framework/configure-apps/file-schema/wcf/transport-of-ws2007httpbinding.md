---
title: '&lt;transport&gt; w &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 3be9d4e64e63b32156cb64257f5bed8230cee3aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350950"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a>&lt;transport&gt; w &lt;ws2007HttpBinding&gt;
Definiuje ustawienia uwierzytelniania dla transportu HTTP.  
  
 \<system.serviceModel>  
\<powiązania >  
\<ws2007HttpBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
\<transport>  
  
## <a name="syntax"></a>Składnia  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
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
|`realm`|Obszar uwierzytelniania dla uwierzytelniania podstawowego lub szyfrowanego. Wartość domyślna to ciąg pusty.<br /><br /> Obszar uwierzytelniania określa co najmniej nazwę hosta, który przeprowadza uwierzytelnianie. Można również określić zbiór użytkowników, którzy mają dostęp. Użytkownik może zapytania obszaru uwierzytelniania, aby określić jedną z kilku możliwych nazwy użytkowników i hasła może służyć.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Podstawowy|Korzysta z uwierzytelniania podstawowego.|  
|Skrót|Uwierzytelnianie szyfrowane używa.|  
|Uwierzytelnianie NTLM|Korzysta z uwierzytelniania NTLM, jako rezerwowe z domeny systemu Windows.|  
|Windows|Używa zintegrowanego uwierzytelniania systemu Windows.|  
|certyfikat|Używa certyfikatów X.509 do uwierzytelniania klienta.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|Brak|Zabezpieczenia są wyłączone.|  
|Podstawowy|Korzysta z uwierzytelniania podstawowego.|  
|Skrót|Uwierzytelnianie szyfrowane używa.|  
|Uwierzytelnianie NTLM|Używa protokołu NTLM jako rezerwowe z domeny systemu Windows.|  
|Windows|Używa zintegrowanego uwierzytelniania systemu Windows.|  
|certyfikat|Używa certyfikatów X.509 do uwierzytelniania klienta.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Reprezentuje możliwości zabezpieczeń [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
