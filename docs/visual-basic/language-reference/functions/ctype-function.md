---
title: "CType — Funkcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d804ce75929592675068fdc434a1ba7429fa5373
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ctype-function-visual-basic"></a>CType — Funkcja (Visual Basic)
Zwraca wynik jawnej konwersji wyrażenia do określonego typu danych, obiektu, struktury, klasy lub interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a>Części  
 `expression`  
 Dowolne prawidłowe wyrażenie. Jeśli wartość `expression` znajduje się poza zakresem dozwolone przez `typename`, Visual Basic zgłasza wyjątek.  
  
 `typename`  
 Dowolne wyrażenie, które jest dozwolony w `As` w klauzuli `Dim` instrukcji, oznacza to, że nazwa dowolnego typu danych, obiektu, struktury, klasy lub interfejsu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!TIP]
>  Aby dokonać konwersji typu można także użyć następujących funkcji:  
>   
>  -   Funkcje konwersji wpisz na przykład `CByte`, `CDbl`, i `CInt` który wykonania konwersji na typ danych. Aby uzyskać więcej informacji, zobacz [funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md). Operatory te wymagają, że jeden typ dziedziczył lub implementował z innego typu. Udostępniają one nieco większą wydajność niż `CType` podczas konwersji do i z `Object` — typ danych.  
  
 `CType`jest skompilowany w tekście, co oznacza, że kod konwersji jest częścią kodu, który wylicza wartość wyrażenia. W niektórych przypadkach kod działa szybciej, ponieważ nie procedur są wywoływane w celu wykonania konwersji.  
  
 Jeśli zdefiniowano brak konwersji z `expression` do `typename` (na przykład z `Integer` do `Date`), Visual Basic wyświetla komunikat o błędzie kompilacji.  
  
 W przypadku niepowodzenia konwersji w czasie wykonywania odpowiednich wyjątku. W przypadku niepowodzenia konwersji zawężającej <xref:System.OverflowException> powstaje na podstawie najczęściej. Jeśli zdefiniowano konwersji <xref:System.InvalidCastException> w zgłoszony. Na przykład, to może nastąpić, jeśli `expression` jest typu `Object` i jej typ środowiska wykonawczego nie ma brak konwersji na `typename`.  
  
 Jeśli typ danych miary `expression` lub `typename` jest klasy lub struktury, zdefiniowany przez użytkownika, można zdefiniować `CType` dla tej klasy lub struktury jako operatora konwersji. Dzięki temu `CType` pełnienie *Przeciążony operator*. Jeśli to zrobisz, można kontrolować zachowanie konwersje do i z klasy lub struktury, w tym wyjątki, które mogą być generowane.  
  
## <a name="overloading"></a>Przeciążenie  
 `CType` Również można przeciążać operatora dla klasy lub struktury zdefiniowane poza swój kod. Jeśli kod konwertuje do lub z klasy lub struktury, trzeba koniecznie zapoznać się z zachowaniem jego `CType` operatora. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="converting-dynamic-objects"></a>Konwertowanie obiekty dynamiczne  
 Konwersje typów obiektów dynamicznych są wykonywane przez zdefiniowane przez użytkownika konwersje dynamicznych, korzystających z <xref:System.Dynamic.DynamicObject.TryConvert%2A> lub <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody. Jeśli pracujesz z obiektami dynamicznymi, użyj <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metodę, aby przekonwertować obiekt dynamiczny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `CType` funkcji konwersji wyrażenia do `Single` — typ danych.  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 Aby uzyskać dodatkowe przykłady, zobacz [Konwersje jawne i niejawne](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Funkcje konwersji](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Instrukcje: definiowanie operatora konwersji](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Konwersja typów w programie .NET Framework](../../../standard/base-types/type-conversion.md)
