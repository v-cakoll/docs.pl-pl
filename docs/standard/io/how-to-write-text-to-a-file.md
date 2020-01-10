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
ms.openlocfilehash: 42b758eeb36a4c319c3e1f24676cb600d580902e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706611"
---
# <a name="how-to-write-text-to-a-file"></a>Instrukcje: wpisywanie tekstu do pliku
W tym temacie przedstawiono różne sposoby zapisywania tekstu do pliku dla aplikacji .NET. 

Następujące klasy i metody są zwykle używane do zapisywania tekstu do pliku:  
  
- <xref:System.IO.StreamWriter> zawiera metody do synchronicznego zapisu w pliku (<xref:System.IO.StreamWriter.Write%2A> i <xref:System.IO.TextWriter.WriteLine%2A>) lub asynchronicznie (<xref:System.IO.StreamWriter.WriteAsync%2A> i <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
- <xref:System.IO.File> udostępnia statyczne metody zapisywania tekstu do pliku, takie jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A>lub do dołączania tekstu do pliku, na przykład <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>i <xref:System.IO.File.AppendText%2A>.  
  
- <xref:System.IO.Path> jest dla ciągów, które mają informacje o ścieżce pliku lub katalogu. Zawiera ona metodę <xref:System.IO.Path.Combine%2A> i, w programie .NET Core 2,1 i nowszych, metody <xref:System.IO.Path.Join%2A> i <xref:System.IO.Path.TryJoin%2A>, które umożliwiają łączenie ciągów w celu utworzenia ścieżki pliku lub katalogu.

> [!NOTE]
> W poniższych przykładach przedstawiono tylko minimalną wymaganą ilość kodu. Aplikacja rzeczywista zazwyczaj zapewnia bardziej niezawodne sprawdzanie błędów i obsługę wyjątków.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Przykład: synchronicznie zapisuj tekst za pomocą StreamWriter —

Poniższy przykład pokazuje, jak używać klasy <xref:System.IO.StreamWriter> do synchronicznego zapisywania tekstu do nowego pliku w jednym wierszu naraz. Ponieważ obiekt <xref:System.IO.StreamWriter> jest zadeklarowany i skonkretyzowany w instrukcji `using`, Metoda <xref:System.IO.StreamWriter.Dispose%2A> jest wywoływana, która automatycznie opróżnia i zamyka strumień.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a>Przykład: synchronicznie dołączanie tekstu do StreamWriter —

Poniższy przykład pokazuje, jak używać klasy <xref:System.IO.StreamWriter> do synchronicznego dołączania tekstu do pliku tekstowego utworzonego w pierwszym przykładzie.   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Przykład: asynchroniczny zapis tekstu z StreamWriter —

Poniższy przykład pokazuje, jak asynchronicznie pisać tekst do nowego pliku przy użyciu klasy <xref:System.IO.StreamWriter>. Aby wywołać metodę <xref:System.IO.StreamWriter.WriteAsync%2A>, wywołanie metody musi znajdować się w `async` metodzie. W C# przykładzie jest C# wymagana 7,1 lub nowsza, co powoduje dodanie obsługi modyfikatora `async` w punkcie wejścia programu. 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Przykład: Napisz i Dołącz tekst z klasą plików

Poniższy przykład pokazuje, jak napisać tekst do nowego pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu klasy <xref:System.IO.File>. <xref:System.IO.File.WriteAllText%2A> i <xref:System.IO.File.AppendAllLines%2A> metody otwierają i zamykają plik automatycznie. Jeśli ścieżka do metody <xref:System.IO.File.WriteAllText%2A> już istnieje, plik zostanie nadpisany.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Instrukcje: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [We/wy plików i strumieni](../../../docs/standard/io/index.md)
