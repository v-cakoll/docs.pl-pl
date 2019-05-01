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
ms.openlocfilehash: 93d87dc98284fad6b8159f681f7d99ce460d60d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947085"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="b52f4-102">Instrukcje: Zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="b52f4-102">How to: Write text to a file</span></span>
<span data-ttu-id="b52f4-103">W tym temacie przedstawiono różne sposoby zapisywanie tekstu do pliku dla aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b52f4-103">This topic shows different ways to write text to a file for a .NET app.</span></span> 

<span data-ttu-id="b52f4-104">Następujące klasy i metody są zwykle używane do zapisywanie tekstu do pliku:</span><span class="sxs-lookup"><span data-stu-id="b52f4-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="b52f4-105"><xref:System.IO.StreamWriter> zawiera metody do zapisu do pliku synchronicznie (<xref:System.IO.StreamWriter.Write%2A> i <xref:System.IO.TextWriter.WriteLine%2A>) lub asynchronicznie (<xref:System.IO.StreamWriter.WriteAsync%2A> i <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="b52f4-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="b52f4-106"><xref:System.IO.File> udostępnia metody statyczne do zapisywanie tekstu do pliku, taką jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A>, lub dołączyć tekst do pliku, taką jak <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, i <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="b52f4-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="b52f4-107"><xref:System.IO.Path> Służy do ciągów zawierających informacje o ścieżce pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="b52f4-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="b52f4-108">Zawiera on <xref:System.IO.Path.Combine%2A> metody i, w programie .NET Core 2.1 i nowsze, <xref:System.IO.Path.Join%2A> i <xref:System.IO.Path.TryJoin%2A> metod, które umożliwiają łączenie ciągów, aby zbudować ścieżki pliku lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="b52f4-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="b52f4-109">W poniższych przykładach pokazano minimalnej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="b52f4-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="b52f4-110">Aplikacja rzeczywistych zwykle zapewnia bardziej niezawodne sprawdzanie błędów i wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b52f4-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="b52f4-111">Przykład: Synchronicznie wpisać tekst za pomocą StreamWriter</span><span class="sxs-lookup"><span data-stu-id="b52f4-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="b52f4-112">Poniższy przykład pokazuje, jak używać <xref:System.IO.StreamWriter> klasy synchronicznie zapisywanie tekstu do nowego jeden wiersz pliku naraz.</span><span class="sxs-lookup"><span data-stu-id="b52f4-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="b52f4-113">Ponieważ <xref:System.IO.StreamWriter> obiektu jest zadeklarowana i tworzone w `using` instrukcji <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda, która automatycznie opróżnia i zamyka strumienia.</span><span class="sxs-lookup"><span data-stu-id="b52f4-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="b52f4-114">Przykład: Synchronicznie dołączyć tekst za pomocą StreamWriter</span><span class="sxs-lookup"><span data-stu-id="b52f4-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="b52f4-115">Poniższy przykład pokazuje, jak używać <xref:System.IO.StreamWriter> klasy synchronicznie dołączyć tekst do pliku tekstowego, utworzony w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b52f4-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="b52f4-116">Przykład: Asynchronicznie zapis tekstu za pomocą StreamWriter</span><span class="sxs-lookup"><span data-stu-id="b52f4-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="b52f4-117">Poniższy przykład pokazuje, jak asynchronicznie zapisywanie tekstu do nowego pliku przy użyciu <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="b52f4-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="b52f4-118">Aby wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metody wywołania metody które muszą znajdować się w `async` metody.</span><span class="sxs-lookup"><span data-stu-id="b52f4-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="b52f4-119">C# Przykład wymaga C# 7.1 lub nowszej, który dodaje obsługę `async` modyfikator dla punktu wejścia programu.</span><span class="sxs-lookup"><span data-stu-id="b52f4-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span> 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="b52f4-120">Przykład: Pisanie i dołączyć tekst z klasą plików</span><span class="sxs-lookup"><span data-stu-id="b52f4-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="b52f4-121">Poniższy przykład pokazuje, jak zapisywanie tekstu do nowego pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu <xref:System.IO.File> klasy.</span><span class="sxs-lookup"><span data-stu-id="b52f4-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="b52f4-122"><xref:System.IO.File.WriteAllText%2A> i <xref:System.IO.File.AppendAllLines%2A> metod Otwórz i zamknij plik automatycznie.</span><span class="sxs-lookup"><span data-stu-id="b52f4-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="b52f4-123">Jeśli ścieżka uzyskiwanie <xref:System.IO.File.WriteAllText%2A> metody już istnieje, zostanie on zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="b52f4-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="b52f4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b52f4-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b52f4-125">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="b52f4-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="b52f4-126">Instrukcje: Odczyt i zapis do pliku danych nowo utworzone</span><span class="sxs-lookup"><span data-stu-id="b52f4-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="b52f4-127">Instrukcje: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="b52f4-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="b52f4-128">Instrukcje: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="b52f4-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="b52f4-129">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="b52f4-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)