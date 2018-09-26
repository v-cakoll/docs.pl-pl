---
title: 'Porady: odczyt tekstu z pliku'
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f979f3d09079f36d12408d0a82ef58e603da859
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203180"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="c8017-102">Porady: odczyt tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="c8017-102">How to: Read Text from a File</span></span>
<span data-ttu-id="c8017-103">W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych.</span><span class="sxs-lookup"><span data-stu-id="c8017-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="c8017-104">W obu przykładach podczas tworzenia wystąpienia klasy <xref:System.IO.StreamReader> należy dostarczyć względną lub bezwzględną ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="c8017-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="c8017-105">W poniższych przykładach założono, że plik o nazwie TestFile.txt znajduje się w folderze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8017-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="c8017-106">Te przykłady kodu nie dotyczą projektowania dla aplikacji Windows Store Apps, ponieważ środowisko wykonawcze Windows oferuje typy strumieni różnych do odczytu i zapisu do plików.</span><span class="sxs-lookup"><span data-stu-id="c8017-106">These code examples do not apply to developing for Windows Store Apps because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="c8017-107">Na przykład, który pokazuje, jak odczytać tekst z pliku w aplikacji Windows Store, zobacz [Szybki Start: odczytywanie i zapisywanie plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="c8017-107">For an example that shows how to read text from a file in a Windows Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="c8017-108">Przykłady pokazujące, jak przeprowadzać konwersję między strumieniami programu .NET Framework i strumieni środowiska wykonawczego Windows, zobacz [porady: konwertowanie między .NET Framework i strumieni środowiska wykonawczego Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="c8017-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8017-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8017-109">Example</span></span>  
 <span data-ttu-id="c8017-110">Poniższy przykład przedstawia operację odczytu synchronicznego przy użyciu aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="c8017-110">The following example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="c8017-111">W tym przykładzie plik tekstowy jest otwierane przy użyciu czytnik strumienia, zawartość jest kopiowana do ciągu i ciąg jest dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="c8017-111">In this example, the text file is opened using a stream reader, the contents are copied to a string, and the string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="c8017-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8017-112">Example</span></span>  
 <span data-ttu-id="c8017-113">Poniższy przykład przedstawia operację odczytu asynchronicznego w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="c8017-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c8017-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8017-114">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="c8017-115">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="c8017-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="c8017-116">NIB: Instrukcje: Tworzenie listy katalogów</span><span class="sxs-lookup"><span data-stu-id="c8017-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [<span data-ttu-id="c8017-117">Szybki Start: Odczyt i zapis plików</span><span class="sxs-lookup"><span data-stu-id="c8017-117">Quickstart: Reading and writing files</span></span>](https://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
- [<span data-ttu-id="c8017-118">Instrukcje: konwersja strumieni platformy .NET Framework i strumieni środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c8017-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="c8017-119">Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="c8017-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="c8017-120">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="c8017-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="c8017-121">Instrukcje: zapisywanie tekstu w pliku</span><span class="sxs-lookup"><span data-stu-id="c8017-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="c8017-122">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="c8017-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="c8017-123">Instrukcje: zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="c8017-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="c8017-124">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="c8017-124">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
