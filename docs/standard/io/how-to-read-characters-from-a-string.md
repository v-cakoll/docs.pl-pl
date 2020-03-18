---
title: 'Jak: Odczytywanie znaków z ciągu'
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
ms.openlocfilehash: ed267ad62e46f6216c94906df1bcefb0684ab51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155766"
---
# <a name="how-to-read-characters-from-a-string"></a>Jak: Odczytywanie znaków z ciągu
Poniższe przykłady kodu pokazują, jak odczytywać znaki synchronicznie lub asynchronicznie z ciągu.  
  
## <a name="example-read-characters-synchronously"></a>Przykład: Synchronicznie odczytznaków
 W tym przykładzie odczytuje 13 znaków synchronicznie z ciągu, przechowuje je w tablicy i wyświetla je. Przykład następnie odczytuje pozostałe znaki w ciągu, przechowuje je w tablicy, począwszy od szóstego elementu i wyświetla zawartość tablicy.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Przykład: Odczyt znaków asynchronicznie  
 Następnym przykładem jest kod za aplikacją WPF. Na obciążenie okna przykład asynchronicznie odczytuje <xref:System.Windows.Controls.TextBox> wszystkie znaki z formantu i przechowuje je w tablicy. Następnie asynchronicznie zapisuje każdą literę lub znak odstępu <xref:System.Windows.Controls.TextBlock> do osobnego wiersza formantu.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [We/Wy pliku asynchronicznego](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Jak: Tworzenie listy katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Jak: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Jak: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Jak: Napisać tekst do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Jak: Zapisywać znaki do ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Plik i strumień we/wy](../../../docs/standard/io/index.md)
