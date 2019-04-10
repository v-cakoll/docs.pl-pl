---
title: <NetFx40_PInvokeStackResilience> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725bd715f6e70dff08929e58d588a3d8561d5011
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224237"
---
# <a name="netfx40pinvokestackresilience-element"></a>\<NetFx40_PInvokeStackResilience> Element
Określa, czy środowisko wykonawcze automatycznie poprawki nieprawidłowa platforma wywołania deklaracje w czasie wykonywania, kosztem wolniejsze przejścia między zarządzane, a kod niezarządzany.  
  
 \<Konfiguracja >  
\<runtime>  
<NetFx40_PInvokeStackResilience>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe wykryje nieprawidłowa platforma wywołuje deklaracje i automatycznie naprawia stosu w czasie wykonywania na platformach 32-bitowych.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`0`|Środowisko wykonawcze używa szybciej międzyoperacyjnego marshaling architektury wprowadzona w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], który nie może wykryć, i wywołanie platformy niepoprawne poprawki deklaracji. Domyślnie włączone.|  
|`1`|Przejść wolniejsze używa środowiska uruchomieniowego, Wykryj i napraw nieprawidłowe platformy, które wywołuje deklaracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element pozwala na szybsze marshaling międzyoperacyjny dla odporności na błędy czasu wykonywania względem platformy nieprawidłowe wywołanie deklaracji.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], usprawnione współdziałania, organizowanie architektura zapewnia zwiększenie wydajności istotne dla przejścia z kodu zarządzanego do kodu niezarządzanego. We wcześniejszych wersjach programu .NET Framework organizowania warstwy wykrył nieprawidłowe wywołania deklaracje na platformach 32-bitowych i platformy automatycznie naprawić stosu. Nowa architektura organizowania eliminuje ten krok. W wyniku przejścia są bardzo szybko, ale platforma nieprawidłowe wywołanie deklaracji może spowodować awarię programu.  
  
 Aby ułatwić wykrywanie nieprawidłowe deklaracje podczas tworzenia środowiska debugowania programu Visual Studio została ulepszona. [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) zarządzanego Asystenta debugowania (MDA) powiadamia o niepoprawne platformy deklaracji wywołania, gdy aplikacja jest uruchomiona w debugerze.  
  
 Dla których aplikacja używa składników, że nie można ponownie skompilować i że ma nieprawidłowe wywołanie platformy deklaracji, można użyć scenariuszy `NetFx40_PInvokeStackResilience` elementu. Dodanie tego elementu do pliku konfiguracyjnego aplikacji za pomocą `enabled="1"` zdecyduje się w trybie zgodności z zachowaniem wcześniejszych wersjach programu .NET Framework, kosztem wolniejsze przejścia. Zestawy, które zostały skompilowane dla wcześniejszych wersji programu .NET Framework są automatycznie wyłączony w tym trybie zgodności, a ten element nie jest konieczne.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak skorzystać z większą odporność względem niepoprawne deklaracje dla aplikacji, kosztem wolniejsze przejścia między wywołania platformy kodu zarządzanego i niezarządzanego.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
