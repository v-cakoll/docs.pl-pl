---
title: Złożone typy danych (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: c7243108d0b7c06f48a21f343321322bb2cc2946
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560285"
---
# <a name="composite-data-types-visual-basic"></a>Złożone typy danych (Visual Basic)
Oprócz danych podstawowych typów języka Visual Basic dostaw, również można grupować elementy o różnych typach, aby utworzyć *złożone typy danych* takich jak klasy, tablic i struktur. Możesz tworzyć złożone typy danych, z typów podstawowych i z innych typów złożonych. Na przykład można zdefiniować tablicę elementy struktury lub struktury z tablicy elementów członkowskich.  
  
## <a name="data-types"></a>Typy danych  
 Typ złożony różni się od typu danych żadnej z jej składników. Na przykład tablica `Integer` nie ma elementów `Integer` typu danych.  
  
 Typ danych tablicy jest zwykle reprezentowany za pomocą typu elementu, nawiasy i przecinki, zgodnie z potrzebami. Na przykład Jednowymiarowa tablica `String` elementy są reprezentowane jako `String()`i dwuwymiarową tablicę `Boolean` elementy są reprezentowane jako `Boolean(,)`.  
  
## <a name="structure-types"></a>Typy struktur  
 Nie ma żadnych single — typ danych obejmujące wszystkie struktury. Zamiast tego każda definicja struktury reprezentuje typ unikatowe dane, nawet wtedy, gdy dwie struktury zdefiniować identyczne elementy w tej samej kolejności. Jednak jeśli tworzysz tę samą strukturę co najmniej dwóch wystąpień, Visual Basic traktuje je tego samego typu danych.  
  
## <a name="tuples"></a>Krotki

Spójna Kolekcja to lekki strukturę, która zawiera dwa lub więcej pól, których typy są wstępnie zdefiniowane. Spójne kolekcje są obsługiwane, począwszy od programu Visual Basic w 2017 r. Kolekcje są najczęściej używane zwracanie wielu wartości w pojedynczym wywołaniu metody bez konieczności przekazywać argumentów przez odwołanie lub spakowanie zwracanego pola w bardziej ciężki klasy lub struktury. Zobacz [krotek](tuples.md) tematu, aby uzyskać więcej informacji na temat krotek.

## <a name="array-types"></a>Typy tablic  
 Nie ma żadnych single — typ danych wchodzących w skład wszystkich tablic. Typ danych konkretnego wystąpienia tablicy jest określana przez następujące elementy:  
  
-   Fakt jest tablicą  
  
-   Ranga tablicy (liczba wymiarów)  
  
-   Typ elementu tablicy  
  
 W szczególności długość danego wymiaru nie jest częścią typu danych wystąpienia. Ilustruje to poniższy przykład.  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 W poprzednim przykładzie, tablica zmienne `arrayA` i `arrayB` są traktowane jako typu danych — `Byte()` — nawet jeśli są one inicjowane na różne długości. Zmienne `arrayB` i `arrayC` nie są tego samego typu, ponieważ ich typy elementów są różne. Zmienne `arrayC` i `arrayD` nie są tego samego typu, ponieważ różnią się ich rangę. Zmienne `arrayD` i `arrayE` mieć taki sam typ — `Short(,)` — ponieważ ich rangę i typów elementów są takie same, nawet jeśli `arrayD` nie została jeszcze zainicjowana.  
  
 Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Typy klas  
 Nie ma żadnych single — typ danych wchodzących w skład wszystkich klas. Mimo że jednej klasy mogą dziedziczyć z innej klasy, każdy jest typem osobne dane. Wiele wystąpień tej samej klasy są tego samego typu danych. Jeśli przypiszesz jednej zmiennej wystąpienia klasy do innego nie tylko mają ten sam typ danych, wskazują na tym samym wystąpieniu klasy w pamięci.  
  
 Aby uzyskać więcej informacji na temat klas, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Zobacz także
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Instrukcje: utrzymywanie więcej niż jednej wartości w zmiennej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
