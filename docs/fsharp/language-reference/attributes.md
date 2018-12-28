---
title: Atrybuty
description: Dowiedz się, jak F# atrybuty Włącz metadane, które mają być stosowane do konstrukcji programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 34223523efbb3bd89bb73f35fac3dfd8113d8611
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611845"
---
# <a name="attributes"></a>Atrybuty

Atrybuty Włącz metadanych, które mają być stosowane do konstrukcji programowania.

## <a name="syntax"></a>Składnia

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *docelowej* jest opcjonalny, a jeśli jest obecny, określa typ jednostki program, który dotyczy ten atrybut. Prawidłowe wartości dla *docelowej* są wyświetlane w tabeli, która pojawia się w dalszej części tego dokumentu.

*Nazwa atrybutu* odwołuje się do nazwy (prawdopodobnie kwalifikowany za pomocą przestrzeni nazw) prawidłowego atrybutu typu, z lub bez sufiksu `Attribute` zwykle używany w nazwach typu atrybutu. Na przykład typ `ObsoleteAttribute` może zostać skrócony tylko `Obsolete` w tym kontekście.

*Argumenty* argumentów konstruktora dla typu atrybutu. Jeśli atrybut ma domyślnego konstruktora, można pominąć listy argumentów i nawiasy. Atrybuty obsługują argumenty pozycyjne i nazwane argumenty. *Argumenty pozycyjne* argumentów, które są używane w kolejności, w jakiej są wyświetlane. Argumenty nazwane może służyć, jeśli atrybut ma właściwości publiczne. Możesz ustawić te elementy przy użyciu następującej składni na liście argumentów.

```
*property-name* = *property-value*
```

Takie inicjowania właściwości mogą znajdować się w dowolnej kolejności, ale muszą wykonać żadnych argumentów pozycyjnych. Poniżej przedstawiono przykład atrybutu, który używa argumentów pozycyjnych i inicjowania właściwości.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

W tym przykładzie atrybut jest `DllImportAttribute`, w tym miejscu są używane w formie skróconej. Pierwszy argument jest parametr pozycyjne, a drugą jest wartość właściwości.

Atrybuty są konstrukcja programowania .NET, która umożliwia obiektu, nazywany *atrybut* ma zostać skojarzony z typem lub innego elementu programu. Element programu, do którego zastosowano atrybut jest znany jako *element docelowy atrybutu*. Ten atrybut zawiera zazwyczaj metadane dotyczące jego element docelowy. W tym kontekście metadanych może być żadnych danych o typie innym niż jego pola i elementy członkowskie.

Atrybuty w F# mogą być stosowane do następujące konstrukcje programowania: funkcje metod, zestawy, moduły, typami (klasy, rekordy, struktury, interfejsy, delegaty, wyliczenia, Unii i tak dalej), konstruktory, właściwości, pola, Parametry, wpisz parametry i zwracane wartości. Atrybuty nie są dozwolone w `let` powiązania wewnątrz klasy, wyrażenia lub wyrażeń przepływu pracy.

Zazwyczaj deklaracji atrybutu pojawia się bezpośrednio przed deklaracją elementu docelowego atrybutu. Wiele deklaracji atrybutu można ze sobą, wykonując następujące czynności.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Atrybuty można badać w czasie wykonywania przy użyciu odbicia .NET.

Można zadeklarować wiele atrybutów pojedynczo, tak jak w poprzednim przykładzie kodu lub można je zadeklarować w jeden zestaw nawiasów Jeśli Użyj średnika do rozdzielenia poszczególne atrybuty i konstruktory, jak pokazano poniżej.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Atrybuty najczęściej obejmują `Obsolete` atrybutu, atrybuty, które ze względów bezpieczeństwa atrybuty do obsługi COM, atrybuty, które odnoszą się do własności kodu i atrybutów, wskazującą, czy typ może być serializowany. W poniższym przykładzie pokazano użycie `Obsolete` atrybutu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Dla celów atrybut `assembly` i `module`, Zastosuj atrybuty do najwyższego poziomu `do` powiązanie w swoim zestawie. Może zawierać słowa `assembly` lub `module` w deklaracji atrybutu w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Jeżeli pominięto element docelowy atrybutu dla atrybutu, dotyczy `do` powiązania F# kompilator spróbuje określić element docelowy atrybutu, który ma sens dla tego atrybutu. Wiele klas atrybutów ma atrybut typu `System.AttributeUsageAttribute` zawierającej informacje o możliwych elementów docelowych obsługiwane dla tego atrybutu. Jeśli `System.AttributeUsageAttribute` wskazuje, że ten atrybut obsługuje funkcje jako elementy docelowe, ten atrybut pochodzi dotyczą główny punkt wejścia programu. Jeśli `System.AttributeUsageAttribute` wskazuje, że ten atrybut obsługuje zestawy jako elementy docelowe, kompilator przyjmuje atrybutu do zastosowania do zestawu. Większość atrybutów nie dotyczą zarówno funkcje, jak i zestawy, ale w przypadkach, gdy robią, ten atrybut jest zajęta do zastosowania do funkcji main tego programu. Jeśli element docelowy atrybutu jest jawnie określona, jest stosowany do określonego celu.

Mimo że nie zwykle należy określić atrybut docelowy jawnie, prawidłowe wartości dla *docelowej* w atrybucie są wyświetlane w poniższej tabeli, a także przykłady użycia.

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
    <td>"let function1 x: [<return: Obsolete>] int = x + 1"</td> 
  </tr>
  <tr>
    <td>pole</td>
    <td>"[<field: DefaultValue>] val mutable x: int"</td> 
  </tr>
  <tr>
    <td>property</td>
    <td>"[<property: Obsolete>] to. MyProperty = x "</td> 
  </tr>
  <tr>
    <td>param</td>
    <td>"element członkowski to. MyMethod ([<param: Out>] x: ref<int>) = x: = 10'.</td> 
  </tr>
  <tr>
    <td>— typ</td>
    <td>

        ```
        [<type: StructLayout(Sequential)>] 
        type MyStruct = 
        struct 
        x : byte
        y : int
        end
        ```
    </td> 
  </tr>
</table>

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)