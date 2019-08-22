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
ms.openlocfilehash: 449146612938700f59f5e2ec761526d1dc66a3fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663957"
---
# <a name="systemnet-element-network-settings"></a>\<System .net >, element (Ustawienia sieci)
Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.  
  
 \<> konfiguracji  
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
|[authenticationModules](authenticationmodules-element-network-settings.md)|Określa moduły używane do uwierzytelniania żądań internetowych.|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostem internetowym.|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).|  
|[mailSettings](mailsettings-element-network-settings.md)|Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).|  
|[requestCaching](requestcaching-element-network-settings.md)|Kontroluje mechanizm buforowania dla żądań sieci.|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla klas w <xref:System.Net> i powiązanych podrzędnych obszarach nazw.|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Określa moduły, które mają być używane do żądania informacji z hostów internetowych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[skonfigurować](../configuration-element.md)|Zawiera ustawienia dla wszystkich przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:System.Net> [ ElementSystem.net>zawieraustawieniadlaklaswi\<](system-net-element-network-settings.md) powiązanych podrzędnych obszarach nazw. Ustawienia Konfiguruj moduły uwierzytelniania, zarządzanie połączeniami, ustawienia poczty, serwer proxy i moduły żądania internetowe, aby otrzymywać informacje z hostów internetowych.  
  
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
