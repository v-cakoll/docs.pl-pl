---
title: 'Instrukcje: odczytywanie znaków z ciągu'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: 0c3516c4abadfd22609c3568beffc14e027ef69e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706676"
---
# <a name="how-to-read-characters-from-a-string"></a>Instrukcje: odczytywanie znaków z ciągu
Poniższy przykład kodu pokazuje, jak odczytywać znaki synchronicznie lub asynchronicznie z ciągu.  
  
## <a name="example-read-characters-synchronously"></a>Przykład: Odczytaj znaki synchronicznie 
 Ten przykład odczytuje 13 znaków synchronicznie z ciągu, zapisuje je w tablicy i wyświetla je. Przykład odczytuje pozostałe znaki w ciągu, zapisuje je w tablicy, zaczynając od szóstego elementu i wyświetla zawartość tablicy.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Przykład: odczytywanie znaków asynchronicznie  
 Następny przykład to kod związany z aplikacją WPF. W przypadku ładowania okna przykład Asynchronicznie odczytuje wszystkie znaki z kontrolki <xref:System.Windows.Controls.TextBox> i zapisuje je w tablicy. Następnie asynchronicznie zapisuje każdą literę lub biały znak w osobnym wierszu kontrolki <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [Asynchroniczne operacje we/wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Instrukcje: Tworzenie listy katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Instrukcje: wpisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: Wpisywanie znaków do ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
