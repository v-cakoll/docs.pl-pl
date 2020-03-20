---
title: <module>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154832"
---
# <a name="module-element-network-settings"></a>\<moduł> element (ustawienia sieciowe)
Dodaje nowy moduł serwera proxy do aplikacji.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>modułów**

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
|`type`|W pełni kwalifikowana nazwa typu <xref:System.Type.FullName%2A> (wskazana przez właściwość) <xref:System.Reflection.Assembly.FullName%2A> i nazwa zestawu (wskazana przez właściwość), oddzielona przecinkiem, która implementuje serwer proxy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Defaultproxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy Protokołu transferu hipertekstu (HTTP).|  
  
## <a name="remarks"></a>Uwagi  
 Element `module` rejestruje klasy proxy, <xref:System.Net.IWebProxy> które implementują interfejs. Po zarejestrowaniu klasy `module` proxy, może służyć do żądania informacji za pośrednictwem obsługiwanego serwera proxy.  
  
 Wartość atrybutu `type` powinna być nazwą klasy modułu i nazwą odpowiadającej mu biblioteki dynamicznego łącza (DLL).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje niestandardową klasę serwera proxy.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [Schemat ustawień sieci](index.md)
