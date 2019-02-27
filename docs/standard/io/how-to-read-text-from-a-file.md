---
title: 'Instrukcje: Odczytywanie tekstu z pliku'
ms.date: 01/03/2019
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
ms.openlocfilehash: 7330c209ce6514459d3ab1dd58dc1c80b1978a56
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56834956"
---
# <a name="how-to-read-text-from-a-file"></a>Instrukcje: Odczytywanie tekstu z pliku
W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych. W obu przykładach podczas tworzenia wystąpienia klasy <xref:System.IO.StreamReader> należy dostarczyć względną lub bezwzględną ścieżkę do pliku. 
  
> [!NOTE]
> Te przykłady kodu nie dotyczą projektowania dla aplikacji Universal Windows (UWP), ponieważ środowisko wykonawcze Windows oferuje typy strumieni różnych do odczytu i zapisu do plików. Na przykład, który pokazuje, jak odczytać tekst z pliku w aplikacji platformy uniwersalnej systemu Windows, zobacz [Szybki Start: Odczyt i zapis plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Przykłady pokazujące, jak przeprowadzać konwersję między strumieniami programu .NET Framework i strumieni środowiska wykonawczego Windows, zobacz [jak: Konwertowanie między strumieniami programu .NET Framework i strumieni środowiska wykonawczego Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Przykład: Synchroniczne odczytu w aplikacji konsoli  
Poniższy przykład przedstawia operację odczytu synchronicznego aplikację konsoli. W tym przykładzie otwiera plik tekstowy, przy użyciu czytnik strumienia kopiuje zawartość na ciąg i wyświetla ciąg do konsoli.  
  
> [!IMPORTANT]
> W przykładzie założono, że plik o nazwie *TestFile.txt* już istnieje w tym samym folderze co aplikacja.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Przykład: Asynchroniczne odczytu w aplikacji WPF 
 Poniższy przykład przedstawia operację odczytu asynchronicznego w aplikacji Windows Presentation Foundation (WPF).  
  
> [!IMPORTANT]
> W przykładzie założono, że plik o nazwie *TestFile.txt* już istnieje w tym samym folderze co aplikacja.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Instrukcje: Utwórz listę katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Szybki start: Odczyt i zapis plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Instrukcje: Konwertowanie między strumieniami programu .NET Framework i strumieni środowiska wykonawczego Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Instrukcje: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Instrukcje: Zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: Odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Instrukcje: Zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
