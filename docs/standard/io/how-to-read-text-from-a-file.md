---
title: 'Porady: odczyt tekstu z pliku'
ms.date: 03/30/2017
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
ms.openlocfilehash: 0bb37c5beaaa529ea09fa23f31b55a0d6bc6d510
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574533"
---
# <a name="how-to-read-text-from-a-file"></a>Porady: odczyt tekstu z pliku
W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych. W obu przykładach, podczas tworzenia wystąpienia <xref:System.IO.StreamReader> klasy, podaj względna lub bezwzględna ścieżka do pliku. W poniższych przykładach założono, że plik o nazwie TestFile.txt znajduje się w folderze aplikacji.  
  
 Te przykłady kodu nie dotyczą projektowania aplikacji do Sklepu Windows, ponieważ środowisko wykonawcze systemu Windows oferuje inne typy strumieni odczytujących i zapisujących pliki. Przykład pokazujący sposób odczyt tekstu z plików w kontekście aplikacji ze Sklepu Windows, temacie [Szybki Start: Odczyt i zapis plików](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx). Przykłady sposobu konwersji między .NET Framework i strumieni środowiska wykonawczego systemu Windows można znaleźć [porady: konwertowanie między .NET Framework i strumieni środowiska wykonawczego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example"></a>Przykład  
 W pierwszym przykładzie pokazano operację odczytu synchronicznego przy użyciu aplikacji konsoli. W tym przykładzie plik jest otwarty przy użyciu czytnik strumienia, zawartość jest kopiowana do ciągu i parametry są dane wyjściowe do konsoli.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a>Przykład  
 W drugim przykładzie pokazano operację odczytu asynchronicznego przy użyciu aplikacji programu Windows Presentation Foundation (WPF).  
  
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
