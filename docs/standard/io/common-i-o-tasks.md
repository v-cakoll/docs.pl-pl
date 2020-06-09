---
title: Typowe zadania We/Wy
description: Dowiedz się, jak wykonywać typowe zadania dotyczące plików & wspólnych zadań związanych z katalogiem przy użyciu klas & metod w przestrzeni nazw System.IO w programie .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
ms.openlocfilehash: 4b97b4e464622e482a9ef45e143865ee82e6b5d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598609"
---
# <a name="common-io-tasks"></a>Typowe zadania We/Wy
<xref:System.IO>Przestrzeń nazw zawiera kilka klas, które umożliwiają wykonywanie różnych akcji, takich jak odczytywanie i zapisywanie, w przypadku plików, katalogów i strumieni. Aby uzyskać więcej informacji, zobacz [we/wy plików i strumienia](index.md).  
  
## <a name="common-file-tasks"></a>Typowe zadania związane z plikami  
  
|Aby wykonać tę czynność...|Zobacz przykład w tym temacie...|  
|-------------------|--------------------------------------|  
|Tworzenie pliku tekstowego|Metoda <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.File.Create%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType>|  
|Zapis w pliku tekstowym|[Instrukcje: Zapisywanie tekstu w pliku](how-to-write-text-to-a-file.md)<br /><br /> [Instrukcje: wpisywanie tekstu do pliku tekstowego (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Odczyt z pliku tekstowego|[Instrukcje: Odczytywanie tekstu z pliku](how-to-read-text-from-a-file.md)|  
|Dołączanie tekstu do pliku|[Instrukcje: Otwieranie pliku dziennika i dołączanie do niego](how-to-open-and-append-to-a-log-file.md)<br /><br /> Metoda <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType>|  
|Zmienianie nazwy lub przenoszenie pliku|Metoda <xref:System.IO.File.Move%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Usuwanie pliku|Metoda <xref:System.IO.File.Delete%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType>|  
|Kopiowanie pliku|Metoda <xref:System.IO.File.Copy%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType>|  
|Pobieranie rozmiaru pliku|<xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType>wartość|  
|Pobieranie atrybutów pliku|Metoda <xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType>|  
|Ustawianie atrybutów pliku|Metoda <xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType>|  
|Ustalanie, czy plik istnieje|Metoda <xref:System.IO.File.Exists%2A?displayProperty=nameWithType>|  
|Odczyt z pliku binarnego|[Instrukcje: Odczyt i zapis we właśnie utworzonym pliku danych](how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Zapis w pliku binarnym|[Instrukcje: Odczyt i zapis we właśnie utworzonym pliku danych](how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Pobieranie rozszerzenia nazwy pliku|Metoda <xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType>|  
|Pobieranie w pełni kwalifikowanej ścieżki pliku|Metoda <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>|  
|Pobieranie nazwy pliku oraz jego rozszerzenia ze ścieżki|Metoda <xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType>|  
|Zmienianie rozszerzenia pliku|Metoda <xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType>|  
  
## <a name="common-directory-tasks"></a>Typowe zadania związane z katalogami  
  
|Aby wykonać tę czynność...|Zobacz przykład w tym temacie...|  
|-------------------|--------------------------------------|  
|Dostęp do pliku w folderze specjalnym, takim jak Moje dokumenty|[Instrukcje: Zapisywanie tekstu w pliku](how-to-write-text-to-a-file.md)|  
|Tworzenie katalogu|Metoda <xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType><br /><br /> <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType>wartość|  
|Tworzenie podkatalogu|Metoda <xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType>|  
|Zmienianie nazwy lub przenoszenie katalogu|Metoda <xref:System.IO.Directory.Move%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Kopiowanie katalogu|[Instrukcje: Kopiowanie katalogów](how-to-copy-directories.md)|  
|Usuwanie katalogu|Metoda <xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType>|  
|Wyświetlanie plików i podkatalogów w katalogu|[Instrukcje: Wyliczanie katalogów i plików](how-to-enumerate-directories-and-files.md)|  
|Znajdowanie rozmiaru katalogu|Klasa <xref:System.IO.Directory?displayProperty=nameWithType>|  
|Ustalanie, czy katalog istnieje|Metoda <xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też

- [We/wy plików i strumieni](index.md)
- [Tworzenie strumieni](composing-streams.md)
- [Asynchroniczne operacje we/wy pliku](asynchronous-file-i-o.md)
