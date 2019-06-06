---
title: <CompatSortNLSVersion>, element
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
ms.openlocfilehash: b426eaaa2dab4d54ea4c82483c079428f3bfac57
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689907"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion > Element
Określa, że środowisko uruchomieniowe ma używać starszych kolejności sortowania podczas porównywania ciągów.  
  
 \<Konfiguracja >  
\<runtime>  
\<CompatSortNLSVersion > Element  
  
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
|4096|Identyfikator ustawień regionalnych reprezentujący alternatywną kolejność sortowania. W tym przypadku 4096 reprezentuje kolejność sortowania programu .NET Framework 3.5 i wcześniejszymi wersjami.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ porównania ciągów, sortowanie i operacje dotyczące wielkości znaków wykonywane przez <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> klasy w .NET Framework 4 są zgodne ze standardem Unicode 5.1. wyniki metod porównujących takich jak <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> może różnić się od poprzednie wersje programu .NET Framework. Jeśli aplikacja jest zależna od starszego zachowania, można przywrócić porównywania ciągów i sortowania reguł używanych w .NET Framework 3.5 i starszych wersjach, umieszczając `<CompatSortNLSVersion>` elementu w pliku konfiguracyjnym aplikacji.  
  
> [!IMPORTANT]
>  Przywrócenie starszych reguł porównywania ciągów i sortowania powoduje też, że w systemie lokalnym musi być dostępna dołączana dynamicznie biblioteka sort00001000.dll.  
  
 Można również użyć reguł sortowania i porównywania ciągów starszej wersji w określonej domenie aplikacji, przekazując ciąg "NetFx40_Legacy20SortingBehavior", do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody tworzenia domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dwie <xref:System.String> obiektów i wywołuje <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody w celu porównania ich przy użyciu konwencji bieżącej kultury.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Po uruchomieniu tego przykładu w .NET Framework 4, wyświetla następujące dane wyjściowe.  
  
```  
sta follows a in the sort order.  
```  
  
 To różni się całkowicie z danych wyjściowych, który jest wyświetlany po uruchomieniu przykładu w .NET Framework 3.5.  
  
```  
sta equals a in the sort order.  
```  
  
 Jeśli jednak dodasz następujący plik konfiguracji do omawianego w przykładzie katalogu, a następnie uruchomisz przykład na .NET Framework 4, dane wyjściowe jest taka sama jak wytworzonego przez przykład, gdy jest on uruchamiany w .NET Framework 3.5.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
