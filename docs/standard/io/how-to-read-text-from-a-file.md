---
title: 'Jak: Odczytywanie tekstu z pliku'
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
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155727"
---
# <a name="how-to-read-text-from-a-file"></a>Jak: Odczytywanie tekstu z pliku
W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych. W obu przykładach podczas tworzenia wystąpienia <xref:System.IO.StreamReader> klasy, należy podać ścieżkę względną lub bezwzględną do pliku.
  
> [!NOTE]
> Te przykłady kodu nie mają zastosowania do tworzenia aplikacji dla systemu Uniwersalnego systemu Windows (UWP), ponieważ środowisko uruchomieniowe systemu Windows udostępnia różne typy strumieni do odczytu i zapisu w plikach. Na przykład, który pokazuje, jak odczytywać tekst z pliku w aplikacji systemu uwp, zobacz [Szybki start: Odczytywanie i zapisywanie plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Przykłady, które pokazują, jak konwertować między strumieniami .NET Framework i strumieniśrodowiska uruchomieniowego systemu Windows, zobacz [Jak: Konwertować między strumieniami .NET Framework i strumieniami środowiska uruchomieniowego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Przykład: Odczyt synchroniczny w aplikacji konsoli  
W poniższym przykładzie przedstawiono synchroniczną operację odczytu w aplikacji konsoli. W tym przykładzie otwiera plik tekstowy przy użyciu czytnika strumienia, kopiuje zawartość do ciągu i wyprowadza ciąg do konsoli.  
  
> [!IMPORTANT]
> W przykładzie przyjęto założenie, że plik o nazwie *TestFile.txt* już istnieje w tym samym folderze co aplikacja.  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Przykład: Odczyt asynchroniczny w aplikacji WPF
 W poniższym przykładzie przedstawiono operację odczytu asynchronicznego w aplikacji Programu Windows Presentation Foundation (WPF).  
  
> [!IMPORTANT]
> W przykładzie przyjęto założenie, że plik o nazwie *TestFile.txt* już istnieje w tym samym folderze co aplikacja.  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [We/Wy pliku asynchronicznego](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Jak: Tworzenie listy katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Szybki start: czytanie i zapisywanie plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [Jak: Konwertować między strumieniami programu .NET Framework a strumieniami środowiska uruchomieniowego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Jak: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Jak: Napisać tekst do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Jak: Odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Jak: Zapisywać znaki do ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Plik i strumień we/wy](../../../docs/standard/io/index.md)
