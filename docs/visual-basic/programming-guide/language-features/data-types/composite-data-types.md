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
ms.openlocfilehash: 73867a5881db7c94d258e8716c4ff4c5b1119e71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650442"
---
# <a name="composite-data-types-visual-basic"></a>Złożone typy danych (Visual Basic)
Oprócz dostaw Visual Basic typy podstawowe dane, można złożyć elementów różnego typu, aby utworzyć *złożone typy danych* takich jak klasy, tablic i struktury. Złożone typy danych można tworzyć z typów podstawowych i innych typów złożonych. Na przykład można zdefiniować tablicę elementów struktury lub struktura z tablicy elementów członkowskich.  
  
## <a name="data-types"></a>Typy danych  
 Typ złożony jest inny niż typ danych dowolnego z jego składników. Na przykład tablicę `Integer` nie ma elementów `Integer` typu danych.  
  
 Typ tablicy danych zwykle odpowiada za pomocą typu elementu, nawiasy i przecinkami w razie potrzeby. Na przykład tablicą jednowymiarową z `String` elementów jest reprezentowany jako `String()`i jest tablicą dwuwymiarową z `Boolean` elementów jest reprezentowany jako `Boolean(,)`.  
  
## <a name="structure-types"></a>Typy struktur  
 Nie ma typu danych jednego obejmujące wszystkie struktury. Zamiast tego każdej definicji struktury reprezentuje typ unikatowy danych, nawet jeśli dwie struktury zdefiniować identyczne elementy w tej samej kolejności. Jednak po utworzeniu co najmniej dwa wystąpienia tej samej struktury języka Visual Basic traktuje je tego samego typu danych.  
  
## <a name="tuples"></a>Krotki

Krotka jest strukturą lekkie, która zawiera dwa lub więcej pól, których typy są wstępnie zdefiniowane. Spójne kolekcje są obsługiwane w programie Visual Basic 2017 r. Spójne kolekcje są najczęściej używane do zwrócenia wiele wartości z wywołania metody pojedynczego bez konieczności przekazywać argumentów przez odwołanie lub pakowania zwrócony pól w bardziej ciężki klasy lub struktury. Zobacz [krotek](tuples.md) tematu, aby uzyskać więcej informacji na temat spójnych kolekcji.

## <a name="array-types"></a>Typy tablic  
 Nie ma typu danych jednego obejmujące wszystkie tablice. Typ danych konkretnego wystąpienia tablicy jest określany przez następujące czynności:  
  
-   Fakt trwa tablicy  
  
-   Rangą tablicy (liczba wymiarów)  
  
-   Typ elementu tablicy  
  
 W szczególności długość danego wymiaru nie jest częścią typ danych wystąpienia. Ilustruje to poniższy przykład.  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 W powyższym przykładzie tablicy zmienne `arrayA` i `arrayB` są uważane za tego samego typu danych — `Byte()` — nawet jeśli są one inicjowane różne długości. Zmienne `arrayB` i `arrayC` nie są tego samego typu, ponieważ ich typy elementów są różne. Zmienne `arrayC` i `arrayD` nie są tego samego typu, ponieważ różnią się ich rangi. Zmienne `arrayD` i `arrayE` mają ten sam typ — `Short(,)` — ponieważ ich rangi i typy elementu są takie same, nawet jeśli `arrayD` nie została jeszcze zainicjowana.  
  
 Aby uzyskać więcej informacji na tablice, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Typy klas  
 Nie ma typu danych jednego zawierający wszystkie klasy. Mimo że jednej klasy mogą dziedziczyć z innej klasy, każdy jest typem danych. Wiele wystąpień tej samej klasy są tego samego typu danych. Po przypisaniu co zmienna wystąpienia klasy do innego, nie tylko mają ten sam typ danych, wskazywać tego samego wystąpienia klasy w pamięci.  
  
 Aby uzyskać więcej informacji na temat klas, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Instrukcje: utrzymywanie więcej niż jednej wartości w zmiennej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
