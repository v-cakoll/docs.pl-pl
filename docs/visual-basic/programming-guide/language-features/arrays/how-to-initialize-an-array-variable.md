---
title: 'Porady: inicjowanie zmiennej tablicy w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: ee8cb91fd2fae9637a0d0e33fca63a4cdb9d2fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Porady: inicjowanie zmiennej tablicy w języku Visual Basic
Inicjowanie zmiennej tablicy przy tym literał w tablicy `New` klauzuli i określając wartość początkową tablicy. Można określić typ lub zezwolić na można wywnioskować na podstawie wartości w tablicy literału. Aby uzyskać więcej informacji o sposobie wywnioskować typu, zobacz "Podczas wypełniania tablicy o początkowej wartości" w [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Aby inicjowanie zmiennej tablicy przy użyciu tablicy literału  
  
-   W `New` klauzuli, lub podczas przypisywania wartości tablicy, podaj wartości elementów w nawiasach klamrowych (`{}`). W poniższym przykładzie pokazano kilka sposobów, aby zadeklarować, Utwórz i zainicjuj zmienną zawiera tablicę, która ma elementy typu `Char`.  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     Po wykonaniu każdego instrukcji, tablica, która jest tworzona ma długość wynosi 3 z elementami pod indeksem 0 za pomocą indeksu 2 zawierające wartości początkowe. Jeśli podasz zarówno górną granicę, jak i wartości musi zawierać wartość dla każdego elementu z indeksem 0 za pomocą górnej granicy.  
  
     Zwróć uwagę, że nie trzeba określić indeks górna granica, jeśli podane wartości elementów w tablicy literału. Jeśli nie górna granica jest określony, rozmiar tablicy jest wywnioskowany na podstawie liczby wartości w tablicy literału.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Można zainicjować zmiennej tablicy wielowymiarowej przy użyciu literałów tablicy  
  
-   Zagnieździć wartości w nawiasach klamrowych (`{}`) w nawiasach klamrowych. Upewnij się, że literały tablica zagnieżdżona, którego wszystkie wnioskować tablicowego tego samego typu i długości. W poniższym przykładzie kodu przedstawiono kilka przykładów inicjowanie tablicy wielowymiarowej.  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   Można jawnie określić zakresu tablicy lub Opuść je i kompilatora wnioskować na podstawie wartości w tablicy literału granice tablicy. Jeśli podasz zarówno górną granicę, jak i wartości musi zawierać wartość dla każdego elementu z indeksem 0 za pomocą górnej granicy w każdego wymiaru. W poniższym przykładzie pokazano kilka sposobów, aby zadeklarować, Utwórz i zainicjuj zmienną zawiera jest tablicą dwuwymiarową, który ma elementy typu `Short`  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     Po wykonaniu każdego instrukcji, utworzony tablica zawiera sześć zainicjowane elementów, które mają indeksy `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, i `(1,2)`. Każda lokalizacja tablica zawiera wartość `10`.  
  
-   Poniższy przykład iterację tablicy wielowymiarowej. W aplikacji konsoli systemu Windows, która jest napisany w języku Visual Basic, Wklej kod wewnątrz `Sub Main()` metody. Ostatni komentarze Pokaż dane wyjściowe.  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Można zainicjować zmiennej tablicy nieregularnej przy użyciu literałów tablicy  
  
-   Zagnieździć wartości obiektów w nawiasach klamrowych (`{}`). Mimo że można zagnieżdżać Literały tablicy, określających tablice różne długości w przypadku tablicy nieregularnej, upewnij się, że który literały tablica zagnieżdżona są ujęte w nawiasy (`()`). Nawiasy wymusić oceny literały tablica zagnieżdżona, a wynikowy tablice są używane jako wartość początkową tablicy nieregularnej. W poniższym przykładzie kodu przedstawiono dwa przykłady inicjowanie tablicy nieregularnej.  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   Poniższy przykład iterację tablicą nieregularną. W aplikacji konsoli systemu Windows, która jest napisany w języku Visual Basic, Wklej kod wewnątrz `Sub Main()` metody.  Ostatni komentarze w kodzie Pokaż dane wyjściowe.  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
