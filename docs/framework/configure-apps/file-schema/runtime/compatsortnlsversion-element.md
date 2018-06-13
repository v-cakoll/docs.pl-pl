---
title: '&lt;Compatsortnlsversion —&gt; — Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e78106c4df2e1c414d00f18871566dd5906c54f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745711"
---
# <a name="ltcompatsortnlsversiongt-element"></a>&lt;Compatsortnlsversion —&gt; — Element
Określa, że środowisko uruchomieniowe ma używać starszych kolejności sortowania podczas porównywania ciągów.  
  
 \<Konfiguracja >  
\<runtime>  
\<Compatsortnlsversion — > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa identyfikator ustawień regionalnych, które będą określać używaną kolejność sortowania.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|4096|Identyfikator ustawień regionalnych reprezentujący alternatywną kolejność sortowania. W takim przypadku 4096 reprezentuje kolejność sortowania [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] i starszych wersji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ porównania ciągów, sortowanie i wielkości liter operacje wykonywane przez <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> klasy w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] są zgodne z Unicode 5.1 standardowe, wyniki metod porównania ciągów, takich jak <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> może różnić się od poprzednie wersje programu .NET Framework. Jeśli aplikacja jest zależna od starsze zachowanie, można przywrócić porównania ciągów i reguł sortowania używane w [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] i wcześniejsze wersje, umieszczając w niej `<CompatSortNLSVersion>` elementu w pliku konfiguracyjnym aplikacji.  
  
> [!IMPORTANT]
>  Przywrócenie starszych reguł porównywania ciągów i sortowania powoduje też, że w systemie lokalnym musi być dostępna dołączana dynamicznie biblioteka sort00001000.dll.  
  
 Umożliwia także reguły sortowania i porównywania ciągów starszej wersji w określonej domenie aplikacji przez przekazanie ciąg "NetFx40_Legacy20SortingBehavior" do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody podczas tworzenia domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwa <xref:System.String> obiektów i wywołania <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodę, aby porównać je przy użyciu konwencji bieżącej kultury.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Po uruchomieniu przykładzie [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], wyświetla następujące dane wyjściowe.  
  
```  
sta follows a in the sort order.  
```  
  
 To jest całkowicie różni się od wynik wyświetlony po uruchomieniu przykładzie na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```  
sta equals a in the sort order.  
```  
  
 Jednak jeśli dodasz następującego pliku konfiguracji, na przykład do katalogu, a następnie uruchom przykładzie w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], dane wyjściowe są takie same jak wytworzonego na przykładzie, gdy jest uruchamiany na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
