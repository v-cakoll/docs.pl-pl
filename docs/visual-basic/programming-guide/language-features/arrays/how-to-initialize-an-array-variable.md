---
title: 'Instrukcje: Inicjowanie zmiennej tablicy w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 67382359a97e9f60b079de1d25589de446042237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638934"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Instrukcje: Inicjowanie zmiennej tablicy w języku Visual Basic
Inicjowanie zmiennej tablicy, umieszczając dołączyć literał tablicy `New` klauzula i określić wartość początkową tablicy. Możesz określić typ lub Zezwalaj, aby był wywnioskowany z wartości w literale tablicy. Aby uzyskać więcej informacji na temat sposobu typ jest wnioskowany, zobacz "Wypełnianie tablicy początkowymi wartościami" w [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Aby zainicjalizować zmienną tablicy przy użyciu literału tablicowego  
  
-   W `New` klauzuli lub po przypisaniu wartości tablicy, należy podać wartości element w nawiasach klamrowych (`{}`). W poniższym przykładzie pokazano kilka sposobów na zadeklarowanie, tworzenie i Inicjowanie zmiennej, by zawierała tablicę z elementami typu `Char`.  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     Po wykonaniu każdej instrukcji, tablica, która jest tworzona ma długość 3, z elementami o indeksie 0 za pomocą indeksu 2, zawierającego wartości początkowe. Jeśli podasz górną granicę i wartości musi zawierać wartość dla każdego elementu z indeksu od 0 do górnej granicy.  
  
     Należy zauważyć, że nie trzeba określić górnego ograniczenia, jeśli podano wartości elementów w tablicy literału. Jeśli nie górna granica jest określony, rozmiar tablicy jest wnioskowany na podstawie liczby wartości w literale tablicy.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Aby zainicjalizować wielowymiarową zmienną tablicy przy użyciu literałów tablicy  
  
-   Umieść wartości obiektu w nawiasach klamrowych (`{}`) wewnątrz nawiasów klamrowych. Upewnij się, że zagnieżdżone literały tablicowe wszystkie działają jako tablice tego samego typu i długości. Poniższy przykład kodu pokazuje kilka przykładów inicjalizacji tablicy wielowymiarowej.  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   Możesz jawnie określić granice tablicy lub opuścić je i pozwolić kompilatorowi na wywnioskowanie granic na podstawie wartości w literale tablicy. Jeśli podasz górne granice i wartości musi zawierać wartość dla każdego elementu z indeksu od 0 do górnej granicy w każdym wymiarze. W poniższym przykładzie pokazano kilka sposobów na zadeklarowanie, tworzenie i Inicjowanie zmiennej, by zawierała dwuwymiarową tablicę z elementami typu `Short`  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     Po wykonaniu każdej instrukcji, utworzona tablica zawiera sześć zainicjowanych elementów, które mają indeksy `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, i `(1,2)`. Każda lokalizacja tablicy zawiera wartość `10`.  
  
-   Poniższy przykład wykonuje iterację przez tablicę wielowymiarową. W aplikacji konsoli Windows, która jest napisana w języku Visual Basic, Wklej kod wewnątrz `Sub Main()` metody. Ostatnio dodane komentarze pokazują dane wyjściowe.  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Aby zainicjalizować niepełną zmienną tablicy przy użyciu literałów tablicy  
  
-   Umieść wartości obiektu w nawiasach klamrowych (`{}`). Chociaż można także zagnieżdżać literały tablicowe, określające tablice o różnej długości, w przypadku nieregularnej tablicy, upewnij się, że literały tablicowe zagnieżdżone są ujęte w nawiasy (`()`). Nawiasy ewaluację zagnieżdżonych tablic literałowych, a wynikłe tablice są używane jako wartości początkowe niepełnych tablic. Poniższy przykład kodu pokazuje dwa przykłady inicjalizacji tablicy nieregularnej.  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   Poniższy przykład wykonuje iterację przez tablicę nieregularną. W aplikacji konsoli Windows, która jest napisana w języku Visual Basic, Wklej kod wewnątrz `Sub Main()` metody.  Ostatnio dodane komentarze w kodzie pokazują dane wyjściowe.  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
