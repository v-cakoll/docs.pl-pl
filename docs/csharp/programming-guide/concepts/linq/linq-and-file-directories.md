---
title: "LINQ i katalogi plików (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 62c7ee272c788ca687b84bb76a853e58f83f69ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-and-file-directories-c"></a>LINQ i katalogi plików (C#)
Wiele operacji systemu plików są zasadniczo zapytań i w związku z tym dobrze nadaje się do metody LINQ.  
  
 Należy pamiętać, że w tej sekcji są nieszkodliwe. Nie są używane do zmiany zawartości oryginalnych plików lub folderów. Wynika to reguły zapytania nie powinno powodować żadnych efektów ubocznych. Ogólnie rzecz biorąc kodu (takie jak zapytania, wykonujących tworzenia / aktualizacji / delete — operatory), który modyfikuje źródła danych powinny być przechowywane oddzielnie od kodu, który odpytuje tylko dane.  
  
 Ta sekcja zawiera następujące tematy:  
  
 [Porady: zapytanie o pliki o określonym atrybucie lub nazwie (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Przedstawiono sposób wyszukiwania plików przez sprawdzenie właściwości co najmniej jeden z jego <xref:System.IO.FileInfo> obiektu.  
  
 [Porady: grupowanie plików według rozszerzenia (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Przedstawia sposób zwrócenia grup <xref:System.IO.FileInfo> obiektu oparte na ich rozszerzenia nazwy pliku.  
  
 [Porady: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Przedstawia sposób zwrócenia całkowita liczba bajtów we wszystkich plikach w drzewie określonego katalogu.  
  
 [Porady: porównywanie zawartości dwóch folderów (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Przedstawia sposób zwrócenia wszystkie pliki, które znajdują się w dwóch określonych folderach, a także wszystkich plików znajdujących się w jednym folderze, ale nie drugiej.  
  
 [Porady: zapytanie o największy plik lub pliki w drzewie katalogu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Przedstawia sposób zwrócenia plików największy lub najmniejszą lub określoną liczbę plików, w drzewie katalogu.  
  
 [Porady: zapytanie o zduplikowane pliki w drzewie katalogu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Przedstawia sposób grupy dla wszystkich nazw plików, które występują w więcej niż jedną lokalizację w drzewie katalogu określonego. Przedstawiono również sposób wykonywania bardziej złożonych porównania oparte na niestandardowej funkcji porównującej.  
  
 [Porady: zapytanie o zawartość plików w folderze (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Pokazano, jak wykonać iterację w drzewie w folderach, Otwórz każdy plik i zapytania jego zawartość.  
  
## <a name="comments"></a>Komentarze  
 Niektóre złożoności jest związane z tworzeniem źródła danych, które dokładnie reprezentuje zawartość systemu plików i bezpiecznie obsługi wyjątków. Przykłady w tej sekcji utworzyć kolekcję migawki <xref:System.IO.FileInfo> obiektów, które reprezentuje wszystkie pliki w określonym katalogu głównym folderu i jego podfolderów. Rzeczywisty stan <xref:System.IO.FileInfo> mogą ulec zmianie w okresie między kiedy rozpocząć i zakończyć wykonywanie zapytania. Na przykład można utworzyć listę <xref:System.IO.FileInfo> obiektów do użycia jako źródło danych. Jeśli użytkownik próbuje uzyskać dostęp `Length` właściwości w zapytaniu, <xref:System.IO.FileInfo> obiektu spróbuje dostęp do systemu plików, aby zaktualizować wartości `Length`. Jeśli plik już istnieje, zostanie wyświetlona <xref:System.IO.FileNotFoundException> w zapytaniu, nawet jeśli nie wyszukując system plików bezpośrednio. Kilka zapytań w tej sekcji, użyj oddzielnych metodach, który wykorzystuje te wyjątki określonego w niektórych przypadkach. Innym rozwiązaniem jest zachowanie aktualizowany dynamicznie przy użyciu źródła danych <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do obiektów (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
