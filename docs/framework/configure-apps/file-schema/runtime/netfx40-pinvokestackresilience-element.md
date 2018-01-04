---
title: "&lt;Netfx40_pinvokestackresilience —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17816ee6134dc6b3074256093c0cba07419baf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a>&lt;Netfx40_pinvokestackresilience —&gt; — Element
Określa, czy środowisko uruchomieniowe platformy niepoprawne wywołanie deklaracje w czasie wykonywania, kosztem wolniejsze przejścia między poprawki zarządzane automatycznie i kodu niezarządzanego.  
  
 \<Konfiguracja >  
\<Runtime >  
< netfx40_pinvokestackresilience — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe wykryje platformy niepoprawne wywołanie deklaracje i automatycznie naprawia stosu w czasie wykonywania na platformach 32-bitowych.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`0`|Środowisko wykonawcze używa interop szybsze, organizowanie architektura wprowadzone w systemie [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], które nie wykrywa i deklaracje wywołanie napraw niepoprawne platformy. Domyślnie włączone.|  
|`1`|Środowisko uruchomieniowe używa wolniejszej przejścia Wykryj i napraw niepoprawne platformy wywołania deklaracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element umożliwia handlu szybsze przekazywanie międzyoperacyjne dla odporności środowiska wykonawczego przed platformy niepoprawne wywołanie deklaracji.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], interop prostsze, organizowanie architektura zapewnia lepszą wydajność istotne dla przejść z kodu zarządzanego do kodu niezarządzanego. We wcześniejszych wersjach programu .NET Framework kierowania warstwy wykryto platformy niepoprawne wywołanie deklaracje na platformach 32-bitowych i automatycznie naprawić stosu. Nowa architektura kierowania eliminuje ten krok. W związku z tym przejścia są bardzo szybko, ale wywołanie niepoprawne platformy deklaracja może spowodować awarię programu.  
  
 Aby ułatwić wykrywanie nieprawidłowe deklaracje podczas tworzenia, udoskonalono Visual Studio debugowanie. [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) zarządzany Asystent debugowania (MDA) powiadamia o niepoprawne platformy deklaracji wywołania, gdy aplikacja jest uruchomiona w debugerze.  
  
 Adres różnych scenariuszy, w którym aplikacja używa składników, że nie można ponownie skompilować i że ma nieprawidłowe wywołanie platformy deklaracje, można użyć `NetFx40_PInvokeStackResilience` elementu. Dodawanie tego elementu do pliku konfiguracji aplikacji z `enabled="1"` zdecyduje się w trybie zgodności z zachowaniem wcześniejszych wersji programu .NET Framework, kosztem wolniejsze przejścia. Zestawy, które zostały skompilowane z wcześniejszych wersji programu .NET Framework są automatycznie wyłączony w tym trybie zgodności i nie wymagają tego elementu.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób do uczestnictwa w zwiększonej odporności przed niepoprawne wywołanie platformy deklaracje dla aplikacji, kosztem wolniejsze przejścia między zarządzanych i niezarządzanych kodu.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
