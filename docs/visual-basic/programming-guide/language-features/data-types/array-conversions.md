---
title: Konwersje tablic
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
ms.openlocfilehash: 1d20b01200d3f967e3355dc6e9651291003d140e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402008"
---
# <a name="array-conversions-visual-basic"></a>Konwersje tablic (Visual Basic)
Typ tablicy można skonwertować na inny typ tablicy, pod warunkiem, że są spełnione następujące warunki:  
  
- **Równa ranga.** Range dwóch tablic muszą być takie same, co oznacza, że muszą mieć taką samą liczbę wymiarów. Jednak długości odpowiednich wymiarów nie muszą być takie same.  
  
- **Typ danych elementu.** Typy danych elementów obu tablic muszą być typami referencyjnymi. Nie można przekonwertować `Integer` tablicy na `Long` tablicę, a nawet do `Object` tablicy, ponieważ występuje co najmniej jeden typ wartości. Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](value-types-and-reference-types.md).  
  
- **Convertibility.** Konwersja, rozszerzająca lub zawężania, musi być możliwa między typami elementów dwóch tablic. Przykładem, że niepowodzenie tego wymagania jest próba konwersji między `String` tablicą a tablicą klasy pochodnej <xref:System.Attribute?displayProperty=nameWithType> . Te dwa typy nie mają wspólnych wartości i nie istnieje konwersja żadnego rodzaju między nimi.  
  
 Konwersja jednego typu tablicy na inny jest poszerzana lub zawężana w zależności od tego, czy konwersja odpowiednich elementów jest poszerzana czy zawężana. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Konwersja na tablicę obiektów  
 Po zadeklarowaniu `Object` tablicy bez jej inicjalizacji jej typ elementu jest `Object` tak długo, jak pozostaje niezainicjowany. Gdy ustawiasz ją na tablicę określonej klasy, przyjmuje ona typ tej klasy. Jednak jego typ podstawowy jest nadal `Object` , a następnie można ustawić go na inną tablicę niepowiązanej klasy. Ponieważ wszystkie klasy pochodzą z `Object` , można zmienić typ elementu tablicy z dowolnej klasy na dowolną inną klasę.  
  
 W poniższym przykładzie nie istnieje żadna konwersja między typami `student` i `String` , ale obie wartości pochodzą od `Object` , więc wszystkie przypisania są prawidłowe.  
  
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
  
 W poniższym przykładzie `students` jest `student` tablicą. Ponieważ nie istnieje konwersja między `String` i `student` , Ostatnia instrukcja kończy się niepowodzeniem.  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](index.md)
- [Konwersje plików w Visual Basic](type-conversions.md)
- [Konwersje jawne i niejawne](implicit-and-explicit-conversions.md)
- [Konwertowanie między ciągami a innymi typami danych](conversions-between-strings-and-other-types.md)
- [Porady: konwertowanie obiektu do innego typu w Visual Basic](how-to-convert-an-object-to-another-type.md)
- [Typy danych](../../../language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../language-reference/functions/type-conversion-functions.md)
- [Tablice](../arrays/index.md)
