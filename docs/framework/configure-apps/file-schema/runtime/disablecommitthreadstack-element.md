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
ms.openlocfilehash: 69b2c9f3bbd4fb7562272903d3ab78e3a4312298
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611649"
---
# <a name="ltdisablecommitthreadstackgt-element"></a>&lt;disablecommitthreadstack —&gt; — Element
Określa, czy stos pełnego wątku jest zatwierdzona, gdy wątek jest uruchomiony.  
  
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
|Włączone|Atrybut wymagany.<br /><br /> Określa, czy zatwierdzenie stos pełnego wątku podczas uruchamiania wątku (zachowanie domyślne) jest wyłączona.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Nie należy wyłączać domyślne zachowanie środowiska CLR, czyli aby zatwierdzić stos pełnego wątku, gdy wątek jest uruchomiony.|  
|1|Wyłączyć zachowanie domyślne środowisko uruchomieniowe języka wspólnego, czyli aby zatwierdzić stos pełnego wątku, gdy wątek jest uruchomiony.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używane przez środowisko uruchomieniowe języka wspólnego i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikacji.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślne zachowanie środowiska uruchomieniowego języka wspólnego jest zatwierdzenie stos pełnego wątku, gdy wątek jest uruchomiony. Jeśli duża liczba wątków musi zostać utworzona na serwerze, który ma ograniczoną pamięć, a większość te wątki użyje bardzo mało miejsca na stosie, serwer może działać lepiej natychmiast, gdy wątek jest st, środowisko uruchomieniowe języka wspólnego nie zatwierdzić stos pełnego wątku chomiona.  
  
> [!NOTE]
>  Można użyć niezarządzane hosty `STARTUP_DISABLE_COMMITTHREADSTACK` Flaga uruchamiania [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczeniu, aby osiągnąć ten sam wynik.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wyłączyć zachowanie domyślne środowisko uruchomieniowe języka wspólnego, czyli aby zatwierdzić stos pełnego wątku podczas uruchamiania wątku.  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
