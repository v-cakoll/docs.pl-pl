---
title: Konwersje tablic (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 88002e2c099ed9503beddb190d243aadcc1087fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830204"
---
# <a name="array-conversions-visual-basic"></a>Konwersje tablic (Visual Basic)
Typ tablicy można przekonwertować na typ innej tablicy, pod warunkiem spełnienia następujących warunków:  
  
-   **Ranga równe.** Rangę dwie tablice muszą być takie same, oznacza to, musi mieć taką samą liczbę wymiarów. Jednak nie długości wymiarów odpowiedniej muszą być takie same.  
  
-   **Typ danych elementu.** Typy danych elementów obu tablicach muszą być typami odwołań. Nie można przekonwertować `Integer` tablicy do `Long` tablicy, a nawet z `Object` tablicy, ponieważ uczestniczy typ co najmniej jedną wartość. Aby uzyskać więcej informacji, zobacz [typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Przetwarzania.** Konwersja, albo zwężająca lub poszerzająca, musi być możliwe między typami elementu dwóch tablic. Przykładem, który zakończy się niepowodzeniem to wymaganie jest próba konwersji między `String` tablicy i tablicę klasę pochodną <xref:System.Attribute?displayProperty=nameWithType>. Te dwa typy wspólnym nic i bez konwersji dowolnego rodzaju istnieje między nimi.  
  
 Konwersja typu tablicy do innej jest zwężająca lub poszerzająca w zależności od tego, czy zwężająca lub poszerzająca konwersji odpowiednich elementów. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Konwersja na tablicę obiektów  
 Kiedy Deklarujesz `Object` jest niedostępna, inicjując go, jego typ elementu `Object` tak długo, jak długo pozostaje niezainicjowany. Po ustawieniu do tablicy w określonej klasy, zajmuje się od typu tej klasy. Jego typ podstawowy jest jednak nadal `Object`, a następnie można ustawić go do innej tablicy niepowiązanych klasy. Ponieważ wszystkie klasy pochodzić od `Object`, typ elementu tablicy można zmienić z dowolnej klasy, na innych klas.  
  
 W poniższym przykładzie nie istnieje konwersja między typami `student` i `String`, ale obie pochodzi z `Object`, więc wszystkie przypisania są prawidłowe.  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>Typ podstawowy elementu tablicy  
 Jeśli początkowo jest zadeklarowanie tablicy z konkretną klasą, jej typ podstawowy elementu jest tej klasy. Jeśli następnie ustawisz go jako tablicę innej klasy, musi być konwersji między dwoma klasami.  
  
 W poniższym przykładzie `students` jest `student` tablicy. Ponieważ nie istnieje konwersja między `String` i `student`, ostatniej instrukcji nie powiodło się.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Konwertowanie między ciągami a innymi typami danych](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
