---
title: 'Instrukcje: Inicjowanie zmiennej tablicy w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 4aa783d6179c72760a12d0259d587b5b38bb9140
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832245"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Instrukcje: Inicjowanie zmiennej tablicy w języku Visual Basic
Inicjowanie zmiennej tablicy, umieszczając dołączyć literał tablicy `New` klauzula i określić wartość początkową tablicy. Możesz określić typ lub Zezwalaj, aby był wywnioskowany z wartości w literale tablicy. Aby uzyskać więcej informacji na temat sposobu typ jest wnioskowany, zobacz "Wypełnianie tablicy początkowymi wartościami" w [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Aby zainicjalizować zmienną tablicy przy użyciu literału tablicowego  
  
-   W `New` klauzuli lub po przypisaniu wartości tablicy, należy podać wartości element w nawiasach klamrowych (`{}`). W poniższym przykładzie pokazano kilka sposobów na zadeklarowanie, tworzenie i Inicjowanie zmiennej, by zawierała tablicę z elementami typu `Char`.  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     Po wykonaniu każdej instrukcji, tablica, która jest tworzona ma długość 3, z elementami o indeksie 0 za pomocą indeksu 2, zawierającego wartości początkowe. Jeśli podasz górną granicę i wartości musi zawierać wartość dla każdego elementu z indeksu od 0 do górnej granicy.  
  
     Należy zauważyć, że nie trzeba określić górnego ograniczenia, jeśli podano wartości elementów w tablicy literału. Jeśli nie górna granica jest określony, rozmiar tablicy jest wnioskowany na podstawie liczby wartości w literale tablicy.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Aby zainicjalizować wielowymiarową zmienną tablicy przy użyciu literałów tablicy  
  
-   Umieść wartości obiektu w nawiasach klamrowych (`{}`) wewnątrz nawiasów klamrowych. Upewnij się, że zagnieżdżone literały tablicowe wszystkie działają jako tablice tego samego typu i długości. Poniższy przykład kodu pokazuje kilka przykładów inicjalizacji tablicy wielowymiarowej.  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
-   Możesz jawnie określić granice tablicy lub opuścić je i pozwolić kompilatorowi na wywnioskowanie granic na podstawie wartości w literale tablicy. Jeśli podasz górne granice i wartości musi zawierać wartość dla każdego elementu z indeksu od 0 do górnej granicy w każdym wymiarze. W poniższym przykładzie pokazano kilka sposobów na zadeklarowanie, tworzenie i Inicjowanie zmiennej, by zawierała dwuwymiarową tablicę z elementami typu `Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     Po wykonaniu każdej instrukcji, utworzona tablica zawiera sześć zainicjowanych elementów, które mają indeksy `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, i `(1,2)`. Każda lokalizacja tablicy zawiera wartość `10`.  
  
-   Poniższy przykład wykonuje iterację przez tablicę wielowymiarową. W aplikacji konsoli Windows, która jest napisana w języku Visual Basic, Wklej kod wewnątrz `Sub Main()` metody. Ostatnio dodane komentarze pokazują dane wyjściowe.  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Aby zainicjalizować niepełną zmienną tablicy przy użyciu literałów tablicy  
  
-   Umieść wartości obiektu w nawiasach klamrowych (`{}`). Chociaż można także zagnieżdżać literały tablicowe, określające tablice o różnej długości, w przypadku nieregularnej tablicy, upewnij się, że literały tablicowe zagnieżdżone są ujęte w nawiasy (`()`). Nawiasy ewaluację zagnieżdżonych tablic literałowych, a wynikłe tablice są używane jako wartości początkowe niepełnych tablic. Poniższy przykład kodu pokazuje dwa przykłady inicjalizacji tablicy nieregularnej.  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
-   Poniższy przykład wykonuje iterację przez tablicę nieregularną. W aplikacji konsoli Windows, która jest napisana w języku Visual Basic, Wklej kod wewnątrz `Sub Main()` metody.  Ostatnio dodane komentarze w kodzie pokazują dane wyjściowe.  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Zobacz także

- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
