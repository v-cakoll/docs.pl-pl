---
title: "let — Powiązania (F#)"
description: "Dowiedz się, jak używać F # \"let\" powiązanie, co umożliwia skojarzenie identyfikatora z wartości lub funkcji."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: bee69edc-d5ae-46bd-8b56-f02d97725d0d
ms.openlocfilehash: a57c5572e4bb5a3777c928dd572b7a84d4f0a334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings"></a>let — Powiązania

A *powiązania* kojarzy identyfikator z wartości lub funkcji. Możesz użyć `let` — słowo kluczowe, aby powiązać nazwę wartości lub funkcji.

## <a name="syntax"></a>Składnia

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a>Uwagi

`let` Słowo kluczowe jest używane w wyrażenia, aby zdefiniować wartości lub wartości funkcji dla jednego lub więcej nazw powiązania. Najprostsza forma `let` wyrażenie wiąże nazwę prostą wartością w następujący sposób.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

Jeśli wyrażenie z identyfikatorem oddzielić przy użyciu nowego wiersza, musi wcięcie każdego wiersza wyrażenia, zgodnie z poniższym kodem.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

Zamiast tylko nazwę wzorca, który zawiera nazwy można określić, na przykład spójnej kolekcji, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

*Treść wyrażenia* jest wyrażeniem, w którym są używane nazwy. Wyrażenie treści pojawia się w oddzielnej linii, wcięcia wiersza się dokładnie z pierwszego znaku w `let` — słowo kluczowe:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

A `let` powiązania mogą być wyświetlane na poziomie modułu w definicji typu klasy lub w zakresach lokalnego, taki jak definicji funkcji. A `let` powiązania na najwyższym poziomie w module lub w typie klasy musi mieć wyrażenie treści, ale na innych poziomach zakresu, wymagane jest wyrażenie treści. Nazwy powiązane są użyteczne po punkcie definicji, ale nie w dowolnym momencie przed `let` powiązania pojawia się, jak przedstawiono w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a>Powiązania funkcji

Powiązania funkcji zgodne z regułami dotyczącymi powiązania wartości, z wyjątkiem tego powiązania funkcji obejmują nazwy funkcji i parametrów, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

Ogólnie rzecz biorąc parametry są wzorców, takich jak wzorzec spójnej kolekcji:

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

A `let` powiązanie wyrażenie daje w wyniku wartość ostatniego wyrażenia. W związku z tym w poniższym przykładzie kodu wartość `result` jest obliczana na podstawie `100 * function3 (1, 2)`, która daje w wyniku `300`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

Aby uzyskać więcej informacji, zobacz [funkcji](index.md).

## <a name="type-annotations"></a>Adnotacje typu

Można określić typy parametrów, umieszczając dwukropka (:), a następnie nazwę typu, wszystkie ujęty w nawiasy. Można również określić typ wartości zwracanej przez dołączenie dwukropek i typ po ostatnim parametrem. Adnotacje pełny typ dla `function1`, z liczb całkowitych jako typy parametrów, zostaną wyświetlone następujące.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

Jeśli nie ma żadnych jawnych parametrów typu, wnioskowanie o typie służy do określania typami parametrów funkcji. Może to obejmować automatyczne uogólnianie typ parametru, aby wartość była ogólna.

Aby uzyskać więcej informacji, zobacz [automatyczna Generalizacja](../generics/automatic-generalization.md) i [wnioskowanie o typie](../type-inference.md).

## <a name="let-bindings-in-classes"></a>Powiązania let w klasach

A `let` powiązania może występować w typie klasy, ale nie w strukturze lub typ rekordu. Aby użyć let powiązania w typie klasy, klasy musi mieć konstruktora podstawowego. Parametry Konstruktora musi występować po nazwie typu w definicji klasy. A `let` powiązania w typie klasy definiuje pól prywatnych i członków dla tego typu klasy, wraz z `do` powiązania w typie, formularzy kod podstawowego konstruktora dla typu. W poniższych przykładach kodu pokazano klasy `MyClass` z pól prywatnych `field1` i `field2`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

Zakresy z `field1` i `field2` są ograniczone do typu, w którym jest zadeklarowany. Aby uzyskać więcej informacji, zobacz [ `let` powiązania w klasach](../members/let-bindings-in-classes.md) i [klasy](../classes.md).

## <a name="type-parameters-in-let-bindings"></a>Parametrów typu w let — powiązania

A `let` powiązanie na poziomie modułu, typu lub wyrażenie do obliczenia mogą zawierać jawnych parametrów typu. Let powiązania w wyrażeniu, takich jak w definicji funkcji, nie może mieć parametrów typu. Aby uzyskać więcej informacji, zobacz [ogólne](../generics/index.md).

## <a name="attributes-on-let-bindings"></a>Atrybuty let — powiązania

Atrybuty można zastosować do najwyższego poziomu `let` powiązania w module, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a>Zakres i dostępności powiązania Let

Zakres jednostka zadeklarowana z powiązaniem let jest ograniczony do części zawierający zakres (na przykład funkcji, modułu, plik lub klasy) po wyświetleniu powiązania. W związku z tym można powiedzieć, że powiązanie let wprowadza nazwę do zakresu. W module wartość let wiązaniem lub funkcja jest dostępna dla klientów modułu tak długo, jak moduł jest niedostępny, ponieważ powiązania let w module są skompilowane w publicznych funkcji modułu. Z kolei powiązania let w klasach są prywatne do klasy.

Zwykle funkcje w modułach musi być kwalifikowana przez nazwę modułu, gdy jest używany przez kod klienta. Na przykład, jeśli moduł `Module1` ma funkcję `function1`, użytkownicy będą określać `Module1.function1` do odwoływania się do funkcji.

Użytkownicy modułu może używać deklaracja importu, aby udostępnić funkcje w ramach tego modułu do użytku nie jest kwalifikowana przez nazwę modułu. W przykładzie wymienionym powyżej użytkowników modułu można otworzyć w takim przypadku moduł za pomocą polecenia Otwórz deklaracji importu `Module1` , a następnie odwoływać się do `function1` bezpośrednio.

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

Niektóre moduły mają atrybut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), co oznacza, że funkcje, które udostępniają musi być kwalifikowana nazwą modułu. Na przykład moduł F # listy ma tego atrybutu.

Aby uzyskać więcej informacji dotyczących modułów i kontroli dostępu, zobacz [modułów](../modules.md) i [kontroli dostępu](../access-control.md).

## <a name="see-also"></a>Zobacz też

[Funkcje](index.md)

[`let`Powiązania w klasach](../members/let-bindings-in-classes.md)
