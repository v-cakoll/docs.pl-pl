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
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160251"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="c4cbf-102">Instrukcje: wpisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="c4cbf-102">How to: Write text to a file</span></span>
<span data-ttu-id="c4cbf-103">W tym temacie przedstawiono różne sposoby zapisywania tekstu do pliku dla aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="c4cbf-104">Następujące klasy i metody są zwykle używane do zapisywania tekstu do pliku:</span><span class="sxs-lookup"><span data-stu-id="c4cbf-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="c4cbf-105"><xref:System.IO.StreamWriter> zawiera metody do synchronicznego zapisu w pliku (<xref:System.IO.StreamWriter.Write%2A> i <xref:System.IO.TextWriter.WriteLine%2A>) lub asynchronicznie (<xref:System.IO.StreamWriter.WriteAsync%2A> i <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="c4cbf-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="c4cbf-106"><xref:System.IO.File> udostępnia statyczne metody zapisywania tekstu do pliku, takie jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A>lub do dołączania tekstu do pliku, na przykład <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>i <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="c4cbf-107"><xref:System.IO.Path> jest dla ciągów, które mają informacje o ścieżce pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="c4cbf-108">Zawiera ona metodę <xref:System.IO.Path.Combine%2A> i, w programie .NET Core 2,1 i nowszych, metody <xref:System.IO.Path.Join%2A> i <xref:System.IO.Path.TryJoin%2A>, które umożliwiają łączenie ciągów w celu utworzenia ścieżki pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="c4cbf-109">W poniższych przykładach przedstawiono tylko minimalną wymaganą ilość kodu.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="c4cbf-110">Aplikacja rzeczywista zazwyczaj zapewnia bardziej niezawodne sprawdzanie błędów i obsługę wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="c4cbf-111">Przykład: synchronicznie zapisuj tekst za pomocą StreamWriter —</span><span class="sxs-lookup"><span data-stu-id="c4cbf-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="c4cbf-112">Poniższy przykład pokazuje, jak używać klasy <xref:System.IO.StreamWriter> do synchronicznego zapisywania tekstu do nowego pliku w jednym wierszu naraz.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="c4cbf-113">Ponieważ obiekt <xref:System.IO.StreamWriter> jest zadeklarowany i skonkretyzowany w instrukcji `using`, Metoda <xref:System.IO.StreamWriter.Dispose%2A> jest wywoływana, która automatycznie opróżnia i zamyka strumień.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="c4cbf-114">Przykład: synchronicznie dołączanie tekstu do StreamWriter —</span><span class="sxs-lookup"><span data-stu-id="c4cbf-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="c4cbf-115">Poniższy przykład pokazuje, jak używać klasy <xref:System.IO.StreamWriter> do synchronicznego dołączania tekstu do pliku tekstowego utworzonego w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="c4cbf-116">Przykład: asynchroniczny zapis tekstu z StreamWriter —</span><span class="sxs-lookup"><span data-stu-id="c4cbf-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="c4cbf-117">Poniższy przykład pokazuje, jak asynchronicznie pisać tekst do nowego pliku przy użyciu klasy <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="c4cbf-118">Aby wywołać metodę <xref:System.IO.StreamWriter.WriteAsync%2A>, wywołanie metody musi znajdować się w `async` metodzie.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="c4cbf-119">W C# przykładzie jest C# wymagana 7,1 lub nowsza, co powoduje dodanie obsługi modyfikatora `async` w punkcie wejścia programu.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="c4cbf-120">Przykład: Napisz i Dołącz tekst z klasą plików</span><span class="sxs-lookup"><span data-stu-id="c4cbf-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="c4cbf-121">Poniższy przykład pokazuje, jak napisać tekst do nowego pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu klasy <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="c4cbf-122"><xref:System.IO.File.WriteAllText%2A> i <xref:System.IO.File.AppendAllLines%2A> metody otwierają i zamykają plik automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="c4cbf-123">Jeśli ścieżka do metody <xref:System.IO.File.WriteAllText%2A> już istnieje, plik zostanie nadpisany.</span><span class="sxs-lookup"><span data-stu-id="c4cbf-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="c4cbf-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4cbf-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c4cbf-125">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="c4cbf-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="c4cbf-126">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="c4cbf-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="c4cbf-127">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="c4cbf-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="c4cbf-128">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="c4cbf-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="c4cbf-129">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="c4cbf-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
