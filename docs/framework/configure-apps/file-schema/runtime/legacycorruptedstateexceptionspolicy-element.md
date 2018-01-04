---
title: "&lt;legacycorruptedstateexceptionspolicy —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f09d6cf256e072d01f3cfc79987aa4d240f96235
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a>&lt;legacycorruptedstateexceptionspolicy —&gt; — Element
Określa, czy środowisko uruchomieniowe języka wspólnego umożliwia kodu zarządzanego do wychwytywania naruszenia zasad dostępu i innych wyjątków uszkodzony.  
  
 \<Konfiguracja >  
\<Runtime >  
\<legacycorruptedstateexceptionspolicy — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, że aplikacja będzie przechwytywać uszkodzenia stanu wyjątek błędów, np. naruszenia zasad dostępu.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Aplikacja nie będzie przechwytywać uszkodzenia stanu wyjątek błędów, np. naruszenia zasad dostępu. Domyślnie włączone.|  
|`true`|Aplikacja będzie przechwytywać uszkodzenia stanu wyjątek błędów, np. naruszenia zasad dostępu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W programie .NET Framework w wersji 3.5 lub starszym środowisko uruchomieniowe języka wspólnego dozwolone kodu zarządzanego przechwytują wyjątki, które zostały zgłoszone przez Państwa uszkodzony procesu. Przykładem tego typu wyjątku jest naruszenia zasad dostępu.  
  
 Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]zarządzanego kodu nie przechwytuje tych typów wyjątków w `catch` bloków. Można jednak zastąpić tę zmianę i obsługa obsługi wyjątków uszkodzony na dwa sposoby:  
  
-   Ustaw `<legacyCorruptedStateExceptionsPolicy>` elementu `enabled` atrybutu `true`. To ustawienie konfiguracji jest stosowane processwide i ma wpływ na wszystkie metody.  
  
 —lub—  
  
-   Zastosuj <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atrybut do metody, która zawiera wyłączenia `catch` bloku.  
  
 Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określić, że aplikacja powinna przywrócić zachowanie przed [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]i catch błędny wszystkie błędy wyjątek stanu.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
