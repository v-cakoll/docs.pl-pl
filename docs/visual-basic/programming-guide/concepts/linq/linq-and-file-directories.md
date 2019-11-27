---
title: LINQ i katalogi plików
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 390d3c7a1c738aea0df8e3dcad0edb70563f8fb6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347797"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ i katalogi plików (Visual Basic)
Wiele operacji systemu plików są zasadniczo zapytania i są w związku z tym dobrze dostosowane do podejścia LINQ.  
  
 Należy zauważyć, że zapytania w tej sekcji nie są destrukcyjne. Nie są one używane do zmiany zawartości oryginalnych plików lub folderów. Wynika to z reguły, że zapytania nie powinny spowodować żadnych efektów ubocznych. Ogólnie rzecz biorąc, każdy kod (łącznie z kwerendami wykonującymi operatory Create/Update/Delete), który modyfikuje dane źródłowe, powinien być oddzielony od kodu, który właśnie wysyła zapytania do danych.  
  
 Ta sekcja zawiera następujące tematy:  
  
 [Instrukcje: zapytanie o pliki o określonym atrybucie lub nazwie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Pokazuje, jak wyszukiwać pliki przez badanie jednej lub wielu właściwości obiektu <xref:System.IO.FileInfo>.  
  
 [Instrukcje: grupowanie plików według rozszerzenia (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Pokazuje, jak zwracać grupy obiektu <xref:System.IO.FileInfo> na podstawie ich rozszerzenia nazwy pliku.  
  
 [Instrukcje: zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Pokazuje, jak zwrócić łączną liczbę bajtów we wszystkich plikach w określonym drzewie katalogów.  
  
 [Instrukcje: porównywanie zawartości dwóch folderów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Pokazuje, jak zwrócić wszystkie pliki znajdujące się w dwóch określonych folderach, a także wszystkie pliki, które znajdują się w jednym folderze, ale nie w drugim.  
  
 [Instrukcje: zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Pokazuje, jak zwrócić największy lub najmniejszy plik lub określoną liczbę plików w drzewie katalogów.  
  
 [Instrukcje: zapytanie o zduplikowane pliki w drzewie katalogów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Pokazuje, jak grupować dla wszystkich nazw plików występujących w więcej niż jednej lokalizacji w określonym drzewie katalogów. Pokazuje również, jak wykonywać bardziej złożone porównania na podstawie niestandardowej metody porównującej.  
  
 [Jak zbadać zawartość plików w folderze (LINQ) (Visual Basic)](how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Pokazuje, jak wykonać iterację folderów w drzewie, otworzyć każdy plik i zbadać zawartość pliku.  
  
## <a name="comments"></a>Komentarze  
 Istnieje pewna złożoność w tworzeniu źródła danych, które dokładnie reprezentuje zawartość systemu plików i w sposób łagodnie obsługuje wyjątki. W przykładach w tej sekcji przedstawiono tworzenie kolekcji migawek <xref:System.IO.FileInfo> obiektów, które reprezentują wszystkie pliki w określonym folderze głównym i jego podfolderach. Rzeczywisty stan poszczególnych <xref:System.IO.FileInfo> może ulec zmianie w czasie między rozpoczęciem i zakończeniem wykonywania zapytania. Na przykład można utworzyć listę obiektów <xref:System.IO.FileInfo>, które mają być używane jako źródło danych. Jeśli spróbujesz uzyskać dostęp do właściwości `Length` w zapytaniu, obiekt <xref:System.IO.FileInfo> podejmie próbę uzyskania dostępu do systemu plików w celu zaktualizowania wartości `Length`. Jeśli plik już nie istnieje, uzyskasz <xref:System.IO.FileNotFoundException> w zapytaniu, mimo że nie ma bezpośredniego zapytania dotyczącego systemu plików. Niektóre zapytania w tej sekcji wykorzystują osobną metodę, która wykorzystuje te konkretne wyjątki w niektórych przypadkach. Inna opcja polega na tym, że źródło danych jest aktualizowane dynamicznie przy użyciu <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
