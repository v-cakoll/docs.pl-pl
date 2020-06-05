---
title: 'Instrukcje: wpisywanie tekstu do pliku'
description: Informacje o sposobach pisania lub dołączania tekstu do pliku dla aplikacji .NET. Użyj metod z klas StreamWriter — lub File, aby pisać tekst synchronicznie lub asynchronicznie.
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
ms.openlocfilehash: 52d3d07f4ffdbdc6510425a65fc173d36e674d06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447215"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="64cea-104">Instrukcje: wpisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="64cea-104">How to: Write text to a file</span></span>
<span data-ttu-id="64cea-105">W tym temacie przedstawiono różne sposoby zapisywania tekstu do pliku dla aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="64cea-105">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="64cea-106">Następujące klasy i metody są zwykle używane do zapisywania tekstu do pliku:</span><span class="sxs-lookup"><span data-stu-id="64cea-106">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="64cea-107"><xref:System.IO.StreamWriter>zawiera metody do zapisu w pliku synchronicznie ( <xref:System.IO.StreamWriter.Write%2A> i <xref:System.IO.TextWriter.WriteLine%2A> ) lub asynchronicznie ( <xref:System.IO.StreamWriter.WriteAsync%2A> oraz <xref:System.IO.StreamWriter.WriteLineAsync%2A> ).</span><span class="sxs-lookup"><span data-stu-id="64cea-107"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="64cea-108"><xref:System.IO.File>zapewnia statyczne metody zapisywania tekstu do pliku, takie jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A> , lub do dołączania tekstu do pliku, takich jak <xref:System.IO.File.AppendAllLines%2A> , <xref:System.IO.File.AppendAllText%2A> , i <xref:System.IO.File.AppendText%2A> .</span><span class="sxs-lookup"><span data-stu-id="64cea-108"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="64cea-109"><xref:System.IO.Path>jest dla ciągów, które mają informacje o ścieżce pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="64cea-109"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="64cea-110">Zawiera ona <xref:System.IO.Path.Combine%2A> metodę i, w programie .NET Core 2,1 i nowszych, <xref:System.IO.Path.Join%2A> metody i <xref:System.IO.Path.TryJoin%2A> , które umożliwiają łączenie ciągów w celu utworzenia ścieżki pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="64cea-110">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="64cea-111">W poniższych przykładach przedstawiono tylko minimalną wymaganą ilość kodu.</span><span class="sxs-lookup"><span data-stu-id="64cea-111">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="64cea-112">Aplikacja rzeczywista zazwyczaj zapewnia bardziej niezawodne sprawdzanie błędów i obsługę wyjątków.</span><span class="sxs-lookup"><span data-stu-id="64cea-112">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="64cea-113">Przykład: synchronicznie zapisuj tekst za pomocą StreamWriter —</span><span class="sxs-lookup"><span data-stu-id="64cea-113">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="64cea-114">Poniższy przykład pokazuje, jak używać <xref:System.IO.StreamWriter> klasy do synchronicznego zapisywania tekstu do nowego pliku w jednym wierszu naraz.</span><span class="sxs-lookup"><span data-stu-id="64cea-114">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="64cea-115">Ponieważ <xref:System.IO.StreamWriter> obiekt jest zadeklarowany i skonkretyzowany w `using` instrukcji, <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda, która automatycznie opróżnia i zamyka strumień.</span><span class="sxs-lookup"><span data-stu-id="64cea-115">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="64cea-116">Przykład: synchronicznie dołączanie tekstu do StreamWriter —</span><span class="sxs-lookup"><span data-stu-id="64cea-116">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="64cea-117">Poniższy przykład pokazuje, jak używać <xref:System.IO.StreamWriter> klasy do synchronicznego dołączania tekstu do pliku tekstowego utworzonego w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="64cea-117">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="64cea-118">Przykład: asynchroniczny zapis tekstu z StreamWriter —</span><span class="sxs-lookup"><span data-stu-id="64cea-118">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="64cea-119">Poniższy przykład pokazuje, jak asynchronicznie pisać tekst do nowego pliku przy użyciu <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="64cea-119">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="64cea-120">Aby wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metodę, wywołanie metody musi znajdować się wewnątrz `async` metody.</span><span class="sxs-lookup"><span data-stu-id="64cea-120">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="64cea-121">Przykład w języku C# wymaga języka C# 7,1 lub nowszego, który dodaje obsługę `async` modyfikatora w punkcie wejścia programu.</span><span class="sxs-lookup"><span data-stu-id="64cea-121">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="64cea-122">Przykład: Napisz i Dołącz tekst z klasą plików</span><span class="sxs-lookup"><span data-stu-id="64cea-122">Example: Write and append text with the File class</span></span>

<span data-ttu-id="64cea-123">Poniższy przykład pokazuje, jak napisać tekst do nowego pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu <xref:System.IO.File> klasy.</span><span class="sxs-lookup"><span data-stu-id="64cea-123">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="64cea-124"><xref:System.IO.File.WriteAllText%2A>Metody i <xref:System.IO.File.AppendAllLines%2A> otwierają i zamykają plik automatycznie.</span><span class="sxs-lookup"><span data-stu-id="64cea-124">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="64cea-125">Jeśli ścieżka do <xref:System.IO.File.WriteAllText%2A> metody już istnieje, plik zostanie nadpisany.</span><span class="sxs-lookup"><span data-stu-id="64cea-125">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="64cea-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64cea-126">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="64cea-127">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="64cea-127">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="64cea-128">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="64cea-128">How to: Read and write to a newly-created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="64cea-129">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="64cea-129">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="64cea-130">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="64cea-130">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)
- [<span data-ttu-id="64cea-131">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="64cea-131">File and stream I/O</span></span>](index.md)
