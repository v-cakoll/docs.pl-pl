---
title: 'Jak: Otwieranie i dołączanie do pliku dziennika'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155714"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Jak: Otwieranie i dołączanie do pliku dziennika
<xref:System.IO.StreamWriter>i <xref:System.IO.StreamReader> zapisywać znaki i odczytywać znaki ze strumieni. Poniższy przykład kodu otwiera plik *log.txt* dla danych wejściowych lub tworzy go, jeśli nie istnieje, i dołącza informacje dziennika na końcu pliku. Przykład następnie zapisuje zawartość pliku do standardowego wyjścia do wyświetlania.

Jako alternatywę dla tego przykładu można przechowywać informacje jako pojedynczy <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> ciąg <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> lub tablicy ciągu i użyć lub metody, aby osiągnąć te same funkcje.  
  
> [!NOTE]
> Użytkownicy języka Visual Basic mogą wybrać użycie metod <xref:Microsoft.VisualBasic.Logging.Log> i <xref:Microsoft.VisualBasic.FileIO.FileSystem> właściwości dostarczonych przez klasę lub klasę do tworzenia lub zapisywania w plikach dziennika.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Jak: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Jak: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Jak: Napisać tekst do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Jak: Odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Jak: Zapisywać znaki do ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Plik i strumień we/wy](../../../docs/standard/io/index.md)
