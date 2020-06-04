---
title: Operator — Instrukcja
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
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404398"
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
Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).

`Public`  
Wymagany. Wskazuje, że ta procedura operatora ma dostęp [publiczny](../modifiers/public.md) .

`Overloads`  
Opcjonalny. Zobacz [przeciążenia](../modifiers/overloads.md).

`Shared`  
Wymagany. Wskazuje, że procedura operatora jest [wspólną](../modifiers/shared.md) procedurą.

`Shadows`  
Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).

`Widening`  
Wymagane dla operatora konwersji, chyba że zostanie określony `Narrowing` . Wskazuje, że ta procedura operatora definiuje konwersję [rozszerzającą](../modifiers/widening.md) . Zobacz "rozszerzanie i zwężanie konwersji" na tej stronie pomocy.

`Narrowing`  
Wymagane dla operatora konwersji, chyba że zostanie określony `Widening` . Wskazuje, że ta procedura operatora definiuje [Zawężanie](../modifiers/narrowing.md) konwersji. Zobacz "rozszerzanie i zwężanie konwersji" na tej stronie pomocy.

`operatorsymbol`  
Wymagany. Symbol lub identyfikator operatora, który definiuje procedura operatora.

`operand1`  
Wymagany. Nazwa i typ pojedynczego operandu operatora jednoargumentowego (w tym operatora konwersji) lub lewego operandu operatora binarnego.

`operand2`  
Wymagane dla operatorów binarnych. Nazwa i typ prawnego operandu operatora binarnego.

`operand1`i `operand2` mają następującą składnię i części:

`[ ByVal ] operandname [ As operandtype ]`

|Część|Opis|
|----------|-----------------|
|`ByVal`|Opcjonalne, ale mechanizm przekazywania musi być [ByVal](../modifiers/byval.md).|
|`operandname`|Wymagany. Nazwa zmiennej reprezentującej ten operand. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`operandtype`|Opcjonalne, chyba że `Option Strict` jest `On` . Typ danych tego operandu.|

`type`  
Opcjonalne, chyba że `Option Strict` jest `On` . Typ danych wartości zwracanej przez procedurę operatora.

`statements`  
Opcjonalny. Blok instrukcji wykonywanych przez procedurę operatora.

`returnvalue`  
Wymagany. Wartość, którą procedura operatora zwraca do kodu wywołującego.

`End` `Operator`  
Wymagany. Kończy definicję tej procedury operatora.

## <a name="remarks"></a>Uwagi

Można używać `Operator` tylko w klasie lub strukturze. Oznacza to, że *kontekst deklaracji* dla operatora nie może być plikiem źródłowym, przestrzenią nazw, modułem, interfejsem, procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

Wszystkie operatory muszą być `Public Shared` . Nie można określić `ByRef` , `Optional` , lub `ParamArray` dla obu operandów.

Nie można użyć symbolu operatora lub identyfikatora do przechowywania wartości zwracanej. Musisz użyć `Return` instrukcji i określić wartość. Dowolna liczba `Return` instrukcji może pojawić się w dowolnym miejscu w procedurze.

Definiowanie operatora w ten sposób jest nazywane *przeciążeniem operatora*, niezależnie od tego, czy jest używane `Overloads` słowo kluczowe. W poniższej tabeli wymieniono operatory, które można zdefiniować.

|Typ|Operatory|
|----------|---------------|
|Jednoargumentowy|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|Binarne|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|
|Konwersja (Jednoargumentowa)|`CType`|

Należy zauważyć, że `=` operator na liście Binary jest operatorem porównania, a nie operatorem przypisania.

Podczas definiowania należy `CType` określić albo `Widening` lub `Narrowing` .

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

- Jeśli zdefiniujesz `IsTrue` Operatory i `IsFalse` , muszą one zwracać `Boolean` Typ.

- Jeśli zdefiniujesz `<<` Operatory i `>>` , muszą one określić `Integer` Typ dla `operandtype` elementu `operand2` .

Zwracany typ nie musi odpowiadać typowi żadnego operandu. Na przykład operator porównania, taki jak `=` lub, `<>` może zwrócić `Boolean` nawet wtedy, gdy żaden operand nie jest `Boolean` .

## <a name="logical-and-bitwise-operators"></a>Operatory logiczne i bitowe

`And`Operatory, `Or` , `Not` i `Xor` mogą wykonywać operacje logiczne lub bitowe w Visual Basic. Jeśli jednak zdefiniujesz jeden z tych operatorów w klasie lub strukturze, możesz zdefiniować tylko jej operację bitową.

Nie można zdefiniować `AndAlso` operatora bezpośrednio przy użyciu `Operator` instrukcji. Można jednak użyć, `AndAlso` jeśli spełniono następujące warunki:

- Zdefiniowano `And` te same typy operandów, których chcesz użyć dla `AndAlso` .

- Twoja definicja `And` zwraca ten sam typ co Klasa lub struktura, w której została zdefiniowana.

- Zdefiniowano `IsFalse` operator na klasie lub strukturze, na których zdefiniowano `And` .

Analogicznie, można użyć, `OrElse` Jeśli zdefiniowano `Or` dla tych samych operandów, z typem zwracanym klasy lub struktury i zdefiniowanej `IsTrue` na klasie lub strukturze.

## <a name="widening-and-narrowing-conversions"></a>Rozszerzanie i zwężanie konwersji

*Konwersja rozszerzająca* zawsze powiedzie się w czasie wykonywania, podczas gdy *Konwersja wąskiego* może zakończyć się niepowodzeniem w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

Jeśli deklarujesz procedurę konwersji `Widening` , kod procedury nie może generować żadnych błędów. Oznacza to, że:

- Musi zawsze zwracać prawidłową wartość typu `type` .

- Musi obsługiwać wszystkie możliwe wyjątki i inne warunki błędu.

- Musi obsłużyć wszelkie błędy zwracane przez wszystkie procedury, które wywołuje.

Jeśli istnieje jakakolwiek możliwość, że procedura konwersji może zakończyć się niepowodzeniem lub może spowodować nieobsługiwany wyjątek, należy zadeklarować ją jako `Narrowing` .

## <a name="example"></a>Przykład

Poniższy przykład kodu używa `Operator` instrukcji do definiowania konspektu struktury, która zawiera procedury operatorów dla `And` `Or` operatorów,, `IsFalse` i `IsTrue` . `And`i `Or` każdy z nich przyjmuje dwa operandy typu `abc` i zwracanego typu `abc` . `IsFalse`i `IsTrue` każdy z nich przyjmuje jeden operand typu `abc` i Return `Boolean` . Te definicje umożliwiają wywołującemu kod użycie `And` , `AndAlso` , `Or` i `OrElse` z operandami typu `abc` .

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a>Zobacz też

- [IsFalse, operator](../operators/isfalse-operator.md)
- [IsTrue, operator](../operators/istrue-operator.md)
- [Widening](../modifiers/widening.md)
- [Narrowing](../modifiers/narrowing.md)
- [Rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md)
- [Instrukcje: definiowanie operatora](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Instrukcje: definiowanie operatora konwersji](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Instrukcje: wywoływanie procedury operatora](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [Instrukcje: używanie klasy definiującej operatory](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
