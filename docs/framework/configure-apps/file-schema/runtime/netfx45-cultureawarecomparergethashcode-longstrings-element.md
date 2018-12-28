---
title: '&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c2dfd5d3944618cf94d32fac2708d6daef5a410
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613690"
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a>&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; — Element
Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczania kodów wartości skrótu dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.  
  
 \<Konfiguracja >  
\<runtime>  
< NetFx45_CultureAwareComparerGetHashCode_LongStrings >  
  
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
|0|Środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania kodów wartości skrótu. Domyślnie włączone.|  
|1|Środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania kodów wartości skrótu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody i <xref:System.ArgumentException> mogą być generowane, gdy metoda podejmuje próbę obliczenia kodu wartości skrótu bardzo dużych ciągów (za pośrednictwem kilka milionów znaków). Dodając ten element do pliku konfiguracji aplikacji i ustawienie jej `enabled` atrybut na wartość "1", można określić, że <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda używać alternatywnego algorytmu, który przydziela stałą ilość pamięci dla obliczania kodów wartości skrótu.  
  
> [!IMPORTANT]
>  `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Element nie jest używany w [!INCLUDE[win8](../../../../../includes/win8-md.md)] i nowszych wersjach.  
  
## <a name="see-also"></a>Zobacz też  
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
