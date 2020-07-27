---
title: LINQ i katalogi plików (C#)
description: Te zasoby języka C# LINQ dla operacji systemu plików nie są używane do zmiany zawartości plików lub folderów.
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: ac00e29f90ee1c04ab9978b6ada3ae5f28991a1c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165671"
---
# <a name="linq-and-file-directories-c"></a>LINQ i katalogi plików (C#)

Wiele operacji systemu plików są zasadniczo zapytania i dlatego są dobrze dopasowane do podejścia LINQ.  
  
 Zapytania w tej sekcji nie są destrukcyjne. Nie są one używane do zmiany zawartości oryginalnych plików lub folderów. Wynika to z reguły, że zapytania nie powinny spowodować żadnych efektów ubocznych. Ogólnie rzecz biorąc, każdy kod (łącznie z kwerendami wykonującymi operatory Create/Update/Delete), który modyfikuje dane źródłowe, powinien być oddzielony od kodu, który właśnie wysyła zapytania do danych.  
  
 Ta sekcja zawiera następujące tematy:  
  
 [Jak wykonać zapytanie o pliki o określonym atrybucie lub nazwie (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)\
 Pokazuje, jak wyszukiwać pliki przez badanie jednej lub wielu właściwości <xref:System.IO.FileInfo> obiektu.  
  
 [Jak grupować pliki według rozszerzenia (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)\
 Pokazuje, jak zwracać grupy <xref:System.IO.FileInfo> obiektów na podstawie ich rozszerzenia nazwy pliku.  
  
 [Jak wykonać zapytanie o całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)\
 Pokazuje, jak zwrócić łączną liczbę bajtów we wszystkich plikach w określonym drzewie katalogów.  
  
 [Jak porównać zawartość dwóch folderów (LINQ) (C#](./how-to-compare-the-contents-of-two-folders-linq.md)) s  
 Pokazuje, jak zwrócić wszystkie pliki znajdujące się w dwóch określonych folderach, a także wszystkie pliki, które znajdują się w jednym folderze, ale nie w drugim.  
  
 [Jak wykonać zapytanie o największy plik lub pliki w drzewie katalogów (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)\
 Pokazuje, jak zwrócić największy lub najmniejszy plik lub określoną liczbę plików w drzewie katalogów.  
  
 [Jak wykonać zapytanie o zduplikowane pliki w drzewie katalogów (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)\
 Pokazuje, jak grupować dla wszystkich nazw plików występujących w więcej niż jednej lokalizacji w określonym drzewie katalogów. Pokazuje również, jak wykonywać bardziej złożone porównania na podstawie niestandardowej metody porównującej.  
  
 [Jak zbadać zawartość plików w folderze (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)\
 Pokazuje, jak wykonać iterację folderów w drzewie, otworzyć każdy plik i zbadać zawartość pliku.  
  
## <a name="comments"></a>Komentarze  
 Istnieje pewna złożoność w tworzeniu źródła danych, które dokładnie reprezentuje zawartość systemu plików i w sposób łagodnie obsługuje wyjątki. W przykładach w tej sekcji przedstawiono tworzenie kolekcji migawek <xref:System.IO.FileInfo> obiektów, które reprezentują wszystkie pliki w określonym folderze głównym i jego podfolderach. Rzeczywisty stan każdego z nich <xref:System.IO.FileInfo> może ulec zmianie w czasie między rozpoczęciem i zakończeniem wykonywania zapytania. Na przykład można utworzyć listę <xref:System.IO.FileInfo> obiektów do użycia jako źródło danych. Jeśli spróbujesz uzyskać dostęp do `Length` właściwości w zapytaniu, <xref:System.IO.FileInfo> obiekt podejmie próbę uzyskania dostępu do systemu plików w celu zaktualizowania wartości `Length` . Jeśli plik już nie istnieje, pojawi się <xref:System.IO.FileNotFoundException> w zapytaniu, mimo że nie masz bezpośredniego zapytania dotyczącego systemu plików. Niektóre zapytania w tej sekcji wykorzystują osobną metodę, która wykorzystuje te konkretne wyjątki w niektórych przypadkach. Inna opcja polega na tym, że źródło danych jest aktualizowane dynamicznie przy użyciu <xref:System.IO.FileSystemWatcher> .  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](./linq-to-objects.md)
