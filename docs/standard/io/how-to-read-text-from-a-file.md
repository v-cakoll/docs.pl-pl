---
title: 'Instrukcje: odczytywanie tekstu z pliku'
description: W tym artykule przedstawiono przykłady synchronicznego lub asynchronicznego odczytywania tekstu z pliku tekstowego przy użyciu klasy StreamReader w programie .NET dla aplikacji klasycznych.
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
ms.openlocfilehash: cbdeab3e907b34b6658eef7228fa6567ae198b08
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447059"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="18e8a-103">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="18e8a-103">How to: Read text from a file</span></span>
<span data-ttu-id="18e8a-104">W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych.</span><span class="sxs-lookup"><span data-stu-id="18e8a-104">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="18e8a-105">W obu przykładach podczas tworzenia wystąpienia <xref:System.IO.StreamReader> klasy należy podać względną lub bezwzględną ścieżkę do pliku.</span><span class="sxs-lookup"><span data-stu-id="18e8a-105">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="18e8a-106">Te przykłady kodu nie dotyczą tworzenia aplikacji uniwersalnych systemu Windows (platformy UWP), ponieważ środowisko wykonawcze systemu Windows udostępnia różne typy strumieni do odczytu i zapisu w plikach.</span><span class="sxs-lookup"><span data-stu-id="18e8a-106">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="18e8a-107">Przykład pokazujący, jak odczytać tekst z pliku w aplikacji platformy UWP, zobacz [Szybki Start: odczytywanie i zapisywanie plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="18e8a-107">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="18e8a-108">Przykłady pokazujące sposób konwersji między strumieniami .NET Framework i strumieniami środowisko wykonawcze systemu Windows można znaleźć w temacie [How to: converting in .NET Framework Streams and środowisko wykonawcze systemu Windows](how-to-convert-between-dotnet-streams-and-winrt-streams.md)Streams.</span><span class="sxs-lookup"><span data-stu-id="18e8a-108">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="18e8a-109">Przykład: Synchroniczne odczyty w aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="18e8a-109">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="18e8a-110">W poniższym przykładzie pokazano synchroniczną operację odczytu w aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="18e8a-110">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="18e8a-111">Ten przykład otwiera plik tekstowy przy użyciu czytnika strumienia, kopiuje zawartość do ciągu i wyprowadza ciąg do konsoli.</span><span class="sxs-lookup"><span data-stu-id="18e8a-111">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="18e8a-112">W przykładzie przyjęto założenie, że plik o nazwie *TestFile. txt* już istnieje w tym samym folderze, w którym znajduje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="18e8a-112">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="18e8a-113">Przykład: asynchroniczny odczyt w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="18e8a-113">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="18e8a-114">W poniższym przykładzie pokazano asynchroniczne operacje odczytu w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="18e8a-114">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="18e8a-115">W przykładzie przyjęto założenie, że plik o nazwie *TestFile. txt* już istnieje w tym samym folderze, w którym znajduje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="18e8a-115">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="18e8a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18e8a-116">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="18e8a-117">Asynchroniczne operacje we/wy pliku</span><span class="sxs-lookup"><span data-stu-id="18e8a-117">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="18e8a-118">[Instrukcje: Tworzenie listy katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="18e8a-118">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="18e8a-119">Szybki Start: odczytywanie i zapisywanie plików</span><span class="sxs-lookup"><span data-stu-id="18e8a-119">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="18e8a-120">Instrukcje: konwertowanie między strumieniami .NET Framework a strumieniami środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="18e8a-120">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="18e8a-121">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="18e8a-121">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="18e8a-122">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="18e8a-122">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="18e8a-123">Instrukcje: wpisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="18e8a-123">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="18e8a-124">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="18e8a-124">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="18e8a-125">Instrukcje: Wpisywanie znaków do ciągu</span><span class="sxs-lookup"><span data-stu-id="18e8a-125">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="18e8a-126">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="18e8a-126">File and stream I/O</span></span>](index.md)
