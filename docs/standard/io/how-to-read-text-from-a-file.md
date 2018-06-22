---
title: 'Porady: odczyt tekstu z pliku'
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7c54e5e55770f3df44819cdf6d2d2c866f7e0fc
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298165"
---
# <a name="how-to-read-text-from-a-file"></a>Porady: odczyt tekstu z pliku
W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych. W obu przykładach, podczas tworzenia wystąpienia <xref:System.IO.StreamReader> klasy, podaj względna lub bezwzględna ścieżka do pliku. W poniższych przykładach założono, że plik o nazwie TestFile.txt znajduje się w folderze aplikacji.  
  
 Te przykłady kodu nie dotyczą tworzenie aplikacji dla aplikacji ze Sklepu Windows, ponieważ środowisko wykonawcze systemu Windows zapewnia strumienia różne typy odczytywanie i zapisywanie do plików. Przykład pokazujący sposób odczyt tekstu z pliku w aplikacji ze Sklepu Windows, temacie [Szybki Start: Odczyt i zapis plików](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh758325(v=win.10)). Przykłady, które pokazują, jak wykonać konwersji między .NET Framework i strumieni środowiska wykonawczego systemu Windows, temacie [porady: konwertowanie między .NET Framework i strumieni środowiska wykonawczego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono synchronicznych operacji odczytu w aplikacji konsoli. W tym przykładzie pliku tekstowego jest otwarty przy użyciu czytnik strumienia zawartości są kopiowane do ciągu i ciągu jest dane wyjściowe do konsoli.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia operację asynchroniczną odczytu w aplikacji Windows Presentation Foundation (WPF).  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [NIB: Porady: Tworzenie listy katalogów](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [Szybki Start: Odczyt i zapis plików](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [Instrukcje: konwersja strumieni platformy .NET Framework i strumieni środowiska wykonawczego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Instrukcje: zapisywanie tekstu w pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Instrukcje: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Instrukcje: zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
