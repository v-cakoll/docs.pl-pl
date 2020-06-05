---
title: Złożone typy danych
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
ms.openlocfilehash: 3e8df5ccfeca4bc0a19237ba6d59e9d0747080ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394301"
---
# <a name="composite-data-types-visual-basic"></a>Złożone typy danych (Visual Basic)
Oprócz podstawowych typów danych Visual Basic dostaw, można także złożyć elementy różnych typów w celu utworzenia *złożonych typów danych* , takich jak struktury, tablice i klasy. Można tworzyć złożone typy danych z typów podstawowych i z innych typów złożonych. Na przykład można zdefiniować tablicę elementów struktury lub strukturę z elementami członkowskimi tablicy.  
  
## <a name="data-types"></a>Typy danych  
 Typ złożony różni się od typu danych któregokolwiek z jego składników. Na przykład tablica `Integer` elementów nie jest `Integer` typu danych.  
  
 Typ danych tablicy jest zwykle reprezentowany przy użyciu typu elementu, nawiasów i przecinków w razie potrzeby. Na przykład Jednowymiarowa tablica `String` elementów jest reprezentowana jako `String()` , a Dwuwymiarowa tablica `Boolean` elementów jest reprezentowana jako `Boolean(,)` .  
  
## <a name="structure-types"></a>Typy struktur  
 Nie istnieje pojedynczy typ danych obejmujący wszystkie struktury. Zamiast tego każda definicja struktury reprezentuje unikatowy typ danych, nawet jeśli dwie struktury definiują identyczne elementy w tej samej kolejności. Jeśli jednak tworzysz dwa lub więcej wystąpień tej samej struktury, Visual Basic uznaje ich za tego samego typu danych.  
  
## <a name="tuples"></a>Krotki

Krotka jest strukturą uproszczoną, która zawiera co najmniej dwa pola, których typy są wstępnie zdefiniowane. Krotki są obsługiwane począwszy od Visual Basic 2017. Krotki są najczęściej używane do zwracania wielu wartości z pojedynczej metody wywołania bez konieczności przekazywania argumentów przez odwołanie lub pakowanie zwracanych pól w bardziej ciężkich klasach lub strukturach. Aby uzyskać więcej informacji na temat krotek, zobacz temat [krotki](tuples.md) .

## <a name="array-types"></a>Typy tablic  
 Nie istnieje pojedynczy typ danych składający się ze wszystkich tablic. Typ danych określonego wystąpienia tablicy jest określany na podstawie następujących elementów:  
  
- Fakt, że jest tablicą  
  
- Ranga (liczba wymiarów) tablicy  
  
- Typ elementu tablicy  
  
 W szczególności długość danego wymiaru nie jest częścią typu danych wystąpienia. Ilustruje to poniższy przykład.  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 W poprzednim przykładzie Zmienne tablicowe `arrayA` i `arrayB` są uznawane za te same typy danych — `Byte()` nawet wtedy, gdy są one inicjowane do różnych długości. Zmienne `arrayB` i `arrayC` nie są tego samego typu, ponieważ ich typy elementów są różne. Zmienne `arrayC` i `arrayD` nie są tego samego typu, ponieważ ich Range różnią się od siebie. Zmienne `arrayD` i `arrayE` mają ten sam typ — `Short(,)` — ponieważ ich Range i typy elementów są takie same, nawet jeśli `arrayD` nie zostały jeszcze zainicjowane.  
  
 Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../arrays/index.md).  
  
## <a name="class-types"></a>Typy klas  
 Nie istnieje pojedynczy typ danych składający się ze wszystkich klas. Chociaż jedna klasa może dziedziczyć z innej klasy, każda z nich jest osobnym typem danych. Wiele wystąpień tej samej klasy ma ten sam typ danych. W przypadku przypisania jednej zmiennej wystąpienia klasy do innej nie tylko mają one ten sam typ danych, wskazują na to samo wystąpienie klasy w pamięci.  
  
 Aby uzyskać więcej informacji na temat klas, zobacz [obiekty i klasy](../objects-and-classes/index.md).  
  
## <a name="see-also"></a>Zobacz też

- [Typy danych](index.md)
- [Typy danych podstawowych](elementary-data-types.md)
- [Typy ogólne w Visual Basic](generic-types.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Konwersje plików w Visual Basic](type-conversions.md)
- [Struktury](structures.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Instrukcje: Utrzymywanie więcej niż jednej wartości w zmiennej](how-to-hold-more-than-one-value-in-a-variable.md)
