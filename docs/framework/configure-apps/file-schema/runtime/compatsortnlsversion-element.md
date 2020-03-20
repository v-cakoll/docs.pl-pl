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
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154273"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion> Element
Określa, że środowisko uruchomieniowe ma używać starszych kolejności sortowania podczas porównywania ciągów.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>**  
  
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
|4096|Identyfikator ustawień regionalnych reprezentujący alternatywną kolejność sortowania. W takim przypadku 4096 reprezentuje kolejność sortowania .NET Framework 3.5 i wcześniejszych wersji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ operacje porównywania ciągów, sortowania <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> i wielkości liter wykonywane przez klasę w programie .NET Framework 4 są zgodne <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> ze <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> standardem Unicode 5.1, wyniki metod porównywania ciągów, takich jak i mogą różnić się od poprzednich wersji programu .NET Framework. Jeśli aplikacja zależy od starszego zachowania, można przywrócić reguły porównywania ciągów i sortowania używane w `<CompatSortNLSVersion>` programie .NET Framework 3.5 i wcześniejszych wersjach, dołączając element w pliku konfiguracyjnym aplikacji.  
  
> [!IMPORTANT]
> Przywrócenie starszych reguł porównywania ciągów i sortowania powoduje też, że w systemie lokalnym musi być dostępna dołączana dynamicznie biblioteka sort00001000.dll.  
  
 Można również użyć starszych reguł sortowania i porównywania ciągów w określonej domenie aplikacji, przekazując ciąg "NetFx40_Legacy20SortingBehavior" do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody podczas tworzenia domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.String> twoniuniu <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> wywołuje dwa obiekty i wywołuje metodę, aby porównać je przy użyciu konwencji bieżącej kultury.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Po uruchomieniu przykładu na .NET Framework 4, wyświetla następujące dane wyjściowe:
  
```console
sta follows a in the sort order.  
```  
  
 Jest to całkowicie różni się od danych wyjściowych, który jest wyświetlany po uruchomieniu przykładu na .NET Framework 3.5:
  
```console
sta equals a in the sort order.  
```  
  
 Jeśli jednak dodasz następujący plik konfiguracyjny do przykładowego katalogu, a następnie uruchomisz przykład w programie .NET Framework 4, dane wyjściowe są identyczne z daneem wytwarzanym przez przykład, gdy jest uruchamiany w programie .NET Framework 3.5.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
