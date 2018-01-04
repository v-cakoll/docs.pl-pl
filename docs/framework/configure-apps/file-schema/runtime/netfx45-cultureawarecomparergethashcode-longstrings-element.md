---
title: "&lt;Netfx45_cultureawarecomparergethashcode_longstrings —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c370bc9ea5f8c3cdbf8690c7e22788b1224f4df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a>&lt;Netfx45_cultureawarecomparergethashcode_longstrings —&gt; — Element
Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczania skrótu dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.  
  
 \<Konfiguracja >  
\<Runtime >  
< netfx45_cultureawarecomparergethashcode_longstrings — >  
  
## <a name="syntax"></a>Składnia  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci podczas obliczania kodów wartości skrótu.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|0|Środowisko uruchomieniowe języka wspólnego przydziela zmiennej ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania skrótu. Domyślnie włączone.|  
|1|Środowisko uruchomieniowe języka wspólnego przydziela stałej ilości pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania skrótu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie środowisko uruchomieniowe języka wspólnego przydziela zmiennej ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody i <xref:System.ArgumentException> może zostać wygenerowany, gdy metoda próbuje Oblicz wartość skrótu ciągów bardzo duże (za pośrednictwem kilku milionów znaków). Dodając ten element do pliku konfiguracji aplikacji i ustawienie jej `enabled` atrybutu "1", można określić, że <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> — metoda przy użyciu alternatywnego algorytmu, który przydziela stałej ilości pamięci dla obliczania skrótu.  
  
> [!IMPORTANT]
>  `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Element nie jest używany w [!INCLUDE[win8](../../../../../includes/win8-md.md)] i nowszych wersjach.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
