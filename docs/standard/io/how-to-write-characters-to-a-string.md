---
title: 'Porady: zapisywanie znaków w ciągach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bea51eaf11bd9d73d5a68eb09795bd9f9f143f95
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214475"
---
# <a name="how-to-write-characters-to-a-string"></a>Porady: zapisywanie znaków w ciągach
Poniższe przykłady kodu zapisywać znaki synchronicznie i asynchronicznie z tablicy znaków w ciągu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zapisuje 5 znaków synchronicznie z tablicy na ciąg.  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a>Przykład  
 Następny przykład odczytuje wszystkie znaki asynchronicznie z <xref:System.Windows.Controls.TextBox> kontrolować i przechowuje je w tablicy. Następnie asynchronicznie zapisuje każdy literę lub biały znak w osobnym wierszu następuje znak końca wiersza, aby <xref:System.Windows.Controls.TextBlock> kontroli.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)  
- [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Instrukcje: wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Instrukcje: zapisywanie tekstu w pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
