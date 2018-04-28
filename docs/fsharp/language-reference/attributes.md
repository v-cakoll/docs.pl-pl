---
title: Atrybuty (F#)
description: 'Dowiedz się, jak włączyć metadanych ma być stosowany do konstrukcji programującej przez atrybuty F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: b8efc0cdc14e690bbc5c24456d0b1eaa3d55988e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="attributes"></a>Atrybuty

Atrybuty Włącz metadanych ma być stosowany do programowania konstrukcji.

## <a name="syntax"></a>Składnia

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Uwagi

W poprzednich składni *docelowej* jest opcjonalna i, jeśli jest obecny, określa typ jednostki program, którego dotyczy ten atrybut. Prawidłowymi wartościami dla *docelowej* są wyświetlane w tabeli, która pojawia się w dalszej części tego dokumentu.

*Nazwa atrybutu* odwołuje się do nazwy (prawdopodobnie kwalifikowany za pomocą przestrzeni nazw) z prawidłowego typu atrybutu, lub bez sufiks `Attribute` zwykle używany w nazwach typu atrybutu. Na przykład typ `ObsoleteAttribute` może zostać skrócony nieco `Obsolete` w tym kontekście.

*Argumenty* argumentów konstruktora dla typu atrybutu. Jeśli atrybut ma domyślny konstruktor, można pominąć listy argumentów i nawiasy. Atrybuty obsługują argumenty pozycyjne i nazwanych argumentów. *Argumenty pozycyjne* są argumenty, które są używane w kolejności ich występowania. Jeśli ten atrybut ma właściwości publiczne można nazwanych argumentów. Można ustawić przy użyciu następującej składni w liście argumentów.

```
*property-name* = *property-value*
```

Takie inicjowania właściwości można w dowolnej kolejności, ale muszą wykonać żadnych argumentów pozycyjnych. Poniżej przedstawiono przykład atrybut, który używa argumentów pozycyjnych i inicjowania właściwości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

W tym przykładzie ten atrybut jest `DllImportAttribute`, w tym miejscu są używane w formie skróconej. Pierwszy argument jest parametrów pozycyjnych, a drugą jest wartość właściwości.

Atrybuty są konstrukcję programowania .NET umożliwia obiektu znanego jako *atrybut* ma zostać skojarzony z typem lub innego elementu programu. Element programu, do którego zastosowano atrybut nosi nazwę *element docelowy atrybutu*. Ten atrybut zawiera zwykle metadane dotyczące elementem docelowym. W tym kontekście metadanych można żadnych danych o typie innym niż jego pola i elementy członkowskie.

Atrybuty w języku F # można zastosować do następujących narzędzi programistycznych: funkcje metod, zestawy, moduły, typów (klas, rekordów, struktury, interfejsy, delegatów, wyliczeń, Unii i tak dalej), konstruktorów, właściwości, pola, parametrów, Parametry typu i wartości zwracane. Atrybuty są niedozwolone w `let` powiązania wewnątrz klasy, wyrażenia lub wyrażeń przepływu pracy.

Zazwyczaj deklaracji atrybutu pojawia się bezpośrednio przed deklaracją elementu docelowego atrybutu. Wiele deklaracji atrybutu można ze sobą w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Atrybuty w czasie wykonywania można badać przy użyciu odbicia .NET.

Można zadeklarować wiele atrybutów indywidualnie, co w poprzednim przykładzie kodu lub mogą zadeklarować ich w jednym zestawie nawiasów Jeśli Użyj średnika do oddzielenia poszczególnych atrybutów i konstruktorów, jak pokazano poniżej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Atrybuty najczęściej spotykanych obejmują `Obsolete` atrybutu, atrybuty zagadnienia dotyczące zabezpieczeń, atrybuty do obsługi modelu COM, atrybuty, które odnoszą się do właściciela kodu i atrybuty wskazującą, czy można zserializować typu. W poniższym przykładzie pokazano użycie `Obsolete` atrybutu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Dla celów atrybutu `assembly` i `module`, zastosować atrybutów do najwyższego poziomu `do` powiązania w tym zestawem. Może zawierać słowo `assembly` lub `module` w deklaracji atrybutu w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Jeśli pominięto element docelowy atrybutu dla atrybutu dotyczą `do` powiązanie, kompilator języka F # spróbuje określić element docelowy atrybutu, który ma sens dla tego atrybutu. Wiele klas atrybut ma atrybut typu `System.AttributeUsageAttribute` zawierającą informacje o możliwych elementy docelowe obsługiwane dla tego atrybutu. Jeśli `System.AttributeUsageAttribute` wskazuje, czy ten atrybut obsługuje funkcje jako miejsca docelowe, ten atrybut jest przełączany do zastosowania do główny punkt wejścia programu. Jeśli `System.AttributeUsageAttribute` wskazuje, że ten atrybut obsługuje zestawy jako miejsca docelowe, kompilator ma atrybut do zastosowania do zestawu. Większość atrybutów nie dotyczą zarówno funkcje i zestawy, ale w przypadkach, gdy robią, ten atrybut pochodzi do zastosowania do głównych funkcji programu. Jeśli element docelowy atrybutu jest jawnie określony, atrybut jest stosowany do określonego obiektu docelowego.

Chociaż zazwyczaj zbędna, nie można określić atrybutu target jawnie, prawidłowe wartości *docelowej* w atrybucie przedstawiono w poniższej tabeli, wraz z przykładem użycia.

<table>
  <tr>
    <th>Element docelowy atrybutu</td>
    <th>Przykład</td> 
  </tr>
  <tr>
    <td>zestaw</td>
    <td>`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</td> 
  </tr>
  <tr>
    <td>return</td>
    <td>"let function1 x: [<return: Obsolete>] int = x + 1'</td> 
  </tr>
  <tr>
    <td>pole</td>
    <td>"[<field: DefaultValue>] val mutable x: int"</td> 
  </tr>
  <tr>
    <td>property</td>
    <td>"[<property: Obsolete>] to. MyProperty = x'</td> 
  </tr>
  <tr>
    <td>Param</td>
    <td>"elementu członkowskiego to. MyMethod ([<param: Out>] x: ref<int>) = x: = 10'.</td> 
  </tr>
  <tr>
    <td>— typ</td>
    <td>
        ```
        [<type: StructLayout(Sequential)>] wpisz MyStruct = struct x: byte y: int zakończenia ```
    </td> 
  </tr>
</table>

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka F#](index.md)
