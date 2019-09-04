---
title: <developmentMode>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0253c3ced52b575097fe5d18abb8ce188c0164fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252695"
---
# <a name="developmentmode-element"></a>\<Element > developmentmode
Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> developmentmode**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**developerInstallation**|Określa, czy środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**true**|Wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.|  
|**false**|Nie wyszukuje zestawów w katalogach określonych przez zmienną środowiskową DEVPATH. Jest to wartość domyślna|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Tego ustawienia należy używać tylko w czasie projektowania. Środowisko uruchomieniowe nie sprawdza wersji w zestawach o silnej nazwie znalezionych w DEVPATH. Po prostu używa pierwszego zestawu, który znajdzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH](../../how-to-locate-assemblies-by-using-devpath.md)
