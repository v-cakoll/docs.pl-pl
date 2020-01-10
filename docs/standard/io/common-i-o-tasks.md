---
title: Typowe zadania We/Wy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
ms.openlocfilehash: 01e9d6b50bd7eeafea792a772ca86a81e40dafd4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708181"
---
# <a name="common-io-tasks"></a>Typowe zadania We/Wy
Przestrzeń nazw <xref:System.IO> zawiera kilka klas, które umożliwiają wykonywanie różnych akcji, takich jak odczytywanie i zapisywanie, w przypadku plików, katalogów i strumieni. Aby uzyskać więcej informacji, zobacz [we/wy plików i strumienia](../../../docs/standard/io/index.md).  
  
## <a name="common-file-tasks"></a>Typowe zadania związane z plikami  
  
|Aby to zrobić...|Zobacz przykład w tym temacie...|  
|-------------------|--------------------------------------|  
|Tworzenie pliku tekstowego|Metoda <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.File.Create%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType>|  
|Zapis w pliku tekstowym|[Instrukcje: zapisywanie tekstu w pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)<br /><br /> [Instrukcje: wpisywanie tekstu do pliku tekstowego (C++/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Odczyt z pliku tekstowego|[Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Dołączanie tekstu do pliku|[Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)<br /><br /> Metoda <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType>|  
|Zmienianie nazwy lub przenoszenie pliku|Metoda <xref:System.IO.File.Move%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Usuwanie pliku|Metoda <xref:System.IO.File.Delete%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType>|  
|Kopiowanie pliku|Metoda <xref:System.IO.File.Copy%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType>|  
|Pobieranie rozmiaru pliku|<xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType> Właściwość|  
|Pobieranie atrybutów pliku|Metoda <xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType>|  
|Ustawianie atrybutów pliku|Metoda <xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType>|  
|Ustalanie, czy plik istnieje|Metoda <xref:System.IO.File.Exists%2A?displayProperty=nameWithType>|  
|Odczyt z pliku binarnego|[Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Zapis w pliku binarnym|[Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Pobieranie rozszerzenia nazwy pliku|Metoda <xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType>|  
|Pobieranie w pełni kwalifikowanej ścieżki pliku|Metoda <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>|  
|Pobieranie nazwy pliku oraz jego rozszerzenia ze ścieżki|Metoda <xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType>|  
|Zmienianie rozszerzenia pliku|Metoda <xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType>|  
  
## <a name="common-directory-tasks"></a>Typowe zadania związane z katalogami  
  
|Aby to zrobić...|Zobacz przykład w tym temacie...|  
|-------------------|--------------------------------------|  
|Dostęp do pliku w folderze specjalnym, takim jak Moje dokumenty|[Instrukcje: zapisywanie tekstu w pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Tworzenie katalogu|Metoda <xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType><br /><br /> <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType> Właściwość|  
|Tworzenie podkatalogu|Metoda <xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType>|  
|Zmienianie nazwy lub przenoszenie katalogu|Metoda <xref:System.IO.Directory.Move%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Kopiowanie katalogu|[Instrukcje: kopiowanie katalogów](../../../docs/standard/io/how-to-copy-directories.md)|  
|Usuwanie katalogu|Metoda <xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType><br /><br /> Metoda <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType>|  
|Wyświetlanie plików i podkatalogów w katalogu|[Instrukcje: wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)|  
|Znajdowanie rozmiaru katalogu|Klasa <xref:System.IO.Directory?displayProperty=nameWithType>|  
|Ustalanie, czy katalog istnieje|Metoda <xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
- [Tworzenie strumieni](../../../docs/standard/io/composing-streams.md)
- [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)
