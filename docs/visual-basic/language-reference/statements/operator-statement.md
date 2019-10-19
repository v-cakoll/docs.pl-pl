---
title: Operator — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: c4fae40992fa665121aff637ae427ef0cafbf547
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582381"
---
# <a name="operator-statement"></a>Operator — Instrukcja

Deklaruje symbol operatora, argumenty operacji i kod, który definiuje procedurę operatora w klasie lub strukturze.

## <a name="syntax"></a>Składnia

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a>Części

`attrlist`  
Opcjonalny. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).

`Public`  
Wymagany. Wskazuje, że ta procedura operatora ma dostęp [publiczny](../../../visual-basic/language-reference/modifiers/public.md) .

`Overloads`  
Opcjonalny. Zobacz [przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md).

`Shared`  
Wymagany. Wskazuje, że procedura operatora jest [wspólną](../../../visual-basic/language-reference/modifiers/shared.md) procedurą.

`Shadows`  
Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

`Widening`  
Wymagane dla operatora konwersji, chyba że zostanie określona `Narrowing`. Wskazuje, że ta procedura operatora definiuje konwersję [rozszerzającą](../../../visual-basic/language-reference/modifiers/widening.md) . Zobacz "rozszerzanie i zwężanie konwersji" na tej stronie pomocy.

`Narrowing`  
Wymagane dla operatora konwersji, chyba że zostanie określona `Widening`. Wskazuje, że ta procedura operatora definiuje [Zawężanie](../../../visual-basic/language-reference/modifiers/narrowing.md) konwersji. Zobacz "rozszerzanie i zwężanie konwersji" na tej stronie pomocy.

`operatorsymbol`  
Wymagany. Symbol lub identyfikator operatora, który definiuje procedura operatora.

`operand1`  
Wymagany. Nazwa i typ pojedynczego operandu operatora jednoargumentowego (w tym operatora konwersji) lub lewego operandu operatora binarnego.

`operand2`  
Wymagane dla operatorów binarnych. Nazwa i typ prawnego operandu operatora binarnego.

`operand1` i `operand2` mają następującą składnię i części:

`[ ByVal ] operandname [ As operandtype ]`

