---
title: '&lt;Gccpugroup —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4461667bdb47d410c857b4ac2c9dd268438a02f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltgccpugroupgt-element"></a>&lt;Gccpugroup —&gt; — Element
Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.  
  
 \<Konfiguracja >  
\<runtime>  
\<GCCpuGroup>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesorów. Domyślnie włączone.|  
|`true`|Wyrzucanie elementów bezużytecznych obsługuje wiele grup Procesora, jeśli włączono odzyskiwanie pamięci na serwerze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy komputer ma wiele grup procesora CPU i odzyskiwanie pamięci na serwerze jest włączone (zobacz [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora CPU i pobiera wszystkie rdzenie do konto podczas tworzenia i równoważenie stosów.  
  
> [!NOTE]
>  Ten element dotyczy tylko pamięci kolekcji wątków. Aby włączyć środowisko uruchomieniowe do dystrybucji użytkownika wątki we wszystkich grupach Procesora, należy również włączyć [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób włączania wyrzucanie elementów bezużytecznych do wielu grup procesorów.  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Porady: wyłączanie współbieżne odzyskiwanie pamięci](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [Wyrzucanie elementów bezużytecznych stacji roboczej i serwera](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
