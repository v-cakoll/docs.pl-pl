---
title: let — Powiązania
description: Dowiedz się, jak F# używać powiązania "let", które kojarzy identyfikator z wartością lub funkcją.
ms.date: 05/16/2016
ms.openlocfilehash: 654631c7d1c48d8737e6098c98efee54cfdd91be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630640"
---
# <a name="let-bindings"></a>let — Powiązania

*Powiązanie* kojarzy identyfikator z wartością lub funkcją. Użyj słowa kluczowego, `let` aby powiązać nazwę z wartością lub funkcją.

## <a name="syntax"></a>Składnia

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Uwagi

`let` Słowo kluczowe jest używane w wyrażeniach wiązania do definiowania wartości lub wartości funkcji dla co najmniej jednej nazwy. Najprostsza forma `let` wyrażenia wiąże nazwę z prostą wartością w następujący sposób.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Jeśli wyrażenie jest oddzielane od identyfikatora przy użyciu nowego wiersza, należy wciąć każdy wiersz wyrażenia, tak jak w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Zamiast tylko nazwy, wzorzec zawierający nazwy można określić na przykład krotka, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Wyrażenie Body* jest wyrażeniem, w którym są używane nazwy. Wyrażenie treści jest wyświetlane w osobnym wierszu, wcięcie w celu podzielenia dokładnie z pierwszym znakiem `let` słowa kluczowego:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

`let` Powiązanie może być wyświetlane na poziomie modułu, w definicji typu klasy lub w lokalnych zakresach, takich jak w definicji funkcji. `let` Powiązanie na najwyższym poziomie modułu lub w typie klasy nie musi mieć wyrażenia Body, ale na innych poziomach zakresu wyrażenie treści jest wymagane. Nazwy powiązane są użyteczne po punkcie definicji, ale nie w żadnym punkcie przed `let` wyświetleniem powiązania, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a>Powiązania funkcji

Powiązania funkcji są zgodne z regułami dotyczącymi powiązań wartości, z tą różnicą, że powiązania funkcji zawierają nazwę funkcji i parametry, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Ogólnie rzecz biorąc, parametry są wzorcami, takimi jak wzorzec krotki:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

Wyrażenie `let` powiązania daje w wyniku wartość ostatniego wyrażenia. W związku z tym, w poniższym przykładzie kodu, wartość `result` jest obliczana z `100 * function3 (1, 2)` `300`, która daje w wyniku.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Aby uzyskać więcej informacji, zobacz [funkcji](index.md).

## <a name="type-annotations"></a>Adnotacje typu

Można określić typy parametrów, dołączając dwukropek (:) po którym następuje nazwa typu, wszystkie zawarte w nawiasach. Można również określić typ wartości zwracanej przez dołączenie dwukropka i typu po ostatnim parametrze. Pełne adnotacje typu dla `function1`, z liczbami całkowitymi jako typy parametrów, byłyby następujące.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Jeśli nie ma żadnych jawnych parametrów typu, wnioskowanie typu jest używane do określenia typów parametrów funkcji. Może to obejmować automatyczne uogólnianie typu parametru, który ma być ogólny.

Aby uzyskać więcej informacji, zobacz [Automatyczne uogólnianie](../generics/automatic-generalization.md) i wnioskowanie o [typie](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Powiązania let w klasach

`let` Powiązanie może pojawić się w typie klasy, ale nie w typie struktury lub rekordu. Aby można było użyć powiązania let w typie klasy, Klasa musi mieć konstruktora podstawowego. Parametry konstruktora muszą występować po nazwie typu w definicji klasy. Powiązanie w typie klasy definiuje prywatne pola i elementy członkowskie dla tego typu klasy oraz, wraz z `do` powiązaniami w typie, tworzy kod dla głównego konstruktora typu. `let` Poniższe przykłady kodu przedstawiają klasę `MyClass` z polami `field1` prywatnymi i `field2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Zakresy `field1` i`field2` są ograniczone do typu, w którym są zadeklarowane. Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](../members/let-bindings-in-classes.md) i [klasach](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Parametry typu w programie Let bindings

`let` Powiązanie na poziomie modułu, w typie lub w wyrażeniu obliczeniowym może mieć jawne parametry typu. Powiązanie let w wyrażeniu, takie jak w definicji funkcji, nie może mieć parametrów typu. Aby uzyskać więcej informacji, zobacz [Ogólne](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Atrybuty dla powiązań Let

Atrybuty mogą być stosowane do powiązań najwyższego poziomu `let` w module, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a>Zakres i dostępność powiązań Let

Zakres jednostki zadeklarowanej za pomocą powiązania Let jest ograniczony do części zawierającego ją zakresu (na przykład funkcji, modułu, pliku lub klasy) po wyświetleniu powiązania. W związku z tym może być uważany, że powiązanie Let wprowadza nazwę do zakresu. W module, wartość lub funkcja, którą można powiązać, jest dostępna dla klientów modułu, o ile moduł jest dostępny, ponieważ powiązania let w module są kompilowane do funkcji publicznych modułu. Z kolei należy zezwolić na powiązania w klasie z klasą.

Zwykle funkcje w modułach muszą być kwalifikowane według nazwy modułu, gdy są używane przez kod klienta. Na przykład jeśli moduł `Module1` zawiera funkcję `function1`, użytkownicy mogą `Module1.function1` odwoływać się do funkcji.

Użytkownicy modułu mogą używać deklaracji importu, aby udostępnić funkcje w ramach tego modułu bez zakwalifikowania nazwy modułu. W takim przykładzie użytkownicy modułu mogą w tym przypadku otworzyć moduł przy użyciu otwartej `Module1` deklaracji import, a następnie odwołać się bezpośrednio do `function1` niego.

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

Niektóre moduły mają atrybut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), co oznacza, że funkcje, które uwidaczniają, muszą być kwalifikowane przy użyciu nazwy modułu. Na przykład moduł F# listy ma ten atrybut.

Aby uzyskać więcej informacji na temat modułów i kontroli dostępu, zobacz [moduły](../modules.md) i [Access Control](../access-control.md).

## <a name="see-also"></a>Zobacz także

- [Funkcje](index.md)
- [`let`Powiązania w klasach](../members/let-bindings-in-classes.md)
