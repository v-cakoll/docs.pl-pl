---
title: "Operator — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.operator
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
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b6be45fd0a606f43c14d57f3f8ae0955f256ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 Opcjonalny. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Wymagany. Wskazuje, że ta procedura operator ma [publicznego](../../../visual-basic/language-reference/modifiers/public.md) dostępu.  
  
 `Overloads`  
 Opcjonalny. Zobacz [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Wymagany. Oznacza, że ta procedura operator [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedury.  
  
 `Shadows`  
 Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Wymagany dla operatora konwersji, chyba że zostanie `Narrowing`. Wskazuje, że ta procedura operator definiuje [Widening](../../../visual-basic/language-reference/modifiers/widening.md) konwersji. Na tej stronie pomocy, zobacz "Rozszerzanie i zwężanie konwersji".  
  
 `Narrowing`  
 Wymagany dla operatora konwersji, chyba że zostanie `Widening`. Wskazuje, że ta procedura operator definiuje [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) konwersji. Na tej stronie pomocy, zobacz "Rozszerzanie i zwężanie konwersji".  
  
 `operatorsymbol`  
 Wymagany. Symbol lub identyfikator operator, który definiuje tę procedurę operatora.  
  
 `operand1`  
 Wymagany. Nazwa i typ pojedynczy argument operacji operatora jednoargumentowego (w tym operatora konwersji) lub lewy argument operacji operatora binarnego.  
  
 `operand2`  
 Wymagany w przypadku operatorów binarnych. Nazwa i typ prawy argument operacji operatora binarnego.  
  
 `operand1`i `operand2` mają następujące składni i części:  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Część|Opis|  
|----------|-----------------|  
|`ByVal`|Opcjonalne, ale mechanizm przekazywania musi być [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Wymagany. Nazwa zmiennej reprezentujący ten argument operacji. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|Opcjonalne chyba że `Option Strict` jest `On`. Typ danych tego argumentu.|  
  
 `type`  
 Opcjonalne chyba że `Option Strict` jest `On`. Zwraca typ danych wartości procedury operatora.  
  
 `statements`  
 Opcjonalny. Blok instrukcji, które są wykonywane procedury operatora.  
  
 `returnvalue`  
 Wymagany. Wartość, która zwraca procedury operatora do wywołującego kodu.  
  
 `End``Operator`  
 Wymagany. Kończy definicję tej procedury operatora.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `Operator` tylko w klasie lub strukturze. Oznacza to, że *kontekście deklaracji* operator nie może być plik źródłowy, przestrzeni nazw, modułu, interfejsu, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Wszystkie operatory musi być `Public Shared`. Nie można określić `ByRef`, `Optional`, lub `ParamArray` dla którykolwiek argument operacji.  
  
 Symbol operatora lub identyfikatora nie można używać do przechowywania wartości zwracanej. Należy użyć `Return` instrukcji, a musi określać wartość. Dowolną liczbę `Return` instrukcje mogą występować w dowolnym miejscu w procedurze.  
  
 Definiowanie operatora w ten sposób jest nazywany *przeładowania operatora*, czy używasz `Overloads` — słowo kluczowe. W poniższej tabeli wymieniono operatory, których można zdefiniować.  
  
|Typ|Operatory|  
|----------|---------------|  
|Jednoargumentowe|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|plików binarnych|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Konwersja (jednoargumentowy)|`CType`|  
  
 Należy pamiętać, że `=` operator porównania nie operator przypisania jest operator binarny listy.  
  
 Podczas definiowania `CType`, należy określić `Widening` lub `Narrowing`.  
  
## <a name="matched-pairs"></a>Dopasowane pary  
 Należy zdefiniować operatorów jako dopasowane pary. W przypadku definiowania albo operator takich parze, należy zdefiniować innych również. Dopasowane pary są następujące:  
  
-   `=`i`<>`  
  
-   `>`i`<`  
  
-   `>=`i`<=`  
  
-   `IsTrue`i`IsFalse`  
  
## <a name="data-type-restrictions"></a>Ograniczenia dotyczące typu danych  
 Co należy zdefiniować operator musi obejmować klasy lub struktury, w którym można zdefiniować. Oznacza to, że klasy lub struktury musi występować jako typ danych z następujących czynności:  
  
-   Argument operacji operatora jednoargumentowego.  
  
-   Co najmniej jeden z argumentów operatora binarnego.  
  
-   Argument operacji lub typ zwracany operatora konwersji.  
  
 Operatorów mają dodatkowe dane typu ograniczenia, w następujący sposób:  
  
-   W przypadku definiowania `IsTrue` i `IsFalse` operatorów, muszą one zarówno zwracać `Boolean` typu.  
  
-   W przypadku definiowania `<<` i `>>` operatorów, ich trzeba określić `Integer` wpisz `operandtype` z `operand2`.  
  
 Zwracany typ nie musi odpowiadać typowi którykolwiek argument operacji. Na przykład operator porównania takich jak `=` lub `<>` może zwrócić `Boolean` nawet, jeśli żaden argument operacji jest `Boolean`.  
  
## <a name="logical-and-bitwise-operators"></a>Operatory logiczne i bitowe  
 `And`, `Or`, `Not`, I `Xor` operatorzy mogą wykonywać operacje logicznych lub bitowe w Visual Basic. Jednak jeśli jeden z tych operatorów zdefiniowanej dla klasy lub struktury, można zdefiniować tylko jego operacji.  
  
 Nie można zdefiniować `AndAlso` operator bezpośrednio z `Operator` instrukcji. Można jednak użyć `AndAlso` czy zostały spełnione następujące warunki:  
  
-   Zdefiniowano `And` na ten sam typ argumentu ma być używany dla `AndAlso`.  
  
-   Definicja `And` zwraca ten sam typ co klasy lub struktury, w którym zdefiniowano go.  
  
-   Zdefiniowano `IsFalse` operatora dla klasy lub struktury, w którym zdefiniowano `And`.  
  
 Analogicznie, można użyć `OrElse` Jeśli zdefiniowano `Or` na tej samej operandy ze zwracanym typem klasy lub struktury, a zdefiniowane `IsTrue` dla klasy lub struktury.  
  
## <a name="widening-and-narrowing-conversions"></a>Rozszerzanie i zwężanie konwersji  
 A *rozszerzanie konwersji* zawsze zakończy się pomyślnie w czasie wykonywania, gdy *konwersja zawężająca* może zakończyć się niepowodzeniem w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 W przypadku procedury konwersji za `Widening`, kod procedury należy wygenerować nie zakończą się niepowodzeniem. Oznacza to następujące czynności:  
  
-   Musi ona zawsze zwrócić wartość prawidłowego typu `type`.  
  
-   Go musi obsługiwać wszystkich możliwych wyjątków i innych błędów.  
  
-   Go musi obsługiwać żadnych zwraca błąd z procedury wywoływanych przez nią.  
  
 Jeśli brak możliwości, które procedury Konwersja może się nie powieść lub że może spowodować, że wystąpił nieobsługiwany wyjątek, muszą deklarować się `Narrowing`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Operator` instrukcji do zdefiniowania konturu struktura, która zawiera operator procedury dotyczące `And`, `Or`, `IsFalse`, i `IsTrue` operatorów. `And`i `Or` każdego dwóch operandach typu `abc` i typ zwracany `abc`. `IsFalse`i `IsTrue` każdego wykonać jeden operand typu `abc` i zwracać `Boolean`. Zezwalaj na te definicje kod wywołujący, aby użyć `And`, `AndAlso`, `Or`, i `OrElse` z argumentów operacji typu `abc`.  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [IsFalse — Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [IsTrue — Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Rozszerzanie](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Zawężanie](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Porady: Definiowanie operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Porady: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Porady: wywoływanie procedury operatora](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [Porady: używanie klasy definiującej operatory](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
