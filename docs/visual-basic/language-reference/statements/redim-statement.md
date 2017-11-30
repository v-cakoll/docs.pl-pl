---
title: "ReDim — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cec66ee33bfd82b3abd623a0130f5635aa3d1d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="redim-statement-visual-basic"></a>ReDim — Instrukcja (Visual Basic)
Przydziela ponownie obszar przechowywania dla zmiennej tablicowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|----------|----------------|  
|`Preserve`|Opcjonalny. Modyfikator używane w celu zachowania danych w istniejącej tablicy po zmianie rozmiaru tylko ostatniego wymiaru.|  
|`name`|Wymagany. Nazwa zmiennej tablicy. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`boundlist`|Wymagany. Lista granic dla każdego wymiaru tablicy ponownie zdefiniowany.|  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `ReDim` instrukcji, aby zmienić rozmiar co najmniej jeden wymiar tablicy, która została już zadeklarowana. Jeśli masz dużą tablicę i niektóre z jego elementów, nie są już potrzebne `ReDim` można zwolnić pamięć, zmniejszając rozmiar tablicy. Z drugiej strony, jeśli tablica wymaga więcej elementów `ReDim` je dodać.  
  
 `ReDim` Instrukcja jest przeznaczona tylko dla tablic. Nie jest prawidłowy w funkcji skalarnych (zmienne, które zawierają tylko jedną wartość), kolekcji lub struktury. Należy pamiętać, że jeśli zadeklarować zmiennej typu `Array`, `ReDim` instrukcji nie ma wystarczających informacji o typie, do utworzenia nowej tablicy.  
  
 Można użyć `ReDim` tylko na poziomie procedury. W związku z tym kontekście deklaracji zmiennej musi być procedury; Nie można go plik źródłowy, przestrzeni nazw, interfejs, klasy, struktury, modułu lub bloku. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Wiele zmiennych.** Można zmienić rozmiar kilku zmiennych tablicowych w tej samej instrukcji deklaracji i określić `name` i `boundlist` części dla każdej zmiennej. Wiele zmiennych są oddzielone przecinkami.  
  
-   **Granice tablicy.** Każdy wpis `boundlist` można określić dolną i górną granicę tego wymiaru. Dolna granica jest zawsze 0 (zero). Górna granica jest największa wartość indeksu możliwe w dla tego wymiaru nie długość wymiaru (czyli górna granica plus jeden). Indeks dla każdego wymiaru może się różnić od 0 do jego górna granica wartości.  
  
     Liczba wymiarów w `boundlist` oryginalna liczba wymiarów (rangę) tablicy musi być zgodna.  
  
-   **Typy danych.** `ReDim` Instrukcji nie można zmienić typ danych zmiennej tablicy lub jego elementów.  
  
-   **Inicjowanie.** `ReDim` Instrukcja nie może zapewnić nowe wartości inicjowania dla elementów tablicy.  
  
-   **Ranga.** `ReDim` Instrukcji nie można zmienić rangą tablicy (liczba wymiarów).  
  
-   **Zmiana rozmiaru z zachowaniem.** Jeśli używasz `Preserve`, zmianie rozmiaru tylko ostatniego wymiaru tablicy. Dla każdego wymiaru należy określić granica istniejącej tablicy.  
  
     Na przykład jeśli tablica ma tylko jeden wymiar, można zmienić rozmiar tego wymiaru i nadal zachować całą zawartość tablicy, ponieważ zmieniasz ostatnie i tylko wymiaru. Jednak jeśli tablica ma co najmniej dwa wymiary, można zmienić rozmiaru tylko ostatniego wymiaru użycie `Preserve`.  
  
-   **Właściwości.** Można użyć `ReDim` dla właściwości, która przechowuje tablicy wartości.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zastąpienie tablicy.** `ReDim`zwalnia istniejącej tablicy i tworzy nową macierz z taką samą rangę. Nowej tablicy zastępuje wydanych tablicy w zmiennej tablicy.  
  
-   **Inicjowanie bez Preserve.** Jeśli nie określisz `Preserve`, `ReDim` inicjuje elementy nowej tablicy przy użyciu wartości domyślnej dla jego typu danych.  
  
-   **Inicjacja za pomocą atrybutu Preserve.** Jeśli określisz `Preserve`, Visual Basic kopiuje elementy z istniejącej tablicy do nowej tablicy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwiększa rozmiar ostatniego wymiaru tablicy dynamicznej bez utraty istniejących danych w tablicy, a następnie zmniejszenie rozmiaru z częściowa utrata danych. Na koniec zmniejsza rozmiar do oryginalnej wartości i ponownie inicjuje wszystkie elementy tablicy.  
  
 [!code-vb[VbVbalrStatements#52](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/redim-statement_1.vb)]  
  
 `Dim` Instrukcja tworzy nową macierz z trzech wymiarów. Każdy wymiar jest zadeklarowany z granicą 10, więc indeks tablicy dla każdego wymiaru mogą należeć do zakresu od 0 do 10. W poniższych kwestii trzy wymiary są nazywane warstwy, wierszy i kolumn.  
  
 Pierwszy `ReDim` tworzy nowy tablicy, która zastępuje istniejącą tablicę w zmiennej `intArray`. `ReDim`kopiuje wszystkie elementy z istniejącej tablicy do nowej tablicy. Również dodaje 10 większą liczbę kolumn na końcu każdego wiersza w każdej warstwie i inicjuje elementów w tych nowych kolumn na wartość 0 (wartość domyślna `Integer`, który jest typem elementu tablicy).  
  
 Drugi `ReDim` tworzy innej tablicy nowy i kopiuje wszystkie elementy, które pasują do. Jednak pięć kolumn zostaną utracone po zakończeniu każdego wiersza w każdej warstwie. Nie jest to problem, po zakończeniu przy użyciu tych kolumn. Zmniejszenie rozmiaru dużą tablicę można zwolnić pamięć, które nie są już potrzebne.  
  
 Trzeci `ReDim` tworzy innej tablicy nowy i usuwa innego pięć kolumn z koniec każdego wiersza w każdej warstwie. Tym razem nie kopiuje elementy. Tej instrukcji zostanie przywrócona do oryginalnego rozmiaru tablicy. Ponieważ nie zawiera instrukcji `Preserve` modyfikator, ustawia wszystkie elementy tablicy oryginalnych wartości domyślnej.  
  
 Aby uzyskać dodatkowe przykłady, zobacz [tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IndexOutOfRangeException>  
 [Const — instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ERASE — instrukcja](../../../visual-basic/language-reference/statements/erase-statement.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
