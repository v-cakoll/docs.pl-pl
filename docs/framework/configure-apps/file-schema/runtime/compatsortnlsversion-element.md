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
ms.openlocfilehash: 575d44ad9ecf445ba5d4b7fbe47032127ccb33ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252731"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion, element >
Określa, że środowisko uruchomieniowe ma używać starszych kolejności sortowania podczas porównywania ciągów.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<CompatSortNLSVersion>**  
  
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
|4096|Identyfikator ustawień regionalnych reprezentujący alternatywną kolejność sortowania. W tym przypadku 4096 reprezentuje porządek sortowania .NET Framework 3,5 i starszych wersji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ operacje porównywania ciągów, sortowania i wielkości liter wykonywane przez <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> klasę w .NET Framework 4 są zgodne ze standardem Unicode 5,1, wyniki metod porównywania ciągów, takie jak <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> mogą się różnić od poprzednie wersje .NET Framework. Jeśli aplikacja jest zależna od zachowania starszej wersji, można przywrócić porównanie ciągów i reguły sortowania używane w .NET Framework 3,5 i wcześniejszych wersjach przez dołączenie `<CompatSortNLSVersion>` elementu w pliku konfiguracyjnym aplikacji.  
  
> [!IMPORTANT]
> Przywrócenie starszych reguł porównywania ciągów i sortowania powoduje też, że w systemie lokalnym musi być dostępna dołączana dynamicznie biblioteka sort00001000.dll.  
  
 Można również użyć starszych reguł sortowania i porównywania ciągów w określonej domenie aplikacji, przekazując ciąg "NetFx40_Legacy20SortingBehavior" do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody podczas tworzenia domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy wystąpienie dwóch <xref:System.String> obiektów i <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> wywołuje metodę w celu porównania ich przy użyciu Konwencji bieżącej kultury.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Po uruchomieniu przykładu na .NET Framework 4 zostanie wyświetlone następujące dane wyjściowe.  
  
```  
sta follows a in the sort order.  
```  
  
 Jest to zupełnie inne niż dane wyjściowe, które są wyświetlane po uruchomieniu przykładu na .NET Framework 3,5.  
  
```  
sta equals a in the sort order.  
```  
  
 Jeśli jednak dodasz następujący plik konfiguracji do katalogu przykładu, a następnie uruchomisz przykład na .NET Framework 4, dane wyjściowe są identyczne z tym, które zostały utworzone przez przykład w przypadku uruchomienia na .NET Framework 3,5.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
