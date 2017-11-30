---
title: Konwersje tablic (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40dc9805157dd0bc991ca2375c3436aa6b6e09a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="array-conversions-visual-basic"></a>Konwersje tablic (Visual Basic)
Typem tablicy można przekonwertować na typ tablicy różnych pod warunkiem spełniać następujące warunki:  
  
-   **Ranga takie same.** Rangi dwóch tablic muszą być takie same, oznacza to, musi mieć taką samą liczbę wymiarów. Jednak nie długości odpowiednich wymiarów muszą być takie same.  
  
-   **Typ danych elementu.** Typy danych elementów zarówno tablic muszą być typy referencyjne. Nie można przekonwertować `Integer` tablicy do `Long` tablicy, a nawet z `Object` tablicy, ponieważ jest elementem typu co najmniej jedną wartość. Aby uzyskać więcej informacji, zobacz [typów wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Możliwości konwersji.** Konwersja, rozszerzanie albo zawężanie, musi być możliwe między typami elementu dwóch tablic. Przykładem, który zakończy się niepowodzeniem to wymaganie jest próba konwersji między `String` tablicy i Tablica klasę pochodną <xref:System.Attribute?displayProperty=nameWithType>. Te dwa typy mają one nic wspólnego, a nie dowolnego rodzaju istnieje konwersja między nimi.  
  
 Konwersja typu tablicy do innej rozszerzanie lub zawężanie w zależności od tego, czy rozszerzanie lub zawężanie konwersji odpowiednich elementów. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Konwersja na tablicę obiektów  
 Gdy zadeklarować `Object` tablica bez jego typem elementu inicjowania jest `Object` tak długo, jak pozostaje niezainicjowany. Po ustawieniu na tablicę określonej klasy przejmuje typ tej klasy. Jednak jego typ podstawowy jest nadal `Object`, i później może go ustawić na innej tablicy klasy niepowiązanych. Ponieważ wszystkie klasy pochodzi od `Object`, możesz zmienić typ elementu tablicy w dowolnej klasy do innej klasy.  
  
 W poniższym przykładzie, nie istnieje konwersja między typami `student` i `String`, ale jednocześnie pochodzi z `Object`, więc wszystkie przypisania są prawidłowe.  
  
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
 Jeśli pierwotnie zadeklarować tablicy o określonej klasy, jego typ podstawowy elementu jest tej klasy. Jeśli zostanie następnie ustawiona na tablicę innej klasy, musi być konwersji między dwiema klasami.  
  
 W poniższym przykładzie `students` jest `student` tablicy. Ponieważ nie istnieje konwersja między `String` i `student`, ostatniej instrukcji nie powiodło się.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Konwertowanie pomiędzy ciągami a innymi typami](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Porady: konwertowanie obiektu do innego typu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
