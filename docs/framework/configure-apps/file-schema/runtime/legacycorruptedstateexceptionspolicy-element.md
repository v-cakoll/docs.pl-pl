---
title: <legacyCorruptedStateExceptionsPolicy>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78b670d8b23b5ecf274432d3758d07dae34dcfcf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607174"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy> Element
Określa, czy środowisko uruchomieniowe języka wspólnego umożliwia kodu zarządzanego wykryć naruszenia zasad dostępu i inne wyjątki uszkodzony.  
  
 \<Konfiguracja >  
\<runtime>  
\<legacyCorruptedStateExceptionsPolicy>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, że aplikacja będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Aplikacja nie będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu. Domyślnie włączone.|  
|`true`|Aplikacja będzie przechwytywać uszkodzenia stan wyjątku awarie, takie jak naruszenia zasad dostępu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W .NET Framework w wersji 3.5 i starszych środowisko uruchomieniowe języka wspólnego mogą przechwytywać wyjątków, które zostały zgłoszone przez Państwa uszkodzony procesu kodu zarządzanego. Naruszenie zasad dostępu znajduje się przykład tego typu wyjątku.  
  
 Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], zarządzany kod nie jest już przechwytuje tego rodzaju wyjątków w `catch` bloków. Można jednak zastąpić tę zmianę i obsługa z obsługą wyjątków uszkodzony na dwa sposoby:  
  
- Ustaw `<legacyCorruptedStateExceptionsPolicy>` elementu `enabled` atrybutu `true`. To ustawienie konfiguracji jest zastosowany processwide i ma wpływ na wszystkie metody.  
  
 —lub—  
  
- Zastosuj <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atrybutu do metody, która zawiera wyjątki `catch` bloku.  
  
 Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że aplikacji należy powrócić do zachowania przed [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]i przechwytywać wszystkie błędny stan wyjątku błędów.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
