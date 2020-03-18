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
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="e607e-102">Jak: Napisać tekst do pliku</span><span class="sxs-lookup"><span data-stu-id="e607e-102">How to: Write text to a file</span></span>
<span data-ttu-id="e607e-103">W tym temacie przedstawiono różne sposoby pisania tekstu w pliku aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="e607e-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="e607e-104">Następujące klasy i metody są zwykle używane do pisania tekstu do pliku:</span><span class="sxs-lookup"><span data-stu-id="e607e-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="e607e-105"><xref:System.IO.StreamWriter>zawiera<xref:System.IO.StreamWriter.Write%2A> metody zapisu w pliku synchronicznie ( i <xref:System.IO.TextWriter.WriteLine%2A>)<xref:System.IO.StreamWriter.WriteAsync%2A> lub <xref:System.IO.StreamWriter.WriteLineAsync%2A>asynchronicznie ( i ).</span><span class="sxs-lookup"><span data-stu-id="e607e-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="e607e-106"><xref:System.IO.File>udostępnia statyczne metody zapisu tekstu do <xref:System.IO.File.WriteAllLines%2A> pliku, takie jak <xref:System.IO.File.WriteAllText%2A>i , lub <xref:System.IO.File.AppendAllLines%2A>dododane tekst do pliku, takie jak , <xref:System.IO.File.AppendAllText%2A>, i <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="e607e-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="e607e-107"><xref:System.IO.Path>jest dla ciągów, które mają informacje o ścieżce pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="e607e-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="e607e-108">Zawiera <xref:System.IO.Path.Combine%2A> metodę i, w .NET Core 2.1 <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> i nowszych, i metody, które umożliwiają łączenie ciągów do tworzenia ścieżki pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="e607e-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="e607e-109">W poniższych przykładach przedstawiono tylko minimalną ilość potrzebnego kodu.</span><span class="sxs-lookup"><span data-stu-id="e607e-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="e607e-110">Aplikacja w świecie rzeczywistym zwykle zapewnia bardziej niezawodne sprawdzanie błędów i obsługę wyjątków.</span><span class="sxs-lookup"><span data-stu-id="e607e-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="e607e-111">Przykład: Synchronicznie pisać tekst za pomocą StreamWriter</span><span class="sxs-lookup"><span data-stu-id="e607e-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="e607e-112">W poniższym przykładzie pokazano, jak używać <xref:System.IO.StreamWriter> klasy do synchronicznie pisać tekst do nowego pliku jeden wiersz naraz.</span><span class="sxs-lookup"><span data-stu-id="e607e-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="e607e-113">Ponieważ <xref:System.IO.StreamWriter> obiekt jest zadeklarowany i tworzone `using` w <xref:System.IO.StreamWriter.Dispose%2A> instrukcji, metoda jest wywoływana, który automatycznie opróżnia i zamyka strumień.</span><span class="sxs-lookup"><span data-stu-id="e607e-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="e607e-114">Przykład: Synchronicznie dołączanie tekstu do programu StreamWriter</span><span class="sxs-lookup"><span data-stu-id="e607e-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="e607e-115">W poniższym przykładzie pokazano, jak używać <xref:System.IO.StreamWriter> klasy do synchronicznie dołączania tekstu do pliku tekstowego utworzonego w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e607e-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="e607e-116">Przykład: Asynchronicznie pisać tekst z StreamWriter</span><span class="sxs-lookup"><span data-stu-id="e607e-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="e607e-117">W poniższym przykładzie pokazano, jak asynchronicznie <xref:System.IO.StreamWriter> zapisywać tekst do nowego pliku przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="e607e-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="e607e-118">Aby wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metodę, wywołanie metody `async` musi znajdować się w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="e607e-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="e607e-119">Przykład Języka C# wymaga języka C# 7.1 `async` lub nowszego, który dodaje obsługę modyfikatora w punkcie wejścia programu.</span><span class="sxs-lookup"><span data-stu-id="e607e-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="e607e-120">Przykład: Pisanie i dołączanie tekstu do klasy Plik</span><span class="sxs-lookup"><span data-stu-id="e607e-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="e607e-121">W poniższym przykładzie pokazano, jak napisać tekst do nowego pliku i <xref:System.IO.File> dodać nowe wiersze tekstu do tego samego pliku przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="e607e-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="e607e-122">Metody <xref:System.IO.File.WriteAllText%2A> <xref:System.IO.File.AppendAllLines%2A> i otwierają i zamykają plik automatycznie.</span><span class="sxs-lookup"><span data-stu-id="e607e-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="e607e-123">Jeśli ścieżka podanych <xref:System.IO.File.WriteAllText%2A> do metody już istnieje, plik jest zastępowany.</span><span class="sxs-lookup"><span data-stu-id="e607e-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="e607e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e607e-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e607e-125">Jak: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="e607e-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="e607e-126">Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="e607e-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="e607e-127">Jak: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="e607e-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="e607e-128">Jak: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="e607e-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="e607e-129">Plik i strumień we/wy</span><span class="sxs-lookup"><span data-stu-id="e607e-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
