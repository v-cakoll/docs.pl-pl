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
ms.openlocfilehash: b7c54e5e55770f3df44819cdf6d2d2c866f7e0fc
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298165"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="1585d-102">Porady: odczyt tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="1585d-102">How to: Read Text from a File</span></span>
<span data-ttu-id="1585d-103">W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych.</span><span class="sxs-lookup"><span data-stu-id="1585d-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="1585d-104">W obu przykładach, podczas tworzenia wystąpienia <xref:System.IO.StreamReader> klasy, podaj względna lub bezwzględna ścieżka do pliku.</span><span class="sxs-lookup"><span data-stu-id="1585d-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="1585d-105">W poniższych przykładach założono, że plik o nazwie TestFile.txt znajduje się w folderze aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1585d-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="1585d-106">Te przykłady kodu nie dotyczą tworzenie aplikacji dla aplikacji ze Sklepu Windows, ponieważ środowisko wykonawcze systemu Windows zapewnia strumienia różne typy odczytywanie i zapisywanie do plików.</span><span class="sxs-lookup"><span data-stu-id="1585d-106">These code examples do not apply to developing for Windows Store Apps because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="1585d-107">Przykład pokazujący sposób odczyt tekstu z pliku w aplikacji ze Sklepu Windows, temacie [Szybki Start: Odczyt i zapis plików](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="1585d-107">For an example that shows how to read text from a file in a Windows Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="1585d-108">Przykłady, które pokazują, jak wykonać konwersji między .NET Framework i strumieni środowiska wykonawczego systemu Windows, temacie [porady: konwertowanie między .NET Framework i strumieni środowiska wykonawczego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="1585d-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1585d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1585d-109">Example</span></span>  
 <span data-ttu-id="1585d-110">W poniższym przykładzie przedstawiono synchronicznych operacji odczytu w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="1585d-110">The following example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="1585d-111">W tym przykładzie pliku tekstowego jest otwarty przy użyciu czytnik strumienia zawartości są kopiowane do ciągu i ciągu jest dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1585d-111">In this example, the text file is opened using a stream reader, the contents are copied to a string, and the string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="1585d-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1585d-112">Example</span></span>  
 <span data-ttu-id="1585d-113">Poniższy przykład przedstawia operację asynchroniczną odczytu w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="1585d-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1585d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1585d-114">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1585d-115">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="1585d-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="1585d-116">NIB: Porady: Tworzenie listy katalogów</span><span class="sxs-lookup"><span data-stu-id="1585d-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [<span data-ttu-id="1585d-117">Szybki Start: Odczyt i zapis plików</span><span class="sxs-lookup"><span data-stu-id="1585d-117">Quickstart: Reading and writing files</span></span>](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [<span data-ttu-id="1585d-118">Instrukcje: konwersja strumieni platformy .NET Framework i strumieni środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1585d-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [<span data-ttu-id="1585d-119">Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="1585d-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="1585d-120">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="1585d-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="1585d-121">Instrukcje: zapisywanie tekstu w pliku</span><span class="sxs-lookup"><span data-stu-id="1585d-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="1585d-122">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="1585d-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="1585d-123">Instrukcje: zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="1585d-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="1585d-124">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="1585d-124">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
