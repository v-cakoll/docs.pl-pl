---
title: "Porady: zapisywanie znaków w ciągach"
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
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 336a7fec5e64cc0c45566631c73928e0c1d40a5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-characters-to-a-string"></a>Porady: zapisywanie znaków w ciągach
W poniższych przykładach kodu wpisz znaki synchronicznego i asynchronicznego z tablicy znaków w ciągu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład 5 znaków wykonuje synchroniczny zapis z tablicy na ciąg.  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a>Przykład  
 Kolejnym przykładzie odczytuje wszystkie znaki asynchronicznie od <xref:System.Windows.Controls.TextBox> kontroli i przechowuje je w tablicy. Następnie asynchronicznie zapisuje każdego znaku literą lub biały znak w osobnym wierszu następuje podział wiersza do <xref:System.Windows.Controls.TextBlock> formantu.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)  
 [Asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [Porady: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Porady: Odczyt i zapis do pliku danych nowo utworzony](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Porady: otwieranie i Dołącz do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Porady: Odczyt tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Porady: zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Porady: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
