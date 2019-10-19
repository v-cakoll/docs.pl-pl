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
ms.openlocfilehash: 475f3f5357f7c989a30ca9e6c5d32b8cc989436f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581861"
---
# <a name="array-conversions-visual-basic"></a>Konwersje tablic (Visual Basic)
Typ tablicy można skonwertować na inny typ tablicy, pod warunkiem, że są spełnione następujące warunki:  
  
- **Równa ranga.** Range dwóch tablic muszą być takie same, co oznacza, że muszą mieć taką samą liczbę wymiarów. Jednak długości odpowiednich wymiarów nie muszą być takie same.  
  
- **Typ danych elementu.** Typy danych elementów obu tablic muszą być typami referencyjnymi. Nie można przekonwertować tablicy `Integer` na tablicę `Long` lub nawet do tablicy `Object`, ponieważ jest uwzględniany co najmniej jeden typ wartości. Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
- **Convertibility.** Konwersja, rozszerzająca lub zawężania, musi być możliwa między typami elementów dwóch tablic. Przykładem niepowodzenia tego wymagania jest próba konwersji między tablicą `String` i tablicą klasy pochodnej <xref:System.Attribute?displayProperty=nameWithType>. Te dwa typy nie mają wspólnych wartości i nie istnieje konwersja żadnego rodzaju między nimi.  
  
 Konwersja jednego typu tablicy na inny jest poszerzana lub zawężana w zależności od tego, czy konwersja odpowiednich elementów jest poszerzana czy zawężana. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Konwersja na tablicę obiektów  
 Gdy deklarujesz tablicę `Object` bez jej inicjalizacji, jej typ elementu jest `Object`, dopóki nie zostanie zainicjowany. Gdy ustawiasz ją na tablicę określonej klasy, przyjmuje ona typ tej klasy. Jednak jego typ podstawowy jest nadal `Object` i można następnie ustawić go na inną tablicę niepowiązanej klasy. Ponieważ wszystkie klasy pochodzą z `Object`, można zmienić typ elementu tablicy z dowolnej klasy na dowolną inną klasę.  
  
 W poniższym przykładzie nie istnieje konwersja między typami `student` i `String`, ale oba pochodzą z `Object`, więc wszystkie przypisania są prawidłowe.  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>Typ podstawowy tablicy  
 Jeśli pierwotnie deklarujesz tablicę z określoną klasą, jej typem elementu podstawowego jest Klasa. Jeśli następnie ustawisz ją na tablicę innej klasy, musi istnieć konwersja między tymi dwiema klasami.  
  
 W poniższym przykładzie `students` jest tablicą `student`. Ponieważ nie istnieje żadna konwersja między `String` i `student`, Ostatnia instrukcja kończy się niepowodzeniem.  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Konwersje typów w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Konwertowanie między ciągami a innymi typami danych](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Instrukcje: konwertowanie obiektu na inny typ w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
