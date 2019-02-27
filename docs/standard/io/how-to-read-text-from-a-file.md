---
title: 'Instrukcje: Odczytywanie tekstu z pliku'
ms.date: 01/03/2019
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
ms.openlocfilehash: 7330c209ce6514459d3ab1dd58dc1c80b1978a56
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56834956"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="8fb3b-102">Instrukcje: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="8fb3b-102">How to: Read text from a file</span></span>
<span data-ttu-id="8fb3b-103">W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych.</span><span class="sxs-lookup"><span data-stu-id="8fb3b-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="8fb3b-104">W obu przykładach podczas tworzenia wystąpienia klasy <xref:System.IO.StreamReader> należy dostarczyć względną lub bezwzględną ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="8fb3b-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="8fb3b-105">Te przykłady kodu nie dotyczą projektowania dla aplikacji Universal Windows (UWP), ponieważ środowisko wykonawcze Windows oferuje typy strumieni różnych do odczytu i zapisu do plików.</span><span class="sxs-lookup"><span data-stu-id="8fb3b-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="8fb3b-106">Na przykład, który pokazuje, jak odczytać tekst z pliku w aplikacji platformy uniwersalnej systemu Windows, zobacz [Szybki Start: Odczyt i zapis plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="8fb3b-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="8fb3b-107">Przykłady pokazujące, jak przeprowadzać konwersję między strumieniami programu .NET Framework i strumieni środowiska wykonawczego Windows, zobacz [jak: Konwertowanie między strumieniami programu .NET Framework i strumieni środowiska wykonawczego Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="8fb3b-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="8fb3b-108">Przykład: Synchroniczne odczytu w aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="8fb3b-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="8fb3b-109">Poniższy przykład przedstawia operację odczytu synchronicznego aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="8fb3b-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="8fb3b-110">W tym przykładzie otwiera plik tekstowy, przy użyciu czytnik strumienia kopiuje zawartość na ciąg i wyświetla ciąg do konsoli.</span><span class="sxs-lookup"><span data-stu-id="8fb3b-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8fb3b-111">W przykładzie założono, że plik o nazwie *TestFile.txt* już istnieje w tym samym folderze co aplikacja.</span><span class="sxs-lookup"><span data-stu-id="8fb3b-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="8fb3b-112">Przykład: Asynchroniczne odczytu w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="8fb3b-112">Example: Asynchronous read in a WPF app</span></span> 
 <span data-ttu-id="8fb3b-113">Poniższy przykład przedstawia operację odczytu asynchronicznego w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="8fb3b-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8fb3b-114">W przykładzie założono, że plik o nazwie *TestFile.txt* już istnieje w tym samym folderze co aplikacja.</span><span class="sxs-lookup"><span data-stu-id="8fb3b-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8fb3b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fb3b-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="8fb3b-116">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="8fb3b-116">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="8fb3b-117">[Instrukcje: Utwórz listę katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8fb3b-117">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="8fb3b-118">Szybki start: Odczyt i zapis plików</span><span class="sxs-lookup"><span data-stu-id="8fb3b-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="8fb3b-119">Instrukcje: Konwertowanie między strumieniami programu .NET Framework i strumieni środowiska wykonawczego Windows</span><span class="sxs-lookup"><span data-stu-id="8fb3b-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="8fb3b-120">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="8fb3b-120">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="8fb3b-121">Instrukcje: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="8fb3b-121">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="8fb3b-122">Instrukcje: Zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="8fb3b-122">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="8fb3b-123">Instrukcje: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="8fb3b-123">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="8fb3b-124">Instrukcje: Zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="8fb3b-124">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="8fb3b-125">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="8fb3b-125">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
