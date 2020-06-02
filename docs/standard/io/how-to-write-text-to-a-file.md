---
title: 'Instrukcje: wpisywanie tekstu do pliku'
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
ms.openlocfilehash: 395344accf5be416fbcc527e51ba83408f9c5810
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291737"
---
# <a name="how-to-write-text-to-a-file"></a>Instrukcje: wpisywanie tekstu do pliku
W tym temacie przedstawiono różne sposoby zapisywania tekstu do pliku dla aplikacji .NET.

Następujące klasy i metody są zwykle używane do zapisywania tekstu do pliku:  
  
- <xref:System.IO.StreamWriter>zawiera metody do zapisu w pliku synchronicznie ( <xref:System.IO.StreamWriter.Write%2A> i <xref:System.IO.TextWriter.WriteLine%2A> ) lub asynchronicznie ( <xref:System.IO.StreamWriter.WriteAsync%2A> oraz <xref:System.IO.StreamWriter.WriteLineAsync%2A> ).  
  
- <xref:System.IO.File>zapewnia statyczne metody zapisywania tekstu do pliku, takie jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A> , lub do dołączania tekstu do pliku, takich jak <xref:System.IO.File.AppendAllLines%2A> , <xref:System.IO.File.AppendAllText%2A> , i <xref:System.IO.File.AppendText%2A> .  
  
- <xref:System.IO.Path>jest dla ciągów, które mają informacje o ścieżce pliku lub katalogu. Zawiera ona <xref:System.IO.Path.Combine%2A> metodę i, w programie .NET Core 2,1 i nowszych, <xref:System.IO.Path.Join%2A> metody i <xref:System.IO.Path.TryJoin%2A> , które umożliwiają łączenie ciągów w celu utworzenia ścieżki pliku lub katalogu.

> [!NOTE]
> W poniższych przykładach przedstawiono tylko minimalną wymaganą ilość kodu. Aplikacja rzeczywista zazwyczaj zapewnia bardziej niezawodne sprawdzanie błędów i obsługę wyjątków.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Przykład: synchronicznie zapisuj tekst za pomocą StreamWriter —

Poniższy przykład pokazuje, jak używać <xref:System.IO.StreamWriter> klasy do synchronicznego zapisywania tekstu do nowego pliku w jednym wierszu naraz. Ponieważ <xref:System.IO.StreamWriter> obiekt jest zadeklarowany i skonkretyzowany w `using` instrukcji, <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda, która automatycznie opróżnia i zamyka strumień.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Przykład: synchronicznie dołączanie tekstu do StreamWriter —

Poniższy przykład pokazuje, jak używać <xref:System.IO.StreamWriter> klasy do synchronicznego dołączania tekstu do pliku tekstowego utworzonego w pierwszym przykładzie.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Przykład: asynchroniczny zapis tekstu z StreamWriter —

Poniższy przykład pokazuje, jak asynchronicznie pisać tekst do nowego pliku przy użyciu <xref:System.IO.StreamWriter> klasy. Aby wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metodę, wywołanie metody musi znajdować się wewnątrz `async` metody. Przykład w języku C# wymaga języka C# 7,1 lub nowszego, który dodaje obsługę `async` modyfikatora w punkcie wejścia programu.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Przykład: Napisz i Dołącz tekst z klasą plików

Poniższy przykład pokazuje, jak napisać tekst do nowego pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu <xref:System.IO.File> klasy. <xref:System.IO.File.WriteAllText%2A>Metody i <xref:System.IO.File.AppendAllLines%2A> otwierają i zamykają plik automatycznie. Jeśli ścieżka do <xref:System.IO.File.WriteAllText%2A> metody już istnieje, plik zostanie nadpisany.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Instrukcje: Wyliczanie katalogów i plików](how-to-enumerate-directories-and-files.md)
- [Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych](how-to-read-and-write-to-a-newly-created-data-file.md)
- [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](how-to-open-and-append-to-a-log-file.md)
- [Instrukcje: odczytywanie tekstu z pliku](how-to-read-text-from-a-file.md)
- [We/wy plików i strumieni](index.md)
