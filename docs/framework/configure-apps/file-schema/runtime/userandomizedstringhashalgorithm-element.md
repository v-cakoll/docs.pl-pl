---
title: "&lt;Userandomizedstringhashalgorithm —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7cd561cf0e0a9e080b150bdaa412686126423c91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a>&lt;Userandomizedstringhashalgorithm —&gt; — Element
Określa, czy środowisko uruchomieniowe języka wspólnego oblicza skrótu dla ciągów na poszczególnych domen aplikacji.  
  
 \<Konfiguracja >  
\<Runtime >  
\<Userandomizedstringhashalgorithm — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy skrótu dla ciągów są obliczane na podstawie domen aplikacji.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`0`|Środowisko uruchomieniowe języka wspólnego nie obliczeniowe skrótu dla ciągów na poszczególnych domen aplikacji; jeden algorytm służy do obliczania skrótu ciągu. Domyślnie włączone.|  
|`1`|Środowisko uruchomieniowe języka wspólnego oblicza skrótu dla ciągów na poszczególnych domen aplikacji. Identycznych ciągów w różnych domenach aplikacji i w różnych procesów będzie miał inną skrótu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.StringComparer> klasy i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metody użyć pojedynczego algorytmu wyznaczania wartości skrótu, tworzącego spójne skrótu w domenach aplikacji. Jest to równoważne ustawienie `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu `0`. Jest to algorytmu wyznaczania wartości skrótu używany w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 <xref:System.StringComparer> Klasy i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metody można również użyć innego algorytmu wyznaczania wartości skrótu, który oblicza skrótu na poszczególnych domen aplikacji. W związku z tym skrótu dla ciągów równoważne różnią się między domenami aplikacji. Jest to funkcji opcjonalnych; Aby móc korzystać z niego, należy ustawić `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu `1`.  
  
 Operacja O(1) jest zwykle wyszukiwania ciągu w tablicy skrótów. Jednak w przypadku wystąpienia dużej liczby kolizji wyszukiwania może stać się O (n<sup>2</sup>) operacji. Można użyć `<UseRandomizedStringHashAlgorithm>` element konfiguracji do generowania losowego algorytmu wyznaczania wartości skrótu dla domeny aplikacji, co z kolei ogranicza liczbę potencjalnych konfliktów, szczególnie w przypadku, gdy klucze, z których mają być obliczane kodów skrótów są oparte na danych wejściowych przez użytkowników.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `DisplayString` klasy, który obejmuje stałą typu string prywatne, `s`, którego wartość wynosi "Jest ciągiem". Zawiera także `ShowStringHashCode` metodę, która wyświetla wartość ciągu i jego skrótu wraz z nazwą domeny aplikacji, w którym jest wykonywany metody.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Po uruchomieniu przykładzie bez podawania plik konfiguracji, wyświetla dane wyjściowe podobne do następującego. Należy zauważyć, że skrótu ciągu identyczne w domenach dwóch aplikacji.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Jednak jeśli dodać następującego pliku konfiguracji do katalogu w tym przykładzie, a następnie uruchomić przykład, kodów skrótów dla tych samych parametrach różnią się według domeny aplikacji.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Gdy plik konfiguracji jest obecny, w przykładzie przedstawiono następujące dane wyjściowe:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
