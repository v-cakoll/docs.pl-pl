---
title: '&lt;system.Net&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f9098ce379cbaf12f589270729018da399f282b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemnetgt-element-network-settings"></a>&lt;system.Net&gt; elementu (ustawienia sieciowe)
Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.  
  
 \<Konfiguracja >  
\<system.net>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[authenticationModules —](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań Internet.|  
|[connectionmanagement —](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostów w Internecie.|  
|[defaultProxy —](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).|  
|[mailSettings](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).|  
|[requestCaching —](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Określa mechanizm buforowania żądań sieciowych.|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla klas w <xref:System.Net> i powiązanych podrzędne przestrzenie nazw.|  
|[webRequestModules —](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Określa moduły służące do żądania informacji z Internetu hostów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Konfiguracja](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Zawiera ustawienia dla wszystkich obszarów nazw.|  
  
## <a name="remarks"></a>Uwagi  
 [ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element zawiera ustawienia dla klas w <xref:System.Net> i powiązanych podrzędne przestrzenie nazw. Ustawienia skonfigurować moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i Internet modułów żądania odbierania informacji z Internetu hostów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono typowej konfiguracji używane przez <xref:System.Net> klasy.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
