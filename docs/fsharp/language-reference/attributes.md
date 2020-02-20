---
title: Atrybuty
description: Dowiedz F# się, jak atrybuty umożliwiają stosowanie metadanych do konstrukcji programistycznej.
ms.date: 05/16/2016
ms.openlocfilehash: 1e42dc61d44f31930a7b34799f28a68a2db69c8c
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504112"
---
# <a name="attributes"></a>Atrybuty

Atrybuty umożliwiają stosowanie metadanych do konstrukcji programistycznej.

## <a name="syntax"></a>Składnia

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *obiekt docelowy* jest opcjonalny i, jeśli jest obecny, określa rodzaj jednostki programu, do której odnosi się ten atrybut. W tabeli, która pojawia się w dalszej części tego dokumentu, są wyświetlane prawidłowe wartości dla *elementu docelowego* .

*Atrybut-name* odnosi się do nazwy (możliwej do zakwalifikowania z przestrzenią nazw) prawidłowego typu atrybutu, z lub bez sufiksu `Attribute`, który jest zazwyczaj używany w nazwach typu atrybutu. Na przykład typ `ObsoleteAttribute` może być skrócony do zaledwie `Obsolete` w tym kontekście.

*Argumenty* są argumentami konstruktora dla typu atrybutu. Jeśli atrybut ma konstruktora bez parametrów, lista argumentów i nawiasy mogą być pominięte. Atrybuty obsługują zarówno argumenty pozycyjne, jak i nazwane argumenty. *Argumenty pozycyjne* są argumentami, które są używane w kolejności, w jakiej są wyświetlane. Nazwanych argumentów można użyć, jeśli atrybut ma właściwości publiczne. Można je ustawić przy użyciu następującej składni na liście argumentów.

```fsharp
property-name = property-value
```

Takie inicjalizacje właściwości mogą być w dowolnej kolejności, ale muszą być zgodne z dowolnymi argumentami pozycyjnymi. Poniżej znajduje się przykład atrybutu, który używa argumentów pozycyjnych i inicjalizacji właściwości:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

W tym przykładzie atrybut jest `DllImportAttribute`w tym miejscu używany w skróconej postaci. Pierwszy argument jest parametrem pozycyjnym, a drugi jest właściwością.

Atrybuty to konstrukcja programistyczna platformy .NET, która umożliwia obiektowi znanemu jako *atrybut* , który ma być skojarzony z typem lub innym elementem programu. Element programu, do którego zastosowano atrybut, jest określany jako *element docelowy atrybutu*. Ten atrybut zwykle zawiera metadane dotyczące jego obiektu docelowego. W tym kontekście metadane mogą zawierać dowolne dane dotyczące typu innego niż jego pola i elementy członkowskie.

Atrybuty w F# programie można stosować do następujących konstrukcji programistycznych: funkcji, metod, zestawów, modułów, typów (klas, rekordów, struktur, interfejsów, delegatów, wyliczeń, Unii itd.), konstruktorów, właściwości, pól, parametrów, parametrów typu i wartości zwracanych. Atrybuty nie są dozwolone dla powiązań `let` wewnątrz klas, wyrażeń ani wyrażeń przepływu pracy.

Zwykle deklaracja atrybutu pojawia się bezpośrednio przed deklaracją obiektu docelowego atrybutu. Deklaracje wielu atrybutów mogą być używane razem w następujący sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Można badać atrybuty w czasie wykonywania przy użyciu odbicia platformy .NET.

Można zadeklarować wiele atrybutów pojedynczo, jak w poprzednim przykładzie kodu lub można je zadeklarować w jednym zestawie nawiasów, jeśli używasz średnika do oddzielenia poszczególnych atrybutów i konstruktorów w następujący sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Zazwyczaj napotkane atrybuty obejmują atrybut `Obsolete`, atrybuty dla zagadnień związanych z bezpieczeństwem, atrybuty obsługi modelu COM, atrybuty, które odnoszą się do własności kodu, oraz atrybuty wskazujące, czy typ może być serializowany. Poniższy przykład demonstruje użycie atrybutu `Obsolete`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Dla atrybutu targets `assembly` i `module`należy zastosować atrybuty do powiązania `do` najwyższego poziomu w zestawie. W deklaracji atrybutu można uwzględnić słowo `assembly` lub `module` w następujący sposób:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Jeśli pominięto element docelowy atrybutu dla atrybutu zastosowanego do powiązania `do`, F# kompilator próbuje określić obiekt docelowy atrybutu, który jest zrozumiały dla tego atrybutu. Wiele klas atrybutów ma atrybut typu `System.AttributeUsageAttribute`, który zawiera informacje o możliwych celach obsługiwanych przez ten atrybut. Jeśli `System.AttributeUsageAttribute` wskazuje, że atrybut obsługuje funkcje jako elementy docelowe, atrybut jest stosowany do głównego punktu wejścia programu. Jeśli `System.AttributeUsageAttribute` wskazuje, że atrybut obsługuje zestawy jako elementy docelowe, kompilator Pobiera atrybut, który ma zostać zastosowany do zestawu. Większość atrybutów nie ma zastosowania do obu funkcji i zestawów, ale w przypadkach, w których są one wykonywane, atrybut jest stosowany do funkcji Main programu. Jeśli obiekt docelowy atrybutu jest jawnie określony, atrybut jest stosowany do określonego celu.

Mimo że zwykle nie trzeba określać obiektu docelowego atrybutu, prawidłowe wartości dla *elementu docelowego* w atrybucie oraz przykłady użycia przedstawiono w poniższej tabeli:

<table>
  <tr>
    <th>Obiekt docelowy atrybutu</td>
    <th>Przykład</td>
  </tr>
  <tr>
    <td>zestaw</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td>pole</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td>property</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td>param</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td>type</td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(LayoutKind.Sequential)&gt;]
type MyStruct =
  struct
    val x : byte
    val y : int
  end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka F#](index.md)
