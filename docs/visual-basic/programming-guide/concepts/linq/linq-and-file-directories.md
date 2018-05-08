---
title: LINQ i katalogi plików (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 4dbba3fcd6fde52975dd2411c80e662e3d2ffa4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ i katalogi plików (Visual Basic)
Wiele operacji systemu plików są zasadniczo zapytań i w związku z tym dobrze nadaje się do metody LINQ.  
  
 Należy pamiętać, że w tej sekcji są nieszkodliwe. Nie są używane do zmiany zawartości oryginalnych plików lub folderów. Wynika to reguły zapytania nie powinno powodować żadnych efektów ubocznych. Ogólnie rzecz biorąc kodu (takie jak zapytania, wykonujących tworzenia / aktualizacji / delete — operatory), który modyfikuje źródła danych powinny być przechowywane oddzielnie od kodu, który odpytuje tylko dane.  
  
 Ta sekcja zawiera następujące tematy:  
  
 [Porady: zapytanie o pliki o określonym atrybucie lub nazwie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Przedstawiono sposób wyszukiwania plików przez sprawdzenie właściwości co najmniej jeden z jego <xref:System.IO.FileInfo> obiektu.  
  
 [Porady: grupowanie plików według rozszerzenia (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Przedstawia sposób zwrócenia grup <xref:System.IO.FileInfo> obiektu oparte na ich rozszerzenia nazwy pliku.  
  
 [Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Przedstawia sposób zwrócenia całkowita liczba bajtów we wszystkich plikach w drzewie określonego katalogu.  
  
 [Porady: porównywanie zawartości dwóch folderów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Przedstawia sposób zwrócenia wszystkie pliki, które znajdują się w dwóch określonych folderach, a także wszystkich plików znajdujących się w jednym folderze, ale nie drugiej.  
  
 [Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Przedstawia sposób zwrócenia plików największy lub najmniejszą lub określoną liczbę plików, w drzewie katalogu.  
  
 [Porady: zapytanie o zduplikowane pliki w drzewie katalogu (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Przedstawia sposób grupy dla wszystkich nazw plików, które występują w więcej niż jedną lokalizację w drzewie katalogu określonego. Przedstawiono również sposób wykonywania bardziej złożonych porównania oparte na niestandardowej funkcji porównującej.  
  
 [Porady: zapytanie o zawartość plików w folderze (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Pokazano, jak wykonać iterację w drzewie w folderach, Otwórz każdy plik i zapytania jego zawartość.  
  
## <a name="comments"></a>Komentarze  
 Niektóre złożoności jest związane z tworzeniem źródła danych, które dokładnie reprezentuje zawartość systemu plików i bezpiecznie obsługi wyjątków. Przykłady w tej sekcji utworzyć kolekcję migawki <xref:System.IO.FileInfo> obiektów, które reprezentuje wszystkie pliki w określonym katalogu głównym folderu i jego podfolderów. Rzeczywisty stan <xref:System.IO.FileInfo> mogą ulec zmianie w okresie między kiedy rozpocząć i zakończyć wykonywanie zapytania. Na przykład można utworzyć listę <xref:System.IO.FileInfo> obiektów do użycia jako źródło danych. Jeśli użytkownik próbuje uzyskać dostęp `Length` właściwości w zapytaniu, <xref:System.IO.FileInfo> obiektu spróbuje dostęp do systemu plików, aby zaktualizować wartości `Length`. Jeśli plik już istnieje, zostanie wyświetlona <xref:System.IO.FileNotFoundException> w zapytaniu, nawet jeśli nie wyszukując system plików bezpośrednio. Kilka zapytań w tej sekcji, użyj oddzielnych metodach, który wykorzystuje te wyjątki określonego w niektórych przypadkach. Innym rozwiązaniem jest zachowanie aktualizowany dynamicznie przy użyciu źródła danych <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do obiektów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
