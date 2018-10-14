---
title: Instrukcja ReDim (Visual Basic)
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
ms.openlocfilehash: 9536ea8a6274e0b4a2589caf5aefa271a3567d32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605397"
---
# <a name="redim-statement-visual-basic"></a>Instrukcja ReDim (Visual Basic)
Przydziela ponownie przestrzeń pamięci dla zmiennej tablicowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|----------|----------------|  
|`Preserve`|Opcjonalna. Modyfikator używany w celu zachowania danych w istniejącej tablicy, po zmianie rozmiaru tylko ostatniego wymiaru.|  
|`name`|Wymagana. Nazwa zmiennej tablicowej. Zobacz temat [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Wymagana. Lista granic każdego wymiaru dla ponownie definiowanej tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 Instrukcję `ReDim` można użyć, aby zmienić rozmiar co najmniej jedenego wymiaru tablicy, która została już zadeklarowana. Jeśli masz dużą tablicę i niektóre z jej elementów nie są już potrzebne, `ReDim` może zwolnić pamięć, zmniejszając rozmiar tablicy. Z drugiej strony, jeśli tablica wymaga więcej elementów, `ReDim` może je dodać.  
  
 Instrukcja `ReDim` jest przeznaczona tylko dla tablic. Nie jest prawidłowa dla funkcji skalarnych (zmienne, które zawierają tylko jedną wartość), kolekcji lub struktur. Należy pamiętać, że jeśli deklarujesz zmienną typu `Array`, instrukcja `ReDim` nie ma wystarczających informacji o typie, aby utworzyć nową tablicę.  
  
 `ReDim` można użyć tylko na poziomie procedury. W związku z tym, kontekstem deklaracji zmiennej musi być procedura; nie może to być plik źródłowy, przestrzeń nazw, interfejs, klasa, struktura, moduł lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Wiele zmiennych.** Można zmienić rozmiar kilku zmiennych tablicowych w tej samej instrukcji deklaracji i określić części `name` i `boundlist` dla każdej zmiennej. Wiele zmiennych oddzielamy przecinkami.  
  
-   **Granice tablicy.** Każdy wpis `boundlist` możne określić dolną i górną granicę tego wymiaru. Dolna granica jest zawsze 0 (zero). GGórna granica jest najwyższą możliwą wartością indeksu dla tego wymiaru, a nie długością wymiaru (która jest górną granicą plus jeden). Indeks dla każdego wymiaru może się zmieniać od 0 do górnej wartości.  
  
     Liczba wymiarów w `boundlist` musi być zgodna z oryginalną liczbą wymiarów (ranga) tablicy.  
  
-   **Typy danych.** Instrukcja `ReDim` nie może zmieniać typu danych zmiennej tablicowej lub jej elementów.  
  
-   **Inicjowanie.** Instrukcja `ReDim` nie może podawać nowych wartości inicjalizacji dla elementów tablicy.  
  
-   **Ranga.** Instrukcjia `ReDim` nie można zmienić rangi tablicy (liczby wymiarów).  
  
-   **Zmiana rozmiaru z zachowaniem.** Jeśli używasz `Preserve`, możesz zmienić rozmiar tylko ostatniego wymiaru tablicy. Dla wszystkich pozostałych wymiarów musisz określić ograniczenie istniejącej tablicy.  
  
     Na przykład jeśli tablica ma tylko jeden wymiar, można zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniasz ostatni i jedyny wymiar. Jednak jeśli Twoja tablica ma co najmniej dwa wymiary, możnesz zmienić rozmiaru tylko ostatniego wymiaru używając `Preserve`.  
  
-   **właściwości.** Można użyć `ReDim` dla właściwości, która przechowuje tablicę wartości.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zastąpienie tablicy.** `ReDim` ReDim zwalnia istniejącą tablicę i tworzy nową tablicę o tej samej randze. Nowa tablica zastępuje zwalnianą tablicę w zmiennej tablicowej.  
  
-   **Inicjowanie bez zachowania.** Jeśli nie określisz opcji `Preserve`, `ReDim` zainicjuje elementy nowej tablicy, używając domyślnej wartości dla ich typu danych.  
  
-   **Inicjacja z zachowaniem** Jeśli określisz opcję `Preserve`, Visual Basic kopiuje elementy z istniejącej tablicy do nowej tablicy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwiększa rozmiar ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejsza rozmiar z częściową utratą danych. Na koniec zmniejsza rozmiar do oryginalnej wartości i ponownie inicjuje wszystkie elementy tablicy.  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 Instrukcja `Dim` tworzy nową tablicę z trzema wymiarami. Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru może wynosić od 0 do 10. W poniższym omówieniu te trzy wymiary są określane jako warstwa, wiersz i kolumna.  
  
 Pierwszy `ReDim` tworzy nową tablicę, która zastępuje istniejącą tablicę w zmiennej `intArray`. `ReDim` kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy. Dodaje również dodatkowe 10 kolumn na końcu każdego wiersza w każdej warstwie i inicjuje elementy w tych nowych kolumnach z wartością 0 (wartość domyślna `Integer`, który jest typem elementu tablicy).  
  
 Drugi `ReDim` tworzy kolejną nową tablicę i kopiuje wszystkie mieszczące się elementy. Jednak pięć kolumn od końca każdego wiersza w każdej warstwie jest traconych. Nie stanowi to problemu, jeśli już nie używasz tych kolumn. Zmniejszenie rozmiaru dużej tablicy może zwolnić pamięć, której już nie potrzebujesz.  
  
 Trzeci `ReDim` tworzy kolejną nową tablicę i usuwa kolejne pięć kolumn od końca każdego wiersza w każdej warstwie. Tym razem nie kopiuje żadnych istniejących elementów. To polecenie przywraca tablicę do jej oryginalnego rozmiaru. Ponieważ instrukcja nie zawiera modyfikatora `Preserve`, ustawia wszystkie elementy tablicy na pierwotne wartości domyślne.  
  
 Aby uzyskać dodatkowe przykłady, zobacz [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IndexOutOfRangeException>  
 [Instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Instrukcja Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Instrukcja Erase](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
