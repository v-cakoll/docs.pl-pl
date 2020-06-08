---
title: <system.Net>, element (ustawienia sieci)
description: <system.Net> ustawień sieciowych zawiera ustawienia, które określają sposób, w jaki .NET Framework łączy się z opcjami sieci w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 9f18c7a3586948c03391d609f437e216a91bc27f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504488"
---
# <a name="systemnet-element-network-settings"></a>\<system.Net>, element (ustawienia sieci)
Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.  
  
[**\<configuration>**](../configuration-element.md)  
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
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[authenticationModules](authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań internetowych.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostem internetowym.|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).|  
|[mailSettings](mailsettings-element-network-settings.md)|Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).|  
|[requestCaching](requestcaching-element-network-settings.md)|Kontroluje mechanizm buforowania dla żądań sieci.|  
|[ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla klas w <xref:System.Net> i powiązanych podrzędnych obszarach nazw.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Określa moduły, które mają być używane do żądania informacji z hostów internetowych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[skonfigurować](../configuration-element.md)|Zawiera ustawienia dla wszystkich przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 [\<system.net>](system-net-element-network-settings.md)Element zawiera ustawienia dla klas z <xref:System.Net> i powiązane podrzędne przestrzenie nazw. Ustawienia Konfiguruj moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i moduły żądania internetowe, aby otrzymywać informacje z hostów internetowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia typową konfigurację używaną przez <xref:System.Net> klasy.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień sieci](index.md)
