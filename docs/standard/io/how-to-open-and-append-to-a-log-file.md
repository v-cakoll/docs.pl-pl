---
title: 'Instrukcje: otwieranie pliku dziennika i dołączanie do niego'
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
ms.openlocfilehash: a549aba3a763bcfc5a3889efd65e2495eca7622c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155714"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Instrukcje: otwieranie pliku dziennika i dołączanie do niego
<xref:System.IO.StreamWriter> i <xref:System.IO.StreamReader> pisać znaki do i odczytywanie znaków ze strumieni. Poniższy przykład kodu otwiera plik *log. txt* dla danych wejściowych lub tworzy go, jeśli nie istnieje, i dołącza informacje dziennika na końcu pliku. Przykład zapisuje zawartość pliku do standardowego wyjścia na potrzeby wyświetlania.

Alternatywą dla tego przykładu jest zapisanie informacji jako jednego ciągu lub tablicy ciągów i użycie metody <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> lub <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> do osiągnięcia tych samych funkcji.  
  
> [!NOTE]
> Visual Basic użytkownicy mogą zdecydować się na użycie metod i właściwości dostarczonych przez klasę <xref:Microsoft.VisualBasic.Logging.Log> lub klasę <xref:Microsoft.VisualBasic.FileIO.FileSystem> do tworzenia lub zapisywania w plikach dziennika.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Instrukcje: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Instrukcje: wpisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Instrukcje: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Instrukcje: Wpisywanie znaków do ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
