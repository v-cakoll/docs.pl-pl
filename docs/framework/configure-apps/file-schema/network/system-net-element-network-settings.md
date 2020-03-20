---
title: <system.Net>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154559"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net element> (ustawienia sieciowe)
Zawiera ustawienia określające sposób łączenia się programu .NET Framework z siecią.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
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
|[authenticationModules](authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań internetowych.|  
|[connectionManagement (PołączenieManagement)](connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostem internetowym.|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy Protokołu transferu hipertekstu (HTTP).|  
|[mailSettings](mailsettings-element-network-settings.md)|Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).|  
|[requestCaching (Buforowanie)](requestcaching-element-network-settings.md)|Steruje mechanizmem buforowania żądań sieciowych.|  
|[ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieciowe dla klas w <xref:System.Net> powiązanych podrzędnych przestrzeniach nazw.|  
|[webRequestModules (WebRequestModules)](webrequestmodules-element-network-settings.md)|Określa moduły, za pomocą których mają być wymagane informacje od hostów internetowych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Konfiguracji](../configuration-element.md)|Zawiera ustawienia dla wszystkich obszarów nazw.|  
  
## <a name="remarks"></a>Uwagi  
 [ \<System.net>](system-net-element-network-settings.md) element zawiera ustawienia dla klas w <xref:System.Net> i powiązanych przestrzeni nazw podrzędnych. Ustawienia konfigurują moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i moduły żądań internetowych do odbierania informacji z hostów internetowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typową <xref:System.Net> konfigurację używaną przez klasy.  
  
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

- [Schemat ustawień sieci](index.md)
