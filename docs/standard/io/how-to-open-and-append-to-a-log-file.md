---
title: "Porady: otwieranie pliku dziennika i dołączanie do niego"
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
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Porady: otwieranie pliku dziennika i dołączanie do niego
<xref:System.IO.StreamWriter>i <xref:System.IO.StreamReader> znaków do zapisu i odczytywanie znaków ze strumieni. Poniższy kod przykładowy otwiera `log.txt` plików dla danych wejściowych lub tworzy plik, jeśli jeszcze nie istnieje i dołącza informacje na końcu pliku. Zawartość pliku następnie są zapisywane do wyjścia standardowego do wyświetlenia. Zamiast tego przykładu, informacje można przechowywane jako pojedynczy ciąg lub tablicę ciągów i <xref:System.IO.File.WriteAllText%2A> lub <xref:System.IO.File.WriteAllLines%2A> — metoda może być stosowana te same funkcje.  
  
> [!NOTE]
>  Visual Basic użytkownicy mogą wybierać metody i właściwości udostępniane przez <xref:Microsoft.VisualBasic.Logging.Log> klasy lub <xref:Microsoft.VisualBasic.FileIO.FileSystem> klasy związane z tworzeniem lub zapisywanie w plikach dziennika.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Porady: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Porady: Odczyt i zapis do pliku danych nowo utworzony](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Porady: Odczyt tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Porady: zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Porady: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Porady: zapisywanie znaków ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)
