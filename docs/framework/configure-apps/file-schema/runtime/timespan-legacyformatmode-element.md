---
title: '&lt;Timespan_legacyformatmode —&gt; — Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0faf2876680ef5ec3fc7373cae9f81eb091f47a1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753973"
---
# <a name="lttimespanlegacyformatmodegt-element"></a>&lt;Timespan_legacyformatmode —&gt; — Element
Określa, czy środowisko uruchomieniowe zachowuje starsze zachowanie w formatowaniu operacje z <xref:System.TimeSpan?displayProperty=nameWithType> wartości.  
  
 \<Konfiguracja >  
\<runtime>  
< timespan_legacyformatmode — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe używa starszej wersji formatowania zachowanie w przypadku <xref:System.TimeSpan?displayProperty=nameWithType> wartości.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko uruchomieniowe nie powoduje przywrócenia starszej wersji działanie formatowania.|  
|`true`|Środowisko uruchomieniowe przywraca starsze zachowanie formatowania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> struktury implementuje <xref:System.IFormattable> interfejsu i obsługuje formatowanie operacje z ciągami formatu standardowych i niestandardowych. Jeśli metodę analizowania napotka nieobsługiwany format specyfikator lub ciąg formatu, zgłasza <xref:System.FormatException>.  
  
 W poprzednich wersjach programu .NET Framework <xref:System.TimeSpan> struktury nie implementuje interfejsu <xref:System.IFormattable> i nie obsługuje ciągi formatów. Jednak wielu deweloperów przez pomyłkę założono, że <xref:System.TimeSpan> obsługiwać zestaw ciągi formatów i używać ich w [złożone formatowanie operacji](../../../../../docs/standard/base-types/composite-formatting.md) z metod, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Zwykle gdy typ implementuje <xref:System.IFormattable> i obsługuje formatowanie ciągów i wywołania metod formatowania o nieobsługiwanym formacie ciągi zazwyczaj throw <xref:System.FormatException>. Jednak ponieważ <xref:System.TimeSpan> nie implementuje interfejsu <xref:System.IFormattable>, środowisko uruchomieniowe ignorowane ciąg formatu i zamiast tego wywołać <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metody. Oznacza to, że chociaż ciągi formatu nie miała wpływu na operację formatowania, ich obecność nie spowodowało <xref:System.FormatException>.  
  
 W przypadkach, w których starszego kodu przekazuje złożone formatowanie — metoda i niepoprawnym ciągiem formatu i nie może być ponownie kompilowane kodu, można użyć `<TimeSpan_LegacyFormatMode>` element, aby przywrócić starszego <xref:System.TimeSpan> zachowanie. Podczas ustawiania `enabled` atrybutu tego elementu, aby `true`, złożone formatowanie wyników metod w wywołaniu <xref:System.TimeSpan.ToString?displayProperty=nameWithType> zamiast <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, a <xref:System.FormatException> nie jest generowany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.TimeSpan> obiektu i próbuje sformatować go przy użyciu <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metody przy użyciu ciągu nieobsługiwany format standardowa.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Po uruchomieniu przykładzie [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] lub we wcześniejszej wersji, wyświetla następujące dane wyjściowe:  
  
```  
12:30:45  
```  
  
 To znacznie różni się od dane wyjściowe po uruchomieniu przykładzie na [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] lub nowszej wersji:  
  
```  
Invalid Format  
```  
  
 Jednak jeśli dodasz następującego pliku konfiguracji, na przykład do katalogu, a następnie uruchom przykładzie w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] lub nowszej wersji, dane wyjściowe są identyczne z utworzonego przez w przykładzie, gdy jest uruchamiany na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
