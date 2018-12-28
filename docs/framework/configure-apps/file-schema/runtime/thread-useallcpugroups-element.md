---
title: '&lt;Thread_UseAllCpuGroups&gt; — Element'
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a3984d594d0739d4b8f2b7b165aab434e10ab80
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611012"
---
# <a name="ltthreaduseallcpugroupsgt-element"></a>&lt;Thread_UseAllCpuGroups&gt; — Element
Określa, czy środowisko uruchomieniowe rozprowadza wątki zarządzane we wszystkich grupach CPU.  
  
 \<Konfiguracja >  
\<runtime>  
< Thread_UseAllCpuGroups >  
  
## <a name="syntax"></a>Składnia  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe rozprowadza wątki zarządzane we wszystkich grupach CPU.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko uruchomieniowe nie rozkłada zarządzanych wątków w obrębie wielu grup CPU. Domyślnie włączone.|  
|`true`|Środowisko uruchomieniowe rozprowadza wątki zarządzane WE wiele grup CPU, jeśli komputer ma wiele grup CPU i [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element jest włączony.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Kiedy komputer posiada wiele grup CPU, włączenie tego elementu powoduje dystrybucję zarządzanych wątków we wszystkich grupach CPU środowisko uruchomieniowe. Aby użyć tej funkcji, należy również włączyć [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, który rozszerza wyrzucania elementów bezużytecznych na wszystkich grupach CPU i uwzględnia wszystkich rdzeni podczas tworzenia i równoważenie stosów. Włączanie [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element wymaga Włączanie [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elementu. Jeśli te elementy nie są włączone, umożliwiając `<Thread_UseAllCpuGroups>` element nie ma wpływu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [\<Gccpugroup — > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
