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
ms.openlocfilehash: 851a63b41dfb5d3b4058e1373148f48d47d9d6ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664066"
---
# <a name="module-element-network-settings"></a>\<module > element (Ustawienia sieci)
Dodaje nowy moduł proxy do aplikacji.  
  
 \<> konfiguracji  
\<system.net>  
\<defaultProxy>  
\<> modułu  
  
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
|`type`|W pełni kwalifikowana nazwa typu (wskazywana przez <xref:System.Type.FullName%2A> Właściwość) i nazwa zestawu (wskazywanym <xref:System.Reflection.Assembly.FullName%2A> przez właściwość) oddzielone przecinkami, które implementują serwer proxy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Konfiguruje serwer proxy protokołu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="remarks"></a>Uwagi  
 Element rejestruje klasy proxy, które <xref:System.Net.IWebProxy> implementują interfejs. `module` Po zarejestrowaniu klasy `module` proxy może służyć do żądania informacji za pomocą obsługiwanego serwera proxy.  
  
 Wartość `type` atrybutu powinna być nazwą klasy modułu i nazwą odpowiadającą jej biblioteką dołączaną dynamicznie (dll).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje niestandardową klasę proxy.  
  
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
- [Schemat ustawień sieci](index.md)
