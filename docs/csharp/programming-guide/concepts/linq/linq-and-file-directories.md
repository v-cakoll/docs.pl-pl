---
title: LINQ i katalogi plików (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: b2153d755b63e1ec14c11b5e94116f7d6b9490f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701778"
---
# <a name="linq-and-file-directories-c"></a>LINQ i katalogi plików (C#)
Wiele operacji systemu plików są zasadniczo zapytań i dlatego są dobrze nadaje się do metody LINQ.  
  
 Należy pamiętać, że w tej sekcji są nieszkodliwe. Nie są używane do zmiany zawartości w oryginalnych plików lub folderów. Wynika to reguły zapytania nie powinny powodować żadnych efektów ubocznych. Ogólnie rzecz biorąc każdy kod (takie jak zapytania, które wykonują Tworzenie / aktualizowanie / delete — operatory), która modyfikuje dane źródłowe powinny być oddzielone od kodu, który odpytuje tylko dane.  
  
 Ta sekcja zawiera następujące tematy:  
  
 [Instrukcje: Zapytanie o pliki o określonym atrybucie lub nazwie (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Pokazuje, jak do wyszukiwania plików, sprawdzając właściwości co najmniej jeden z jego <xref:System.IO.FileInfo> obiektu.  
  
 [Instrukcje: Grupowanie plików według rozszerzenia (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Przedstawia sposób zwrócenia grup <xref:System.IO.FileInfo> obiektu oparte na ich rozszerzenia nazwy pliku.  
  
 [Instrukcje: Zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Przedstawia sposób zwrócenia całkowita liczba bajtów we wszystkich plikach w drzewie określonego katalogu.  
  
 [Instrukcje: Porównywanie zawartości dwóch folderów (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Przedstawia sposób zwrócenia wszystkich plików, które znajdują się w dwóch określonych folderów i również wszystkie pliki, które znajdują się w jednym folderze, ale nie drugiej.  
  
 [Instrukcje: Zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Przedstawia sposób zwrócenia pliku największą lub najmniejszą lub określoną liczbę plików, w drzewie katalogu.  
  
 [Instrukcje: Zapytanie o zduplikowane pliki w drzewie katalogu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Pokazuje, jak grupy dla wszystkich nazw plików, które występują w więcej niż jednej lokalizacji w drzewie określonego katalogu. Przedstawiono również sposób wykonywać bardziej złożone porównania oparte na niestandardowej funkcji porównującej.  
  
 [Instrukcje: Zapytanie o zawartość plików w folderze (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Pokazuje, jak wykonać iterację folderów w drzewie, Otwórz każdy plik i wykonywać zapytania na jego zawartość.  
  
## <a name="comments"></a>Komentarze  
 Złożoność jest związane z tworzeniem źródła danych, które dokładnie reprezentuje zawartość systemu plików i bez problemu zmieniała obsługuje wyjątki. Przykłady w tej sekcji utworzyć kolekcję migawki <xref:System.IO.FileInfo> obiektów, które reprezentuje wszystkie pliki w określonym katalogu głównym folderu i jego podfolderach. Rzeczywisty stan <xref:System.IO.FileInfo> mogą ulec zmianie w okresie między podczas rozpoczęcia i zakończenia wykonywania zapytania. Na przykład można utworzyć listę <xref:System.IO.FileInfo> obiekty do użycia jako źródło danych. Jeśli próbujesz uzyskać dostęp do `Length` właściwości w zapytaniu, <xref:System.IO.FileInfo> obiektu podejmie próbę dostęp do systemu plików, aby zaktualizować wartość `Length`. Jeśli plik już istnieje, zostanie wyświetlony <xref:System.IO.FileNotFoundException> w zapytaniu, nawet jeśli nie wyszukując system plików bezpośrednio. Niektóre zapytania w tej sekcji Użyj oddzielnych metodach, który wykorzystuje te wyjątki określonego w niektórych przypadkach. Innym rozwiązaniem jest zapewnienie źródła danych, aktualizowane dynamicznie przy użyciu <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
