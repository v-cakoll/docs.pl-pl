---
title: Operator — instrukcja (Visual Basic)
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
ms.openlocfilehash: 69dea99cf71bd1e091116e54e244abfca291ffdb
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481978"
---
# <a name="operator-statement"></a>Operator — Instrukcja
Deklaruje symbol operatora, argumenty operacji i kod, który definiuje procedurę operatora w klasie lub strukturze.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Wymagane. Wskazuje, że ta procedura operator ma [publicznych](../../../visual-basic/language-reference/modifiers/public.md) dostępu.  
  
 `Overloads`  
 Opcjonalna. Zobacz [przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Wymagane. Wskazuje, że ta procedura operator [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedury.  
  
 `Shadows`  
 Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Wymagane dla operatora konwersji, chyba że określisz `Narrowing`. Wskazuje, że ta procedura operator definiuje [Widening](../../../visual-basic/language-reference/modifiers/widening.md) konwersji. Zobacz "Rozszerzające i zawężające konwersje" na tej stronie pomocy.  
  
 `Narrowing`  
 Wymagane dla operatora konwersji, chyba że określisz `Widening`. Wskazuje, że ta procedura operator definiuje [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) konwersji. Zobacz "Rozszerzające i zawężające konwersje" na tej stronie pomocy.  
  
 `operatorsymbol`  
 Wymagane. Symbol lub identyfikator operator, który definiuje tę procedurę operatora.  
  
 `operand1`  
 Wymagane. Nazwa i typ jeden argument operacji operatora jednoargumentowego (w tym operatora konwersji) lub lewy operand operatora binarnego.  
  
 `operand2`  
 Wymagane dla operatorów binarnych. Nazwa i typ prawy operand operatora binarnego.  
  
 `operand1` i `operand2` poniższej składni i części:  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Część|Opis|  
|----------|-----------------|  
|`ByVal`|Opcjonalne, ale mechanizm przekazywania musi być [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Wymagane. Nazwa zmiennej, reprezentujący ten argument operacji. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|Opcjonalne chyba że `Option Strict` jest `On`. Typ danych ten argument operacji.|  
  
 `type`  
 Opcjonalne chyba że `Option Strict` jest `On`. Zwraca typ danych wartości procedury operatora.  
  
 `statements`  
 Opcjonalna. Blok instrukcji, które są wykonywane procedury operatora.  
  
 `returnvalue`  
 Wymagane. Wartość, która procedura operator zwraca do wywołującego kodu.  
  
 `End``Operator`  
 Wymagane. Kończy definicję tej procedury operatora.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `Operator` tylko w klasie lub strukturze. Oznacza to, że *kontekst deklaracji* operator nie może być plik źródłowy, przestrzeni nazw, moduł, interfejsu, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Wszystkie operatory muszą być `Public Shared`. Nie można określić `ByRef`, `Optional`, lub `ParamArray` na jeden z operandów.  
  
 Symbol operatora lub identyfikatora nie można użyć do przechowywania wartości zwracanej. Należy użyć `Return` instrukcji i należy określić wartość. Dowolną liczbę `Return` instrukcji może występować w dowolnym miejscu w procedurze.  
  
 Definiowanie operatora w ten sposób jest nazywany *przeciążania operatorów*, czy używasz `Overloads` — słowo kluczowe. W poniższej tabeli wymieniono operatory, które można zdefiniować.  
  
|Typ|Operatory|  
|----------|---------------|  
|Jednoargumentowy|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|plików binarnych|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Konwersja (jednoargumentowy)|`CType`|  
  
 Należy pamiętać, że `=` operator binarny listy jest operator porównania nie operator przypisania.  
  
 Podczas definiowania `CType`, należy określić `Widening` lub `Narrowing`.  
  
## <a name="matched-pairs"></a>Dopasowane pary  
 Należy zdefiniować jako dopasowane pary niektórych operatorów. Jeśli zdefiniujesz albo operator takich pary, należy zdefiniować innych także. Dopasowane pary są następujące:  
  
-   `=` i `<>`  
  
-   `>` i `<`  
  
-   `>=` i `<=`  
  
-   `IsTrue` i `IsFalse`  
  
## <a name="data-type-restrictions"></a>Ograniczenia dotyczące typu danych  
 Każdy operator, który zdefiniujesz muszą obejmować klasy lub struktury, w którym można zdefiniować. Oznacza to, że klasa lub struktura musi znajdować się w formie typu danych z następujących czynności:  
  
-   Argument operacji operatora jednoargumentowego.  
  
-   Co najmniej jeden z operandów operatora binarnego.  
  
-   Argument lub zwracany typ operatora konwersji.  
  
 Niektóre operatory mają dodatkowe dane, wpisz następujące ograniczenia:  
  
-   Jeśli zdefiniujesz `IsTrue` i `IsFalse` operatorów, muszą one zarówno zwracać `Boolean` typu.  
  
-   Jeśli zdefiniujesz `<<` i `>>` operatorów, muszą oni zarówno określić `Integer` wpisz `operandtype` z `operand2`.  
  
 Zwracany typ nie musi odpowiadać typowi jeden z operandów. Na przykład operator porównania takich jak `=` lub `<>` może zwrócić `Boolean` nawet jeśli żaden z operandów jest `Boolean`.  
  
## <a name="logical-and-bitwise-operators"></a>Operatory logiczne i bitowe  
 `And`, `Or`, `Not`, I `Xor` operatorzy mogą wykonywać operacji logicznych lub bitowe w Visual Basic. Jednak jeśli zdefiniujesz jednego z tych operatorów dla klasy lub struktury, można zdefiniować tylko jego operacji na poziomie bitowym.  
  
 Nie można zdefiniować `AndAlso` operator bezpośrednio z `Operator` instrukcji. Można jednak użyć `AndAlso` jeśli zostały spełnione następujące warunki:  
  
-   Zdefiniowano `And` na te same typy operand, którego chcesz użyć dla `AndAlso`.  
  
-   Definicja `And` zwraca ten sam typ co klasa lub struktura, w którym zdefiniowano go.  
  
-   Zdefiniowano `IsFalse` operator dla klasy lub struktury, w którym zdefiniowano `And`.  
  
 Podobnie, można użyć `OrElse` Jeżeli posiadasz zdefiniowane `Or` na tych samych argumentów o zwracanym typie krawędzi klasy lub struktury, a zdefiniowano `IsTrue` dla klasy lub struktury.  
  
## <a name="widening-and-narrowing-conversions"></a>Rozszerzanie i zwężanie konwersji  
 A *poszerzenie konwersji* zawsze zakończy się pomyślnie w czasie wykonywania, podczas gdy *konwersja zawężająca* może zakończyć się niepowodzeniem w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Jeśli zadeklarujesz procedury konwersji za `Widening`, kod procedury nie należy wygenerować zakończą się niepowodzeniem. Oznacza to, że:  
  
-   Zawsze musi zwracać prawidłowe wartości typu `type`.  
  
-   Musi on obsługiwać wszystkich możliwych wyjątków i inne warunki błędu.  
  
-   Jego musi obsługiwać żadnych zwraca błąd z procedury wywoływanych przez nią.  
  
 Jeśli ma żadnych możliwość, że procedura Konwersja może się nie powieść lub jej może spowodować, że nieobsługiwany wyjątek, należy zadeklarować ją jako `Narrowing`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Operator` instrukcję w celu zdefiniowania konturu to struktura, która zawiera procedury operatora `And`, `Or`, `IsFalse`, i `IsTrue` operatorów. `And` i `Or` uwzględniać dwóch argumentów operacji typu `abc` i zwracany typ `abc`. `IsFalse` i `IsTrue` uwzględniać jeden argument operacji typu `abc` i zwracają `Boolean`. Te definicje Zezwalaj na kod wywołujący, aby użyć `And`, `AndAlso`, `Or`, i `OrElse` z argumentów operacji typu `abc`.  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [IsFalse, operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Instrukcje: definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Instrukcje: definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Instrukcje: wywoływanie procedury operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [Instrukcje: używanie klasy definiującej operatory](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
