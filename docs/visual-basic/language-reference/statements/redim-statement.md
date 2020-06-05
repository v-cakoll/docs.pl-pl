---
title: ReDim, instrukcja
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
ms.openlocfilehash: 82f19762865fdf3c3f32a0349e21e3b97bebd567
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404281"
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
|`name`|Wymagany. Nazwa zmiennej tablicowej. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Wymagany. Lista granic każdego wymiaru ponownie zdefiniowanej tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć instrukcji, `ReDim` Aby zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już zadeklarowana. Jeśli masz dużą tablicę i nie potrzebujesz już niektórych jej elementów, `ReDim` można zwolnić pamięć, zmniejszając rozmiar tablicy. Z drugiej strony, jeśli tablica wymaga więcej elementów, `ReDim` można je dodać.  
  
 `ReDim`Instrukcja jest przeznaczona tylko dla tablic. Nie jest on prawidłowy w przypadku wartości skalarnych (zmiennych, które zawierają tylko jedną wartość), kolekcji lub struktur. Należy pamiętać, że Jeśli zadeklarujesz zmienną do typu `Array` , `ReDim` instrukcja nie ma wystarczających informacji o typie, aby utworzyć nową tablicę.  
  
 Można używać `ReDim` tylko na poziomie procedury. W związku z tym, kontekst deklaracji dla zmiennej musi być procedurą; nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, klasą, strukturą, modułem lub blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
- **Wiele zmiennych.** Można zmienić rozmiar kilku zmiennych tablicowych w tej samej instrukcji deklaracji i określić `name` `boundlist` części i dla każdej zmiennej. Wiele zmiennych jest oddzielonych przecinkami.  
  
- **Granice tablicy.** Każdy wpis w programie `boundlist` może określać dolną i górną granicę tego wymiaru. Dolna granica jest zawsze równa 0 (zero). Górna granica to najwyższa możliwa wartość indeksu dla tego wymiaru, a nie długość wymiaru (jest to górna granica plus jeden). Indeks każdego wymiaru może się różnić od 0 za pośrednictwem jego górnej wartości powiązanej.  
  
     Liczba wymiarów w `boundlist` musi być zgodna z oryginalną liczbą wymiarów (rangą) tablicy.  
  
- **Typy danych.** `ReDim`Instrukcja nie może zmienić typu danych zmiennej tablicowej ani jej elementów.  
  
- **Zainicjować.** `ReDim`Instrukcja nie może podawać nowych wartości inicjujących dla elementów tablicy.  
  
- **Stopni.** `ReDim`Instrukcja nie może zmienić rangi (liczby wymiarów) tablicy.  
  
- **Zmienianie rozmiarów przy zachowaniu.** Jeśli używasz `Preserve` , możesz zmienić rozmiar tylko ostatniego wymiaru tablicy. Dla każdego innego wymiaru należy określić granicę istniejącej tablicy.  
  
     Na przykład jeśli tablica ma tylko jeden wymiar, można zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniany jest ostatni i tylko wymiar. Jeśli jednak tablica ma dwa lub więcej wymiarów, można zmienić rozmiar tylko ostatniego wymiaru, jeśli używasz `Preserve` .  
  
- **Aœciwoœci.** Można użyć `ReDim` na właściwości, która przechowuje tablicę wartości.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Zastępowanie tablicy.** `ReDim`zwalnia istniejącą tablicę i tworzy nową tablicę o tej samej rangi. Nowa tablica zastępuje wydaną tablicę w zmiennej tablicowej.  
  
- **Inicjalizacja bez zachowania.** Jeśli nie określisz `Preserve` , `ReDim` inicjuje elementy nowej tablicy przy użyciu wartości domyślnej dla ich typu danych.  
  
- **Inicjowanie z zachowaniem.** Jeśli określisz `Preserve` , Visual Basic Kopiuje elementy z istniejącej tablicy do nowej tablicy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwiększa rozmiar ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejsza rozmiar ze częściową utratą danych. Na koniec zmniejsza rozmiar z powrotem do pierwotnej wartości i ponownie inicjuje wszystkie elementy tablicy.  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 `Dim`Instrukcja tworzy nową tablicę z trzema wymiarami. Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru może nastąpić z przedziału od 0 do 10. W poniższej dyskusji trzy wymiary są określane jako warstwy, wiersze i kolumny.  
  
 Najpierw `ReDim` tworzy nową tablicę, która zastąpi istniejącą tablicę zmienną `intArray` . `ReDim`Kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy. Dodaje także 10 większej liczby kolumn do końca każdego wiersza w każdej warstwie i inicjuje elementy w tych nowych kolumnach do 0 (wartość domyślna `Integer` , która jest typem elementu tablicy).  
  
 Druga `ReDim` tworzy kolejną nową tablicę i kopiuje wszystkie elementy, które pasują do siebie. Jednak pięć kolumn zostanie utraconych od końca każdego wiersza w każdej warstwie. Nie jest to problem, Jeśli zakończysz korzystanie z tych kolumn. Zmniejszenie rozmiaru dużej tablicy może zwolnić pamięć, która nie jest już potrzebna.  
  
 Trzecia `ReDim` tworzy kolejną nową tablicę i usuwa kolejną pięć kolumn na końcu każdego wiersza w każdej warstwie. Tym razem nie kopiuje żadnych istniejących elementów. Ta instrukcja przywraca pierwotny rozmiar tablicy. Ponieważ instrukcja nie zawiera `Preserve` modyfikatora, ustawia wszystkie elementy tablicy na ich pierwotne wartości domyślne.  
  
 Aby uzyskać więcej przykładów, zobacz [tablice](../../programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IndexOutOfRangeException>
- [Const, instrukcja](const-statement.md)
- [Dim, instrukcja](dim-statement.md)
- [Erase, instrukcja](erase-statement.md)
- [Nothing](../nothing.md)
- [Tablice](../../programming-guide/language-features/arrays/index.md)
