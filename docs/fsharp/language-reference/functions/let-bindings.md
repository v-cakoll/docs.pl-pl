---
title: let — Powiązania
description: Dowiedz się, jak używać F# "let" powiązanie, które kojarzy identyfikator z wartością lub funkcji.
ms.date: 05/16/2016
ms.openlocfilehash: 45de82acf6f4423698cd8037266968e023f40dcb
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612676"
---
# <a name="let-bindings"></a>let — Powiązania

A *powiązania* kojarzy identyfikator z wartością lub funkcji. Możesz użyć `let` — słowo kluczowe, aby powiązać nazwę wartości lub funkcji.

## <a name="syntax"></a>Składnia

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Uwagi

`let` Słowo kluczowe jest używane w powiązaniu wyrażeń do definiowania wartości lub wartości funkcji dla co najmniej jedną nazwę. Najprostsza forma `let` wyrażenie wiąże nazwę prostej wartości w następujący sposób.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Jeśli oddzielisz wyrażenia z identyfikatorem przy użyciu nowego wiersza, należy utworzyć wcięcie każdego wiersza wyrażenie, tak jak w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Zamiast tylko nazwy, można określić wzorzec, który zawiera nazwy, na przykład spójna kolekcja, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Wyrażenie treści* jest wyrażeniem, w którym są używane nazwy. Wyrażenie treści pojawia się w osobnym wierszu wcięcia linii się dokładnie z pierwszego znaku w `let` — słowo kluczowe:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A `let` powiązań mogą być wyświetlane na poziomie modułu w definicji typu klasy lub w lokalnych zakresów, takich jak definicja funkcji. A `let` powiązania na najwyższym poziomie, modułu lub typu klasy nie musi zawierać wyrażenie treści, ale na innych poziomach zakresu wyrażenie treści jest wymagane. Powiązane są użyteczne po punkcie definicji, ale nie w dowolnym momencie przed `let` powiązania pojawi się, jak to pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>Powiązania — funkcja

Powiązania funkcji postępuj zgodnie z reguły dla powiązania wartości, z tą różnicą, że funkcja powiązań obejmują nazwy funkcji i parametrów, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Ogólnie rzecz biorąc parametry są wzorców, takich jak wzorzec spójnej kolekcji:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A `let` powiązanie wyrażenie zwróci wartość ostatniego wyrażenia. W związku z tym, w poniższym przykładzie kodu wartość `result` jest obliczany na podstawie `100 * function3 (1, 2)`, która daje w wyniku `300`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Aby uzyskać więcej informacji, zobacz [funkcji](index.md).

## <a name="type-annotations"></a>Deklaracje typów

Można określić typy parametrów, umieszczając dwukropek (:), a następnie nazwę typu, wszystkie ujęty w nawiasy. Można również określić typ wartości zwracanej przez dołączenie dwukropek i typ po ostatnim parametrze. Adnotacje pełny typ dla `function1`, za pomocą liczb całkowitych jako typy parametrów, należy użyć następującego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Jeśli nie ma żadnych parametrów typu jawnego, wnioskowanie o typie umożliwia określić typy parametrów funkcji. Może to obejmować automatyczne uogólnianie typ parametru ogólnego.

Aby uzyskać więcej informacji, zobacz [automatyczna Generalizacja](../generics/automatic-generalization.md) i [wnioskowanie o typie](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Powiązania let w klasach

A `let` powiązań mogą być wyświetlane w typu klasy, ale nie w strukturze lub typie rekordu. Aby użyć umożliwiają powiązania w typie klasy, klasy musi mieć konstruktora podstawowego. Parametry Konstruktora musi znajdować się po nazwie typu w definicji klasy. A `let` powiązania w typie klasy definiuje pola prywatne i członków dla tego typu klasy, a wraz z `do` powiązania w typie formularzy kodu dla konstruktora podstawowego typu. W poniższych przykładach kodu pokazano klasę `MyClass` za pomocą pola prywatne `field1` i `field2`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Zakresy `field1` i `field2` są ograniczone do typu, w którym są one zgłoszone. Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](../members/let-bindings-in-classes.md) i [klasy](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Let — powiązania parametrów typu w

A `let` powiązania na poziomie modułu w typie lub w wyrażeniu obliczeń może mieć parametrów typu jawnego. Let, powiązanie w wyrażeniu, takie jak w definicji funkcji, nie może mieć parametrów typu. Aby uzyskać więcej informacji, zobacz [ogólne](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Atrybuty let — powiązania

Atrybuty mogą być stosowane do najwyższego poziomu `let` powiązania w module, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Zakres i dostępności powiązania Let

Zakres jednostki zadeklarowane za pomocą powiązania let jest ograniczony do części zawierający zakresu (na przykład funkcja modułu, plik lub klasy), po wyświetleniu powiązania. W związku z tym można powiedzieć, że powiązania let wprowadza nazwę w zakresie. W module wartość granicy umożliwiają lub funkcja jest dostępna dla klientów modułu tak długo, jak moduł jest niedostępna, ponieważ powiązania let w moduł są kompilowane do funkcji publicznych modułu. Z drugiej strony powiązania let w klasie są prywatne do klasy.

Zwykle funkcje w modułach musi być kwalifikowana przez nazwę modułu, gdy jest używana przez kod klienta. Na przykład, jeśli moduł `Module1` ma funkcję `function1`, należałoby określić użytkowników `Module1.function1` do odwoływania się do funkcji.

Użytkownicy modułu mogą skorzystać z deklaracji importu, aby udostępnić funkcje w ramach tego modułu do użycia nie jest kwalifikowana przez nazwę modułu. W przykładzie powyżej, użytkownicy modułu można otworzyć w takim przypadku moduł przy użyciu open deklaracji importu `Module1` i po tej dacie odnoszą się do `function1` bezpośrednio.

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

Niektóre moduły mają atrybut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), co oznacza, że funkcje, które udostępniają musi być kwalifikowana z nazwą modułu. Na przykład F# moduł listy ma tego atrybutu.

Aby uzyskać więcej informacji na temat modułów i kontroli dostępu, zobacz [modułów](../modules.md) i [kontroli dostępu](../access-control.md).

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
- [`let` Powiązania w klasach](../members/let-bindings-in-classes.md)