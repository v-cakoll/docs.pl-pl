---
title: Typowe zadania-O
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 51238020f4d93ad32dac85a95d7b1cab26f2dd64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="common-io-tasks"></a>Typowe zadania We/Wy
<xref:System.IO> Przestrzeń nazw zawiera szereg klas, które umożliwiają różne akcje, takie jak odczytywanie i zapisywanie do wykonania dla plików, katalogów i strumieni. Aby uzyskać więcej informacji, zobacz [plików i strumieni I-O](../../../docs/standard/io/index.md).  
  
## <a name="common-file-tasks"></a>Typowe zadania związane z plikami  
  
|Aby to zrobić...|Zobacz przykład w tym temacie...|  
|-------------------|--------------------------------------|  
|Tworzenie pliku tekstowego|<xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.File.Create%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType>— Metoda|  
|Zapis w pliku tekstowym|[Porady: zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)<br /><br /> [Porady: wpisywanie tekstu do pliku (C + +/ CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Odczyt z pliku tekstowego|[Porady: Odczyt tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Dołączanie tekstu do pliku|[Porady: otwieranie i Dołącz do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)<br /><br /> <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType>— Metoda|  
|Zmienianie nazwy lub przenoszenie pliku|<xref:System.IO.File.Move%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType>— Metoda|  
|Usuwanie pliku|<xref:System.IO.File.Delete%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType>— Metoda|  
|Kopiowanie pliku|<xref:System.IO.File.Copy%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType>— Metoda|  
|Pobieranie rozmiaru pliku|<xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType>Właściwość|  
|Pobieranie atrybutów pliku|<xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType>— Metoda|  
|Ustawianie atrybutów pliku|<xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType>— Metoda|  
|Ustalanie, czy plik istnieje|<xref:System.IO.File.Exists%2A?displayProperty=nameWithType>— Metoda|  
|Odczyt z pliku binarnego|[Porady: Odczyt i zapis do pliku danych nowo utworzony](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Zapis w pliku binarnym|[Porady: Odczyt i zapis do pliku danych nowo utworzony](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Pobieranie rozszerzenia nazwy pliku|<xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType>— Metoda|  
|Pobieranie w pełni kwalifikowanej ścieżki pliku|<xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>— Metoda|  
|Pobieranie nazwy pliku oraz jego rozszerzenia ze ścieżki|<xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType>— Metoda|  
|Zmienianie rozszerzenia pliku|<xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType>— Metoda|  
  
## <a name="common-directory-tasks"></a>Typowe zadania związane z katalogami  
  
|Aby to zrobić...|Zobacz przykład w tym temacie...|  
|-------------------|--------------------------------------|  
|Dostęp do pliku w folderze specjalnym, takim jak Moje dokumenty|[Porady: zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Tworzenie katalogu|<xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType>Właściwość|  
|Tworzenie podkatalogu|<xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType>— Metoda|  
|Zmienianie nazwy lub przenoszenie katalogu|<xref:System.IO.Directory.Move%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType>— Metoda|  
|Kopiowanie katalogu|[Porady: kopiowanie katalogów](../../../docs/standard/io/how-to-copy-directories.md)|  
|Usuwanie katalogu|<xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType>— Metoda<br /><br /> <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType>— Metoda|  
|Wyświetlanie plików i podkatalogów w katalogu|[Porady: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)|  
|Znajdowanie rozmiaru katalogu|<xref:System.IO.Directory?displayProperty=nameWithType>klasy|  
|Ustalanie, czy katalog istnieje|<xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType>— Metoda|  
  
## <a name="see-also"></a>Zobacz też  
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)  
 [Tworzenie strumieni](../../../docs/standard/io/composing-streams.md)  
 [Asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)
