---
title: 'Instrukcje: Zapisywanie tekstu do pliku'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d2fb5a30e165b78fef797bf8bfe536b66cae9a1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640751"
---
# <a name="how-to-write-text-to-a-file"></a>Instrukcje: Zapisywanie tekstu do pliku
W tym temacie przedstawiono różne sposoby zapisywanie tekstu do pliku dla aplikacji platformy .NET. 

Następujące klasy i metody są zwykle używane do zapisywanie tekstu do pliku:  
  
- <xref:System.IO.StreamWriter> zawiera metody do zapisu do pliku synchronicznie (<xref:System.IO.StreamWriter.Write%2A> i <xref:System.IO.TextWriter.WriteLine%2A>) lub asynchronicznie (<xref:System.IO.StreamWriter.WriteAsync%2A> i <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
- <xref:System.IO.File> udostępnia metody statyczne do zapisywanie tekstu do pliku, taką jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A>, lub dołączyć tekst do pliku, taką jak <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, i <xref:System.IO.File.AppendText%2A>.  
  
- <xref:System.IO.Path> Służy do ciągów zawierających informacje o ścieżce pliku lub katalogu. Zawiera on <xref:System.IO.Path.Combine%2A> metody i, w programie .NET Core 2.1 i nowsze, <xref:System.IO.Path.Join%2A> i <xref:System.IO.Path.TryJoin%2A> metod, które umożliwiają łączenie ciągów, aby zbudować ścieżki pliku lub katalogu.

> [!NOTE]
> W poniższych przykładach pokazano minimalnej ilości kodu. Aplikacja rzeczywistych zwykle zapewnia bardziej niezawodne sprawdzanie błędów i wyjątków.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Przykład: Synchronicznie wpisać tekst za pomocą StreamWriter

Poniższy przykład pokazuje, jak używać <xref:System.IO.StreamWriter> klasy synchronicznie zapisywanie tekstu do nowego jeden wiersz pliku naraz. Ponieważ <xref:System.IO.StreamWriter> obiektu jest zadeklarowana i tworzone w `using` instrukcji <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda, która automatycznie opróżnia i zamyka strumienia.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a>Przykład: Synchronicznie dołączyć tekst za pomocą StreamWriter

Poniższy przykład pokazuje, jak używać <xref:System.IO.StreamWriter> klasy synchronicznie dołączyć tekst do pliku tekstowego, utworzony w pierwszym przykładzie.   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Przykład: Asynchronicznie zapis tekstu za pomocą StreamWriter

Poniższy przykład pokazuje, jak asynchronicznie zapisywanie tekstu do nowego pliku przy użyciu <xref:System.IO.StreamWriter> klasy. Aby wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metody wywołania metody które muszą znajdować się w `async` metody. C# Przykład wymaga C# 7.1 lub nowszej, który dodaje obsługę `async` modyfikator dla punktu wejścia programu. 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Przykład: Pisanie i dołączyć tekst z klasą plików

Poniższy przykład pokazuje, jak zapisywanie tekstu do nowego pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu <xref:System.IO.File> klasy. <xref:System.IO.File.WriteAllText%2A> i <xref:System.IO.File.AppendAllLines%2A> metod Otwórz i zamknij plik automatycznie. Jeśli ścieżka uzyskiwanie <xref:System.IO.File.WriteAllText%2A> metody już istnieje, zostanie on zastąpiony.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Instrukcje: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Instrukcje: Odczyt i zapis do pliku danych nowo utworzone](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Instrukcje: Otwieranie i dołączanie do pliku dziennika](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Instrukcje: Odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