|Części|Opis|
|----------|-----------------|
|`ByVal`|Opcjonalne, ale mechanizm przekazywania musi być [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|
|`operandname`|Wymagany. Nazwa zmiennej reprezentującej ten operand. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`operandtype`|Opcjonalne, chyba że `Option Strict` jest `On`. Typ danych tego operandu.|

`type`  
Opcjonalne, chyba że `Option Strict` jest `On`. Typ danych wartości zwracanej przez procedurę operatora.

`statements`  
Opcjonalny. Blok instrukcji wykonywanych przez procedurę operatora.

`returnvalue`  
Wymagany. Wartość, którą procedura operatora zwraca do kodu wywołującego.

`End``Operator`  
Wymagany. Kończy definicję tej procedury operatora.

## <a name="remarks"></a>Uwagi

@No__t_0 można używać tylko w klasie lub strukturze. Oznacza to, że *kontekst deklaracji* dla operatora nie może być plikiem źródłowym, przestrzenią nazw, modułem, interfejsem, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Wszystkie operatory muszą być `Public Shared`. Dla każdego operandu nie można określić `ByRef`, `Optional` lub `ParamArray`.

Nie można użyć symbolu operatora lub identyfikatora do przechowywania wartości zwracanej. Należy użyć instrukcji `Return` i określić wartość. Dowolna liczba instrukcji `Return` może występować w dowolnym miejscu procedury.

Definiowanie operatora w ten sposób jest nazywane *przeciążeniem operatora*, niezależnie od tego, czy jest używane słowo kluczowe `Overloads`. W poniższej tabeli wymieniono operatory, które można zdefiniować.

|Typ|Operatory|
|----------|---------------|
|Jednostk|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|plików binarnych|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, 0, 1, 2, 3, 4, 5 , 6, 7, 8 9|
|Konwersja (Jednoargumentowa)|`CType`|

Należy zauważyć, że operator `=` na liście elementów binarnych jest operatorem porównania, a nie operatorem przypisania.

Podczas definiowania `CType` należy określić `Widening` lub `Narrowing`.

## <a name="matched-pairs"></a>Dopasowane pary

Należy zdefiniować określone operatory jako dopasowane pary. W przypadku zdefiniowania dowolnego operatora takiej pary należy zdefiniować również pozostałe. Dopasowane pary są następujące:

- `=` i `<>`

- `>` i `<`

- `>=` i `<=`

- `IsTrue` i `IsFalse`

## <a name="data-type-restrictions"></a>Ograniczenia dotyczące typów danych

Każdy zdefiniowany operator musi zawierać klasę lub strukturę, w których ją zdefiniujesz. Oznacza to, że Klasa lub struktura muszą występować jako typ danych następujących elementów:

- Operand operatora jednoargumentowego.

- Co najmniej jeden operand operatora binarnego.

- Operand lub zwracany typ operatora konwersji.

 Niektóre operatory mają dodatkowe ograniczenia dotyczące typów danych w następujący sposób:

- Jeśli zdefiniujesz operatory `IsTrue` i `IsFalse`, muszą one zwracać typ `Boolean`.

- Jeśli zdefiniujesz operatory `<<` i `>>`, muszą one określić typ `Integer` dla `operandtype` `operand2`.

Zwracany typ nie musi odpowiadać typowi żadnego operandu. Na przykład operator porównania, taki jak `=` lub `<>`, może zwrócić `Boolean` nawet wtedy, gdy żaden operand nie jest `Boolean`.

## <a name="logical-and-bitwise-operators"></a>Operatory logiczne i bitowe

Operatory `And`, `Or`, `Not` i `Xor` mogą wykonywać operacje logiczne lub bitowe w Visual Basic. Jeśli jednak zdefiniujesz jeden z tych operatorów w klasie lub strukturze, możesz zdefiniować tylko jej operację bitową.

Nie można zdefiniować operatora `AndAlso` bezpośrednio przy użyciu instrukcji `Operator`. Można jednak użyć `AndAlso`, jeśli spełniono następujące warunki:

- Zdefiniowano `And` w tych samych typach operandów, które mają być używane dla `AndAlso`.

- Definicja `And` zwraca ten sam typ co Klasa lub struktura, w której została zdefiniowana.

- Zdefiniowano operator `IsFalse` na klasie lub strukturze, na których zdefiniowano `And`.

Podobnie, można użyć `OrElse`, jeśli zdefiniowano `Or` dla tych samych operandów, z typem zwracanym klasy lub struktury, a zdefiniowano `IsTrue` na klasie lub strukturze.

## <a name="widening-and-narrowing-conversions"></a>Rozszerzanie i zwężanie konwersji

*Konwersja rozszerzająca* zawsze powiedzie się w czasie wykonywania, podczas gdy *Konwersja wąskiego* może zakończyć się niepowodzeniem w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

Jeśli deklarujesz procedurę konwersji do `Widening`, kod procedury nie może generować żadnych błędów. Oznacza to następujące kwestie:

- Musi zawsze zwracać prawidłową wartość typu `type`.

- Musi obsługiwać wszystkie możliwe wyjątki i inne warunki błędu.

- Musi obsłużyć wszelkie błędy zwracane przez wszystkie procedury, które wywołuje.

Jeśli istnieje jakakolwiek możliwość, że procedura konwersji może się nie powieść lub że może to spowodować nieobsługiwany wyjątek, należy zadeklarować ją jako `Narrowing`.

## <a name="example"></a>Przykład

Poniższy przykład kodu używa instrukcji `Operator` do definiowania konspektu struktury, która zawiera procedury operatorów dla operatorów `And`, `Or`, `IsFalse` i `IsTrue`. `And` i `Or` każda z nich przyjmuje dwa operandy typu `abc` i zwracany typ `abc`. `IsFalse` i `IsTrue` każda z nich przyjmuje jeden operand typu `abc` i zwraca `Boolean`. Te definicje umożliwiają wywołującemu kod używanie `And`, `AndAlso`, `Or` i `OrElse` z operandami typu `abc`.

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a>Zobacz także

- [IsFalse, operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Instrukcje: definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Instrukcje: wywoływanie procedury operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [Instrukcje: używanie klasy definiującej operatory](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
