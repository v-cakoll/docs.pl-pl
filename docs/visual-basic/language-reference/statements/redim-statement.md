---
title: ReDim — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: fabfd9a45d47cc1b881b3743181a03e89158f939
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346736"
---
# <a name="redim-statement-visual-basic"></a>ReDim, instrukcja (Visual Basic)
Ponownie przydziela miejsce do magazynowania dla zmiennej tablicowej.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|----------|----------------|  
|`Preserve`|Opcjonalna. Modyfikator używany w celu zachowania danych w istniejącej tablicy, gdy zmieniany jest rozmiar tylko ostatniego wymiaru.|  
|`name`|Wymagana. Nazwa zmiennej tablicowej. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Wymagana. Lista granic każdego wymiaru dla ponownie definiowanej tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą instrukcji `ReDim` można zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już zadeklarowana. Jeśli masz dużą tablicę i nie potrzebujesz już niektórych jej elementów, `ReDim` może zwolnić pamięć, zmniejszając rozmiar tablicy. Z drugiej strony, jeśli tablica wymaga więcej elementów, `ReDim` mogą je dodać.  
  
 Instrukcja `ReDim` jest przeznaczona tylko dla tablic. Nie jest odpowiednia dla właściwości skalarnych (zmienne, które zawierają tylko jedną wartość), kolekcji ani struktur. Należy pamiętać, że Jeśli zadeklarujesz zmienną do typu `Array`, instrukcja `ReDim` nie zawiera wystarczających informacji o typie, aby utworzyć nową tablicę.  
  
 `ReDim` można użyć tylko na poziomie procedury. W związku z tym, kontekstem deklaracji zmiennej musi być procedura, a nie plik źródłowy, przestrzeń nazw, interfejs, klasa, struktura, moduł czy blok. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
- **Wiele zmiennych.** Można zmienić rozmiar kilku zmiennych tablicowych w jednej instrukcji deklaracji i określić `name` i `boundlist` części dla każdej zmiennej. Wiele zmiennych rozdziela się przecinkami.  
  
- **Granice tablicy.** Każdy wpis w `boundlist` może określać dolną i górną granicę tego wymiaru. Dolna granica jest zawsze równa 0 (zero). Górna granica jest najwyższą możliwą wartością indeksu dla tego wymiaru, a nie długością wymiaru (która jest większa o jeden od górnej granicy). Indeks dla każdego wymiaru może się zmieniać od 0 do górnej wartości.  
  
     Liczba wymiarów w `boundlist` musi być zgodna z oryginalną liczbą wymiarów (rangą) tablicy.  
  
- **Typy danych.** Instrukcja `ReDim` nie może zmienić typu danych zmiennej tablicowej ani jej elementów.  
  
- **Zainicjować.** Instrukcja `ReDim` nie może udostępniać nowych wartości inicjujących dla elementów tablicy.  
  
- **Stopni.** Instrukcja `ReDim` nie może zmienić rangi (liczby wymiarów) tablicy.  
  
- **Zmienianie rozmiarów przy zachowaniu.** Jeśli używasz `Preserve`, możesz zmienić rozmiar tylko ostatniego wymiaru tablicy. Dla wszystkich pozostałych wymiarów musisz określić granicę istniejącej tablicy.  
  
     Na przykład jeśli tablica ma tylko jeden wymiar, możesz zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniasz ostatni i jedyny wymiar. Jeśli jednak tablica ma dwa lub więcej wymiarów, można zmienić rozmiar tylko ostatniego wymiaru, jeśli używasz `Preserve`.  
  
- **Aœciwoœci.** `ReDim` można użyć na właściwości, która przechowuje tablicę wartości.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Zastępowanie tablicy.** `ReDim` zwalnia istniejącą tablicę i tworzy nową tablicę o tej samej rangi. Nowa tablica zastępuje zwalnianą tablicę w zmiennej tablicowej.  
  
- **Inicjalizacja bez zachowania.** Jeśli nie określisz `Preserve`, `ReDim` inicjuje elementy nowej tablicy przy użyciu wartości domyślnej dla ich typu danych.  
  
- **Inicjowanie z zachowaniem.** Jeśli określisz `Preserve`, Visual Basic Kopiuje elementy z istniejącej tablicy do nowej tablicy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest pokazane zwiększenie rozmiaru ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejszenie rozmiaru z częściową utratą danych. Na koniec następuje zmniejszenie rozmiaru do oryginalnej wartości i ponownie inicjowanie wszystkich elementów tablicy.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 Instrukcja `Dim` tworzy nową tablicę z trzema wymiarami. Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru może wynosić od 0 do 10. W poniższym omówieniu te trzy wymiary są określane jako warstwa, wiersz i kolumna.  
  
 Pierwszy `ReDim` tworzy nową tablicę, która zastępuje istniejącą tablicę w zmiennej `intArray`. `ReDim` kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy. Dodaje także 10 większej liczby kolumn do końca każdego wiersza w każdej warstwie i inicjuje elementy w tych nowych kolumnach do 0 (wartość domyślna `Integer`, która jest typem elementu tablicy).  
  
 Druga `ReDim` tworzy kolejną nową tablicę i kopiuje wszystkie elementy, które pasują do siebie. Jednak pięć kolumn od końca każdego wiersza w każdej warstwie jest traconych. Nie stanowi to problemu, jeśli już nie używasz tych kolumn. Zmniejszenie rozmiaru dużej tablicy może zwolnić pamięć, której już nie potrzebujesz.  
  
 Trzeci `ReDim` tworzy kolejną nową tablicę i usuwa kolejne pięć kolumn z końca każdego wiersza w każdej warstwie. Tym razem nie kopiuje żadnych istniejących elementów. Ta instrukcja przywraca tablicę do jej oryginalnego rozmiaru. Ponieważ instrukcja nie zawiera modyfikatora `Preserve`, ustawia wszystkie elementy tablicy na ich pierwotne wartości domyślne.  
  
 Aby uzyskać więcej przykładów, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IndexOutOfRangeException>
- [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Erase, instrukcja](../../../visual-basic/language-reference/statements/erase-statement.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
