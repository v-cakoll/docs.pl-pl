---
title: <module> — Element (Ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 4658af3f55bddb5f5a748db5366c53f1d2733983
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268201"
---
# <a name="module-element-network-settings"></a>\<Moduł >, Element (ustawienia sieci)
Dodaje nowy moduł serwera proxy aplikacji.  
  
 \<Konfiguracja >  
\<system.net>  
\<defaultProxy>  
\<module>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`type`|W pełni kwalifikowana nazwa typu (wskazywanym przez <xref:System.Type.FullName%2A> właściwości) i nazwy zestawu (wskazywanym przez <xref:System.Reflection.Assembly.FullName%2A> właściwości), oddzielone przecinkami, który implementuje serwera proxy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|Umożliwia skonfigurowanie serwera proxy protokołu HTTP (Hypertext Transfer).|  
  
## <a name="remarks"></a>Uwagi  
 `module` Element rejestruje klasy serwera proxy, które implementują <xref:System.Net.IWebProxy> interfejsu. Po zarejestrowaniu klasy proxy `module` może służyć do żądania informacji za pośrednictwem obsługiwanych serwera proxy.  
  
 Wartość `type` atrybut powinien mieć nazwę klasy, modułu i nazwą z jej odpowiednie dynamiczne łącze biblioteki (DLL).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje klasę niestandardowego serwera proxy.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
