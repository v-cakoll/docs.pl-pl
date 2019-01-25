---
title: 'Instrukcje: Odczytywanie znaków z ciągu'
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbf213c783d1688e9168265cedc27d2ac7a5a96d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504820"
---
# <a name="how-to-read-characters-from-a-string"></a>Instrukcje: Odczytywanie znaków z ciągu
Następujące przykłady kodu przedstawiają sposób synchronicznie i asynchronicznie odczytywanie znaków z ciągu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie odczytuje 13 znaków synchronicznie z ciągu, przechowuje je w tablicy i wyświetla te znaki. Następnie odczytuje pozostałych znaków w ciągu, przechowuje je w tablicy, zaczynając od szóstego elementu i wyświetla zawartość tablicy.  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a>Przykład  
 Następny przykład odczytuje wszystkie znaki asynchronicznie z <xref:System.Windows.Controls.TextBox> kontrolować i przechowuje je w tablicy. Następnie asynchronicznie zapisuje każdy literę lub biały znak w osobnym wierszu następuje znak końca wiersza, aby <xref:System.Windows.Controls.TextBlock> kontroli.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StringReader>
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>
- [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)
- [NIB: Instrukcje: Utwórz listę katalogów](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)
- [Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Instrukcje: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Instrukcje: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Instrukcje: Zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [Instrukcje: Zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
