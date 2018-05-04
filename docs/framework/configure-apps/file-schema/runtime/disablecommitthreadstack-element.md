---
title: '&lt;disablecommitthreadstack —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d8724d16a25cdec040fa5b1f5472da06b11f669
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdisablecommitthreadstackgt-element"></a>&lt;disablecommitthreadstack —&gt; — Element
Określa, czy po uruchomieniu wątku zatwierdzone stosu wątku pełna.  
  
 \<Konfiguracja >  
\<runtime>  
\<disablecommitthreadstack — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|włączone|Atrybut wymagany.<br /><br /> Określa, czy zatwierdzania stosu wątku pełne podczas uruchamiania wątku (domyślnie) jest wyłączona.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Nie należy wyłączać domyślne zachowanie środowiska CLR, czyli zatwierdzić stosu wątku pełne po uruchomieniu wątku.|  
|1|Wyłącz domyślne zachowanie środowiska CLR, czyli zatwierdzić stosu wątku pełne po uruchomieniu wątku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracyjnym używane przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie środowiska CLR jest zatwierdzić stosu wątku pełne po uruchomieniu wątku. Jeśli należy utworzyć dużej liczby wątków na serwerze, która ma ograniczoną pamięci, a większość tych wątków użyje bardzo mało miejsca na stosie, serwer może działać lepiej środowisko uruchomieniowe języka wspólnego nie zadeklarować stosu wątku pełne natychmiast, gdy wątek jest st arted.  
  
> [!NOTE]
>  Niezarządzane hostów można użyć `STARTUP_DISABLE_COMMITTHREADSTACK` Flaga uruchamiania w [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczeniu, aby osiągnąć ten sam rezultat.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można wyłączyć domyślnego zachowania środowiska CLR, czyli zatwierdzić stosu wątku pełne podczas uruchamiania wątku.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
