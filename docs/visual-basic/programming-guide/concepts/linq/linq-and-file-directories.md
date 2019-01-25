---
title: LINQ i katalogi plików (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: bd6889c087f9347c2c056ed10356ae2a55565a4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566869"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ i katalogi plików (Visual Basic)
Wiele operacji systemu plików są zasadniczo zapytań i dlatego są dobrze nadaje się do metody LINQ.  
  
 Należy pamiętać, że w tej sekcji są nieszkodliwe. Nie są używane do zmiany zawartości w oryginalnych plików lub folderów. Wynika to reguły zapytania nie powinny powodować żadnych efektów ubocznych. Ogólnie rzecz biorąc każdy kod (takie jak zapytania, które wykonują Tworzenie / aktualizowanie / delete — operatory), która modyfikuje dane źródłowe powinny być oddzielone od kodu, który odpytuje tylko dane.  
  
 Ta sekcja zawiera następujące tematy:  
  
 [Instrukcje: Zapytanie o pliki o określonym atrybucie lub nazwy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Pokazuje, jak do wyszukiwania plików, sprawdzając właściwości co najmniej jeden z jego <xref:System.IO.FileInfo> obiektu.  
  
 [Instrukcje: Grupa plików według rozszerzenia (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Przedstawia sposób zwrócenia grup <xref:System.IO.FileInfo> obiektu oparte na ich rozszerzenia nazwy pliku.  
  
 [Instrukcje: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Przedstawia sposób zwrócenia całkowita liczba bajtów we wszystkich plikach w drzewie określonego katalogu.  
  
 [Instrukcje: Porównywanie zawartości dwóch folderów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Przedstawia sposób zwrócenia wszystkich plików, które znajdują się w dwóch określonych folderów i również wszystkie pliki, które znajdują się w jednym folderze, ale nie drugiej.  
  
 [Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Przedstawia sposób zwrócenia pliku największą lub najmniejszą lub określoną liczbę plików, w drzewie katalogu.  
  
 [Instrukcje: Zapytanie o zduplikowane pliki w drzewie katalogu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Pokazuje, jak grupy dla wszystkich nazw plików, które występują w więcej niż jednej lokalizacji w drzewie określonego katalogu. Przedstawiono również sposób wykonywać bardziej złożone porównania oparte na niestandardowej funkcji porównującej.  
  
 [Instrukcje: Zapytanie o zawartość plików w folderze (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Pokazuje, jak wykonać iterację folderów w drzewie, Otwórz każdy plik i wykonywać zapytania na jego zawartość.  
  
## <a name="comments"></a>Komentarze  
 Złożoność jest związane z tworzeniem źródła danych, które dokładnie reprezentuje zawartość systemu plików i bez problemu zmieniała obsługuje wyjątki. Przykłady w tej sekcji utworzyć kolekcję migawki <xref:System.IO.FileInfo> obiektów, które reprezentuje wszystkie pliki w określonym katalogu głównym folderu i jego podfolderach. Rzeczywisty stan <xref:System.IO.FileInfo> mogą ulec zmianie w okresie między podczas rozpoczęcia i zakończenia wykonywania zapytania. Na przykład można utworzyć listę <xref:System.IO.FileInfo> obiekty do użycia jako źródło danych. Jeśli próbujesz uzyskać dostęp do `Length` właściwości w zapytaniu, <xref:System.IO.FileInfo> obiektu podejmie próbę dostęp do systemu plików, aby zaktualizować wartość `Length`. Jeśli plik już istnieje, zostanie wyświetlony <xref:System.IO.FileNotFoundException> w zapytaniu, nawet jeśli nie wyszukując system plików bezpośrednio. Niektóre zapytania w tej sekcji Użyj oddzielnych metodach, który wykorzystuje te wyjątki określonego w niektórych przypadkach. Innym rozwiązaniem jest zapewnienie źródła danych, aktualizowane dynamicznie przy użyciu <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Zobacz także
- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
