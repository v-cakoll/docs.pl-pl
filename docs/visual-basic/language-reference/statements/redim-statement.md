---
title: ReDim, instrukcja (Visual Basic)
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
# <a name="redim-statement-visual-basic"></a>ReDim, instrukcja (Visual Basic)
Przydziela ponownie obszar przechowywania dla zmiennej tablicowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|----------|----------------|  
|`Preserve`|Opcjonalna. Modyfikator używany w celu zachowania danych w istniejącej tablicy, gdy zmieniany jest rozmiar tylko ostatniego wymiaru.|  
|`name`|Wymagana. Nazwa zmiennej tablicowej. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Wymagana. Lista granic każdego wymiaru dla ponownie definiowanej tablicy.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą instrukcji `ReDim` można zmienić rozmiar co najmniej jednego wymiaru tablicy, która została już zadeklarowana. Jeśli tablica jest duża i niektóre z jej elementów nie są już potrzebne, instrukcja `ReDim` może zwolnić pamięć, zmniejszając rozmiar tablicy. Z drugiej strony, jeśli tablica wymaga więcej elementów, instrukcja `ReDim` może je dodać.  
  
 Instrukcja `ReDim` jest przeznaczona tylko dla tablic. Nie jest odpowiednia dla właściwości skalarnych (zmienne, które zawierają tylko jedną wartość), kolekcji ani struktur. Pamiętaj, że jeśli deklarujesz zmienną typu `Array`, instrukcja `ReDim` nie ma wystarczających informacji o typie, aby utworzyć nową tablicę.  
  
 Instrukcji `ReDim` można używać tylko na poziomie procedury. W związku z tym, kontekstem deklaracji zmiennej musi być procedura, a nie plik źródłowy, przestrzeń nazw, interfejs, klasa, struktura, moduł czy blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Wiele zmiennych.** Można zmienić rozmiar kilku zmiennych tablicowych w tej samej instrukcji deklaracji oraz określić części `name` i `boundlist` dla każdej zmiennej. Wiele zmiennych rozdziela się przecinkami.  
  
-   **Granice tablicy.** Każdy wpis w części `boundlist` może określać dolną i górną granicę tego wymiaru. Dolna granica jest zawsze równa 0 (zero). Górna granica jest najwyższą możliwą wartością indeksu dla tego wymiaru, a nie długością wymiaru (która jest większa o jeden od górnej granicy). Indeks dla każdego wymiaru może się zmieniać od 0 do górnej wartości.  
  
     Liczba wymiarów w części `boundlist` musi być zgodna z oryginalną liczbą wymiarów (rangą) tablicy.  
  
-   **Typy danych.** Instrukcja `ReDim` nie może zmieniać typu danych zmiennej tablicowej ani jej elementów.  
  
-   **Inicjowanie.** Instrukcja `ReDim` nie może podawać nowych wartości inicjalizacji dla elementów tablicy.  
  
-   **Ranga.** Instrukcja `ReDim` nie może zmienić rangi (liczby wymiarów) tablicy.  
  
-   **Zmiana rozmiaru z zachowaniem zawartości.** Jeśli używasz części `Preserve`, możesz zmienić rozmiar tylko ostatniego wymiaru tablicy. Dla wszystkich pozostałych wymiarów musisz określić granicę istniejącej tablicy.  
  
     Na przykład jeśli tablica ma tylko jeden wymiar, możesz zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniasz ostatni i jedyny wymiar. Jednak jeśli Twoja tablica ma co najmniej dwa wymiary, korzystając z części `Preserve` możesz zmienić rozmiar tylko ostatniego wymiaru.  
  
-   **Właściwości.** Instrukcji `ReDim` można użyć dla właściwości, która przechowuje tablicę wartości.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zamiana tablicy.** Instrukcja `ReDim` zwalnia istniejącą tablicę i tworzy nową tablicę o tej samej randze. Nowa tablica zastępuje zwalnianą tablicę w zmiennej tablicowej.  
  
-   **Inicjowanie bez zachowania zawartości.** Jeśli nie określisz części `Preserve`, instrukcja `ReDim` zainicjuje elementy nowej tablicy, używając domyślnej wartości dla ich typu danych.  
  
-   **Inicjowanie z zachowaniem zawartości** Jeśli określisz część `Preserve`, język Visual Basic skopiuje elementy z istniejącej tablicy do nowej tablicy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest pokazane zwiększenie rozmiaru ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejszenie rozmiaru z częściową utratą danych. Na koniec następuje zmniejszenie rozmiaru do oryginalnej wartości i ponownie inicjowanie wszystkich elementów tablicy.  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 Instrukcja `Dim` tworzy nową tablicę z trzema wymiarami. Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru może wynosić od 0 do 10. W poniższym omówieniu te trzy wymiary są określane jako warstwa, wiersz i kolumna.  
  
 Pierwsza instrukcja `ReDim` tworzy nową tablicę, która zastępuje istniejącą tablicę w zmiennej `intArray`. Instrukcja `ReDim` kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy. Dodaje również dodatkowe 10 kolumn na końcu każdego wiersza w każdej warstwie i inicjuje elementy w tych nowych kolumnach z wartością 0 (wartość domyślna `Integer`, który jest typem elementu tablicy).  
  
 Druga instrukcja `ReDim` tworzy kolejną nową tablicę i kopiuje wszystkie mieszczące się elementy. Jednak pięć kolumn od końca każdego wiersza w każdej warstwie jest traconych. Nie stanowi to problemu, jeśli już nie używasz tych kolumn. Zmniejszenie rozmiaru dużej tablicy może zwolnić pamięć, której już nie potrzebujesz.  
  
 Trzecia instrukcja `ReDim` tworzy kolejną nową tablicę i usuwa kolejne pięć kolumn od końca każdego wiersza w każdej warstwie. Tym razem nie kopiuje żadnych istniejących elementów. Ta instrukcja przywraca tablicę do jej oryginalnego rozmiaru. Ponieważ instrukcja nie zawiera modyfikatora `Preserve`, ustawia wszystkie elementy tablicy na pierwotne wartości domyślne.  
  
 Aby uzyskać dodatkowe przykłady, zobacz [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IndexOutOfRangeException>  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Erase, instrukcja](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
