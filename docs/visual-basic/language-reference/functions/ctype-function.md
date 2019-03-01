---
title: CType — Funkcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 8f60edb2b5e2dba15526169ef10bc05c1f50a7f1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970015"
---
# <a name="ctype-function-visual-basic"></a>CType — Funkcja (Visual Basic)
Zwraca wynik jawnej konwersji wyrażenia do określonego typu danych, obiektu, struktury, klasy lub interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a>Części  
 `expression`  
 Dowolne prawidłowe wyrażenie. Jeśli wartość `expression` znajduje się poza zakresem dozwolonym przez `typename`, Visual Basic zgłasza wyjątek.  
  
 `typename`  
 Dowolne wyrażenie, które jest dozwolony w `As` w klauzuli `Dim` instrukcji, oznacza to, że nazwa dowolnego typu danych, obiektu, struktury, klasy lub interfejsu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!TIP]
>  Aby przeprowadzić konwersję typu umożliwia także następujące funkcje:  
>   
>  -   Funkcje konwersji typu, takie jak `CByte`, `CDbl`, i `CInt` które wykonują konwersję na określony typ danych. Aby uzyskać więcej informacji, zobacz [funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md). Operatorzy Ci wymagają, że jeden typ dziedziczył lub implementował innego typu. Zapewniają lepszą wydajność niż `CType` podczas konwersji do i z `Object` typu danych.  
  
 `CType` jest skompilowany w tekście, co oznacza, że kod konwersji jest częścią kodu, który oblicza wyrażenie. W niektórych przypadkach kod działa szybciej ponieważ procedury nie są wywoływane w celu wykonania konwersji.  
  
 Jeśli konwersja nie jest zdefiniowana z `expression` do `typename` (na przykład z `Integer` do `Date`), Visual Basic wyświetli komunikat o błędzie kompilacji.  
  
 Jeśli konwersja nie powiedzie się w czasie wykonywania, zgłoszony odpowiedni wyjątek. W przypadku niepowodzenia konwersji zawężającej <xref:System.OverflowException> jest najczęstszym rezultatem. Jeśli konwersja jest niezdefiniowana, <xref:System.InvalidCastException> zgłoszone. Na przykład przyczyną może być `expression` typu `Object` i jego typu run-time nie ma konwersji do `typename`.  
  
 Jeśli typ danych `expression` lub `typename` jest klasy lub struktury zdefiniowany przez użytkownika, można zdefiniować `CType` dla tej klasy lub struktury jako operatora konwersji. To sprawia, że `CType` pełnić rolę *Przeciążony operator*. Jeśli to zrobisz, możesz kontrolować zachowanie podczas konwersji do i od klasy lub struktury, łącznie z wyjątkami, które mogą zostać zgłoszone.  
  
## <a name="overloading"></a>Przeciążenie  
 `CType` Operator może również być przeciążony na klasę lub strukturę zdefiniowaną poza kodem. Jeśli Twój kod konwertuje do lub z takiej klasy lub struktury, należy zrozumieć zachowanie jego `CType` operatora. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="converting-dynamic-objects"></a>Konwertowanie obiektów dynamicznych  
 Konwersje typów obiektów dynamicznych są wykonywane przez zdefiniowane przez użytkownika dynamiczne konwersje, które używają <xref:System.Dynamic.DynamicObject.TryConvert%2A> lub <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody. Jeśli pracujesz z obiektami dynamicznymi, użyj <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metodę, aby przekonwertować obiekt dynamiczny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `CType` funkcji konwersji wyrażenia `Single` typu danych.  
  
 [!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]  
  
 Aby uzyskać więcej przykładów, zobacz [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Funkcje konwersji](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrukcje: Definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Konwersja typów w programie .NET Framework](../../../standard/base-types/type-conversion.md)
