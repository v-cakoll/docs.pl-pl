---
title: '&lt;TimeSpan_LegacyFormatMode&gt; — Element'
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
ms.openlocfilehash: e371f45286c88c9136b869e750009dadeb261877
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612260"
---
# <a name="lttimespanlegacyformatmodegt-element"></a>&lt;TimeSpan_LegacyFormatMode&gt; — Element
Określa, czy środowisko uruchomieniowe pozwala zachować starsze zachowanie w operacjach przy użyciu formatowania <xref:System.TimeSpan?displayProperty=nameWithType> wartości.  
  
 \<Konfiguracja >  
\<runtime>  
< TimeSpan_LegacyFormatMode >  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko wykonawcze używa starszego formatowania działania z <xref:System.TimeSpan?displayProperty=nameWithType> wartości.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko wykonawcze nie przywrócić starsze zachowanie formatowania.|  
|`true`|Środowisko uruchomieniowe przywraca starsze zachowanie formatowania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> struktury implementuje <xref:System.IFormattable> interfejsu i obsługuje formatowanie operacji za pomocą ciągów formatu standardowego i niestandardowego. Jeśli metoda analizowania napotka specyfikator nieobsługiwany format lub ciąg formatu, zgłasza <xref:System.FormatException>.  
  
 W poprzednich wersjach programu .NET Framework <xref:System.TimeSpan> struktury nie implementuje <xref:System.IFormattable> i nie obsługują ciągi formatu. Jednak wielu deweloperów przez pomyłkę przyjąć, że <xref:System.TimeSpan> obsługiwać zestaw ciągów formatu i używać ich w [operacji formatowania złożonego](../../../../../docs/standard/base-types/composite-formatting.md) za pomocą metod, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType>. Normalnie Jeśli typ implementuje <xref:System.IFormattable> i obsługuje formatowanie ciągów, wywołania do metod formatowania z nieobsługiwany format ciągów zazwyczaj generują <xref:System.FormatException>. Jednak ponieważ <xref:System.TimeSpan> nie zaimplementował <xref:System.IFormattable>, środowisko uruchomieniowe ignorowane w formacie ciągu i zamiast tego wywołuje <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metody. Oznacza to, że chociaż ciągi formatu nie miało wpływu na operacji formatowania, ich obecność nie powoduje <xref:System.FormatException>.  
  
 W przypadkach, w których starszego kodu przekazuje formatowania, metoda i nieprawidłowy ciąg formatu złożonego, a ten kod nie może być ponownie kompilowane, można użyć `<TimeSpan_LegacyFormatMode>` elementu do przywrócenia starszej wersji <xref:System.TimeSpan> zachowanie. Po ustawieniu `enabled` atrybutu tego elementu `true`, metoda powoduje wywołanie w celu formatowania złożonego <xref:System.TimeSpan.ToString?displayProperty=nameWithType> zamiast <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, a <xref:System.FormatException> nie jest zgłaszany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy wystąpienie <xref:System.TimeSpan> obiektu i próbuje sformatować je za pomocą <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metody przy użyciu nieobsługiwanego standardowym ciągiem formatującym.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Po uruchomieniu przykładu w [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] lub starszą wersję, wyświetla następujące dane wyjściowe:  
  
```  
12:30:45  
```  
  
 To znacznie różni się od dane wyjściowe po uruchomieniu przykładu w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] lub nowszej wersji:  
  
```  
Invalid Format  
```  
  
 Jednak jeśli dodasz następujący plik konfiguracji do przykładu katalogu, a następnie uruchom przykład na [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] lub nowszej wersji, dane wyjściowe jest taka sama jak wytworzonego przez w przykładzie, gdy jest uruchamiany na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
