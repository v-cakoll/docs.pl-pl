---
title: '&lt;Userandomizedstringhashalgorithm —&gt; — Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bb4286ea6055d2df9111b2222b137f2668bfdfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681043"
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a>&lt;Userandomizedstringhashalgorithm —&gt; — Element
Określa, czy środowisko uruchomieniowe języka wspólnego oblicza kody skrótów dla ciągów na podstawie domeny aplikacji.  
  
 \<Konfiguracja >  
\<runtime>  
\<UseRandomizedStringHashAlgorithm>  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy kody skrótów dla ciągów są obliczane na podstawie domeny aplikacji.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`0`|Środowisko uruchomieniowe języka wspólnego nie może obliczyć kodów skrótu dla ciągów na podstawie domeny aplikacji; jeden algorytm jest używany do obliczania kodów wartości skrótu ciągu. Domyślnie włączone.|  
|`1`|Środowisko uruchomieniowe języka wspólnego oblicza kody skrótów dla ciągów na podstawie domeny aplikacji. Identyczne ciągi w różnych domenach aplikacji i w różnych procesach będą miały różne wartości skrótów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie <xref:System.StringComparer> klasy i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metody użyć pojedynczego algorytmu mieszania, który produkuje spójny kod mieszany w różnych domenach aplikacji. Jest to równoważne ustawieniu `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu `0`. Jest to algorytm mieszania używany w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 <xref:System.StringComparer> Klasy i <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metodę można również użyć innego algorytmu wyznaczania wartości skrótu, który oblicza kody skrótów na poszczególnych domen aplikacji. W rezultacie kody skrótów dla równoważnych ciągów różnią się w różnych domenach aplikacji. Jest to opcjonalna funkcja; Aby z niej korzystać, należy ustawić `enabled` atrybutu `<UseRandomizedStringHashAlgorithm>` elementu `1`.  
  
 Wyszukiwanie ciągu w tabeli skrótów jest zazwyczaj operacją O(1). Jednak w przypadku wystąpienia dużej liczby kolizji wyszukiwanie może stać się O (n<sup>2</sup>) operacji. Możesz użyć `<UseRandomizedStringHashAlgorithm>` element konfiguracji, aby wygenerować losowy algorytm mieszania dla domeny aplikacji, co z kolei ogranicza liczbę potencjalnych konfliktów, szczególnie w przypadku, gdy klucze, z których obliczane są kody mieszania są oparte na danych wejściowych przez użytkowników.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `DisplayString` klasę zawierającą prywatną stałą typu ciąg, `s`, którego wartość jest "Jest ciąg". Obejmuje również `ShowStringHashCode` metoda, która wyświetla wartości ciągu i jego kod skrótu wraz z nazwą domeny aplikacji, w którym metoda jest wykonywaay.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Po uruchomieniu przykładu bez podawania pliku konfiguracji, wyświetla dane wyjściowe podobne do następujących. Należy zauważyć, że kody mieszania dla ciągu są identyczne w dwóch domenach aplikacji.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Jeśli dodasz następujący plik konfiguracji do katalogu w tym przykładzie, a następnie uruchomisz przykład, kody skrótów dla tego samego ciągu będą różne według domeny aplikacji.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Gdy plik konfiguracji jest obecny, przykładzie są wyświetlane następujące dane wyjściowe:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
