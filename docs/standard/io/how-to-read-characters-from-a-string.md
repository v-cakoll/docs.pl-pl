---
title: "Porady: odczytywanie znaków z ciągów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9116ec63bfc1d12daf7627186a52bd29d5918485
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-characters-from-a-string"></a>Porady: odczytywanie znaków z ciągów
W poniższych przykładach kodu przedstawiają sposób synchronicznego i asynchronicznego odczytywanie znaków z ciągu.  
  
## <a name="example"></a>Przykład  
 Ten przykład odczytuje 13 znaków synchronicznie z ciągiem i przechowuje je w tablicy i wyświetla te znaki. Następnie odczytuje pozostałych znaków w ciągu, przechowuje je w tablicy, zaczynając od elementu szóstego i wyświetla zawartość tablicy.  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a>Przykład  
 Kolejnym przykładzie odczytuje wszystkie znaki asynchronicznie od <xref:System.Windows.Controls.TextBox> kontroli i przechowuje je w tablicy. Następnie asynchronicznie zapisuje każdego znaku literą lub biały znak w osobnym wierszu następuje podział wiersza do <xref:System.Windows.Controls.TextBlock> formantu.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StringReader>  
 <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
 [Asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [NIB: Porady: Tworzenie listy katalogów](http://msdn.microsoft.com/en-us/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [Porady: Odczyt i zapis do pliku danych nowo utworzony](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Porady: otwieranie i Dołącz do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Porady: Odczyt tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Porady: zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Porady: zapisywanie znaków ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)
