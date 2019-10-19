---
title: ReDim — Instrukcja (Visual Basic)
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
ms.openlocfilehash: a9384ba118df2a84fbd2581e6a8bacb58e41ddcc
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582087"
---
# <a name="redim-statement-visual-basic"></a>ReDim — Instrukcja (Visual Basic)
Ponownie przydziela miejsce do magazynowania dla zmiennej tablicowej.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|----------|----------------|  
|`Preserve`|Opcjonalny. Modyfikator używany do zachowania danych w istniejącej tablicy po zmianie rozmiaru tylko ostatniego wymiaru.|  
|`name`|Wymagany. Nazwa zmiennej tablicowej. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Wymagany. Lista granic każdego wymiaru ponownie zdefiniowanej tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą instrukcji `ReDim` można zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już zadeklarowana. Jeśli masz dużą tablicę i nie potrzebujesz już niektórych jej elementów, `ReDim` może zwolnić pamięć, zmniejszając rozmiar tablicy. Z drugiej strony, jeśli tablica wymaga więcej elementów, `ReDim` mogą je dodać.  
  
 Instrukcja `ReDim` jest przeznaczona tylko dla tablic. Nie jest on prawidłowy w przypadku wartości skalarnych (zmiennych, które zawierają tylko jedną wartość), kolekcji lub struktur. Należy pamiętać, że Jeśli zadeklarujesz zmienną do typu `Array`, instrukcja `ReDim` nie zawiera wystarczających informacji o typie, aby utworzyć nową tablicę.  
  
 @No__t_0 można użyć tylko na poziomie procedury. W związku z tym, kontekst deklaracji dla zmiennej musi być procedurą; nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, klasą, strukturą, modułem lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Przepisy  
  
- **Wiele zmiennych.** Można zmienić rozmiar kilku zmiennych tablicowych w jednej instrukcji deklaracji i określić `name` i `boundlist` części dla każdej zmiennej. Wiele zmiennych jest oddzielonych przecinkami.  
  
- **Granice tablicy.** Każdy wpis w `boundlist` może określać dolną i górną granicę tego wymiaru. Dolna granica jest zawsze równa 0 (zero). Górna granica to najwyższa możliwa wartość indeksu dla tego wymiaru, a nie długość wymiaru (jest to górna granica plus jeden). Indeks każdego wymiaru może się różnić od 0 za pośrednictwem jego górnej wartości powiązanej.  
  
     Liczba wymiarów w `boundlist` musi być zgodna z oryginalną liczbą wymiarów (rangą) tablicy.  
  
- **Typy danych.** Instrukcja `ReDim` nie może zmienić typu danych zmiennej tablicowej ani jej elementów.  
  
- **Zainicjować.** Instrukcja `ReDim` nie może udostępniać nowych wartości inicjujących dla elementów tablicy.  
  
- **Stopni.** Instrukcja `ReDim` nie może zmienić rangi (liczby wymiarów) tablicy.  
  
- **Zmienianie rozmiarów przy zachowaniu.** Jeśli używasz `Preserve`, możesz zmienić rozmiar tylko ostatniego wymiaru tablicy. Dla każdego innego wymiaru należy określić granicę istniejącej tablicy.  
  
     Na przykład jeśli tablica ma tylko jeden wymiar, można zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniany jest ostatni i tylko wymiar. Jeśli jednak tablica ma dwa lub więcej wymiarów, można zmienić rozmiar tylko ostatniego wymiaru, jeśli używasz `Preserve`.  
  
- **Aœciwoœci.** @No__t_0 można użyć na właściwości, która przechowuje tablicę wartości.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Zastępowanie tablicy.** `ReDim` zwalnia istniejącą tablicę i tworzy nową tablicę o tej samej rangi. Nowa tablica zastępuje wydaną tablicę w zmiennej tablicowej.  
  
- **Inicjalizacja bez zachowania.** Jeśli nie określisz `Preserve`, `ReDim` inicjuje elementy nowej tablicy przy użyciu wartości domyślnej dla ich typu danych.  
  
- **Inicjowanie z zachowaniem.** Jeśli określisz `Preserve`, Visual Basic Kopiuje elementy z istniejącej tablicy do nowej tablicy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwiększa rozmiar ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejsza rozmiar ze częściową utratą danych. Na koniec zmniejsza rozmiar z powrotem do pierwotnej wartości i ponownie inicjuje wszystkie elementy tablicy.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 Instrukcja `Dim` tworzy nową tablicę z trzema wymiarami. Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru może nastąpić z przedziału od 0 do 10. W poniższej dyskusji trzy wymiary są określane jako warstwy, wiersze i kolumny.  
  
 Pierwszy `ReDim` tworzy nową tablicę, która zastępuje istniejącą tablicę w zmiennej `intArray`. `ReDim` kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy. Dodaje także 10 większej liczby kolumn do końca każdego wiersza w każdej warstwie i inicjuje elementy w tych nowych kolumnach do 0 (wartość domyślna `Integer`, która jest typem elementu tablicy).  
  
 Druga `ReDim` tworzy kolejną nową tablicę i kopiuje wszystkie elementy, które pasują do siebie. Jednak pięć kolumn zostanie utraconych od końca każdego wiersza w każdej warstwie. Nie jest to problem, Jeśli zakończysz korzystanie z tych kolumn. Zmniejszenie rozmiaru dużej tablicy może zwolnić pamięć, która nie jest już potrzebna.  
  
 Trzeci `ReDim` tworzy kolejną nową tablicę i usuwa kolejne pięć kolumn z końca każdego wiersza w każdej warstwie. Tym razem nie kopiuje żadnych istniejących elementów. Ta instrukcja przywraca pierwotny rozmiar tablicy. Ponieważ instrukcja nie zawiera modyfikatora `Preserve`, ustawia wszystkie elementy tablicy na ich pierwotne wartości domyślne.  
  
 Aby uzyskać więcej przykładów, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IndexOutOfRangeException>
- [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Erase, instrukcja](../../../visual-basic/language-reference/statements/erase-statement.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
