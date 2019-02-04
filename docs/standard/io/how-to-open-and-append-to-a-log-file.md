---
title: 'Instrukcje: Otwieranie i dołączanie do pliku dziennika'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 921b13e057929d7d6b283b26014a4c1f195f39c9
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674844"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Instrukcje: Otwieranie i dołączanie do pliku dziennika
<xref:System.IO.StreamWriter> i <xref:System.IO.StreamReader> zapisu znaków do i odczytywanie znaków ze strumieni. Poniższy kod przykładowy otwiera *log.txt* plików dla danych wejściowych lub go utworzy, jeśli nie istnieje i dołącza informacje dziennika na końcu pliku. Przykład następnie zapisuje zawartość pliku do wyjścia standardowego do wyświetlenia. 

Jako alternatywę do tego przykładu, można przechowywać informacje jako pojedynczy ciąg lub tablicę ciągów i użyj <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> lub <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> metodę, aby osiągnąć te same funkcje.  
  
> [!NOTE]
> Użytkownicy języka Visual Basic mogą zdecydować się na metody i właściwości dostarczonych przez <xref:Microsoft.VisualBasic.Logging.Log> klasy lub <xref:Microsoft.VisualBasic.FileIO.FileSystem> klasa do tworzenia lub zapisywanie w plikach dziennika.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Instrukcje: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Instrukcje: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Instrukcje: Zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: Odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Instrukcje: Zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
