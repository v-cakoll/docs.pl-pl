---
title: 'Jak: Napisać tekst do pliku'
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
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160251"
---
# <a name="how-to-write-text-to-a-file"></a>Jak: Napisać tekst do pliku
W tym temacie przedstawiono różne sposoby pisania tekstu w pliku aplikacji .NET.

Następujące klasy i metody są zwykle używane do pisania tekstu do pliku:  
  
- <xref:System.IO.StreamWriter>zawiera<xref:System.IO.StreamWriter.Write%2A> metody zapisu w pliku synchronicznie ( i <xref:System.IO.TextWriter.WriteLine%2A>)<xref:System.IO.StreamWriter.WriteAsync%2A> lub <xref:System.IO.StreamWriter.WriteLineAsync%2A>asynchronicznie ( i ).  
  
- <xref:System.IO.File>udostępnia statyczne metody zapisu tekstu do <xref:System.IO.File.WriteAllLines%2A> pliku, takie jak <xref:System.IO.File.WriteAllText%2A>i , lub <xref:System.IO.File.AppendAllLines%2A>dododane tekst do pliku, takie jak , <xref:System.IO.File.AppendAllText%2A>, i <xref:System.IO.File.AppendText%2A>.  
  
- <xref:System.IO.Path>jest dla ciągów, które mają informacje o ścieżce pliku lub katalogu. Zawiera <xref:System.IO.Path.Combine%2A> metodę i, w .NET Core 2.1 <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> i nowszych, i metody, które umożliwiają łączenie ciągów do tworzenia ścieżki pliku lub katalogu.

> [!NOTE]
> W poniższych przykładach przedstawiono tylko minimalną ilość potrzebnego kodu. Aplikacja w świecie rzeczywistym zwykle zapewnia bardziej niezawodne sprawdzanie błędów i obsługę wyjątków.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Przykład: Synchronicznie pisać tekst za pomocą StreamWriter

W poniższym przykładzie pokazano, jak używać <xref:System.IO.StreamWriter> klasy do synchronicznie pisać tekst do nowego pliku jeden wiersz naraz. Ponieważ <xref:System.IO.StreamWriter> obiekt jest zadeklarowany i tworzone `using` w <xref:System.IO.StreamWriter.Dispose%2A> instrukcji, metoda jest wywoływana, który automatycznie opróżnia i zamyka strumień.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Przykład: Synchronicznie dołączanie tekstu do programu StreamWriter

W poniższym przykładzie pokazano, jak używać <xref:System.IO.StreamWriter> klasy do synchronicznie dołączania tekstu do pliku tekstowego utworzonego w pierwszym przykładzie.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Przykład: Asynchronicznie pisać tekst z StreamWriter

W poniższym przykładzie pokazano, jak asynchronicznie <xref:System.IO.StreamWriter> zapisywać tekst do nowego pliku przy użyciu klasy. Aby wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metodę, wywołanie metody `async` musi znajdować się w ramach metody. Przykład Języka C# wymaga języka C# 7.1 `async` lub nowszego, który dodaje obsługę modyfikatora w punkcie wejścia programu.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Przykład: Pisanie i dołączanie tekstu do klasy Plik

W poniższym przykładzie pokazano, jak napisać tekst do nowego pliku i <xref:System.IO.File> dodać nowe wiersze tekstu do tego samego pliku przy użyciu klasy. Metody <xref:System.IO.File.WriteAllText%2A> <xref:System.IO.File.AppendAllLines%2A> i otwierają i zamykają plik automatycznie. Jeśli ścieżka podanych <xref:System.IO.File.WriteAllText%2A> do metody już istnieje, plik jest zastępowany.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Jak: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Jak: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Jak: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [Plik i strumień we/wy](../../../docs/standard/io/index.md)
