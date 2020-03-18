---
title: LINQ i katalogi plików (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: fe503584e7d14e8d1dd281eb644f0723782feb4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714623"
---
# <a name="linq-and-file-directories-c"></a>LINQ i katalogi plików (C#)

Wiele operacji systemu plików są zasadniczo zapytania i dlatego są dobrze dostosowane do podejścia LINQ.  
  
 Zapytania w tej sekcji są nieniszczące. Nie są one używane do zmiany zawartości oryginalnych plików lub folderów. Jest to zgodne z regułą, że zapytania nie powinny powodować żadnych skutków ubocznych. Ogólnie rzecz biorąc, każdy kod (w tym kwerendy, które wykonują tworzenie / aktualizacja / usuwanie operatorów), który modyfikuje dane źródłowe powinny być oddzielone od kodu, który po prostu wysyła zapytania do danych.  
  
 Ta sekcja zawiera następujące tematy:  
  
 [Jak wysyłać zapytania do plików o określonym atrybucie lub nazwie (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)\
 Pokazuje, jak wyszukiwać pliki, sprawdzając jedną <xref:System.IO.FileInfo> lub więcej właściwości jego obiektu.  
  
 [Jak grupować pliki według rozszerzenia (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)\
 Pokazuje, jak zwracać grupy <xref:System.IO.FileInfo> obiektów na podstawie ich rozszerzenia nazwy pliku.  
  
 [Jak zbadać całkowitą liczbę bajtów w zestawie folderów (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)\
 Pokazuje, jak zwrócić całkowitą liczbę bajtów we wszystkich plikach w określonym drzewie katalogów.  
  
 [Jak porównać zawartość dwóch folderów (LINQ) (C#)](./how-to-compare-the-contents-of-two-folders-linq.md)s  
 Pokazuje, jak zwrócić wszystkie pliki, które są obecne w dwóch określonych folderach, a także wszystkie pliki, które są obecne w jednym folderze, ale nie innych.  
  
 [Jak wysyłać zapytania o największy plik lub pliki w drzewie katalogów (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)\
 Pokazuje, jak zwrócić największy lub najmniejszy plik lub określoną liczbę plików w drzewie katalogów.  
  
 [Jak wysyłać zapytania o zduplikowane pliki w drzewie katalogów (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)\
 Pokazuje, jak grupować wszystkie nazwy plików występujące w więcej niż jednej lokalizacji w określonym drzewie katalogów. Pokazuje również, jak wykonywać bardziej złożone porównania na podstawie niestandardowego porównania.  
  
 [Jak zbadać zawartość plików w folderze (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)\
 Pokazuje, jak iterate folderów w drzewie, otworzyć każdy plik i kwerendy zawartość pliku.  
  
## <a name="comments"></a>Komentarze  
 Istnieje pewna złożoność związana z tworzeniem źródła danych, które dokładnie reprezentuje zawartość systemu plików i bezpiecznie obsługuje wyjątki. Przykłady w tej sekcji utworzyć kolekcję migawki <xref:System.IO.FileInfo> obiektów, które reprezentuje wszystkie pliki w określonym folderze głównym i wszystkie jego podfoldery. Rzeczywisty stan każdego <xref:System.IO.FileInfo> z nich może ulec zmianie w czasie między rozpoczęciem i zakończeniem wykonywania kwerendy. Na przykład można utworzyć listę <xref:System.IO.FileInfo> obiektów do użycia jako źródło danych. Jeśli spróbujesz `Length` uzyskać dostęp do <xref:System.IO.FileInfo> właściwości w kwerendzie, obiekt spróbuje `Length`uzyskać dostęp do systemu plików w celu zaktualizowania wartości . Jeśli plik już nie istnieje, <xref:System.IO.FileNotFoundException> otrzymasz w zapytaniu, nawet jeśli nie są zapytania systemu plików bezpośrednio. Niektóre kwerendy w tej sekcji używają oddzielnej metody, która zużywa te wyjątki w niektórych przypadkach. Inną opcją jest dynamiczne aktualizowanie źródła danych <xref:System.IO.FileSystemWatcher>przy użyciu pliku .  
  
## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (C#)](./linq-to-objects.md)
