---
title: 'Jak: Odczytywanie tekstu z pliku'
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
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155727"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="967b8-102">Jak: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="967b8-102">How to: Read text from a file</span></span>
<span data-ttu-id="967b8-103">W poniższych przykładach pokazano, jak odczytać tekst synchronicznie i asynchronicznie z pliku tekstowego przy użyciu platformy .NET dla aplikacji komputerowych.</span><span class="sxs-lookup"><span data-stu-id="967b8-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="967b8-104">W obu przykładach podczas tworzenia wystąpienia <xref:System.IO.StreamReader> klasy, należy podać ścieżkę względną lub bezwzględną do pliku.</span><span class="sxs-lookup"><span data-stu-id="967b8-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="967b8-105">Te przykłady kodu nie mają zastosowania do tworzenia aplikacji dla systemu Uniwersalnego systemu Windows (UWP), ponieważ środowisko uruchomieniowe systemu Windows udostępnia różne typy strumieni do odczytu i zapisu w plikach.</span><span class="sxs-lookup"><span data-stu-id="967b8-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="967b8-106">Na przykład, który pokazuje, jak odczytywać tekst z pliku w aplikacji systemu uwp, zobacz [Szybki start: Odczytywanie i zapisywanie plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="967b8-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="967b8-107">Przykłady, które pokazują, jak konwertować między strumieniami .NET Framework i strumieniśrodowiska uruchomieniowego systemu Windows, zobacz [Jak: Konwertować między strumieniami .NET Framework i strumieniami środowiska uruchomieniowego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="967b8-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="967b8-108">Przykład: Odczyt synchroniczny w aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="967b8-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="967b8-109">W poniższym przykładzie przedstawiono synchroniczną operację odczytu w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="967b8-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="967b8-110">W tym przykładzie otwiera plik tekstowy przy użyciu czytnika strumienia, kopiuje zawartość do ciągu i wyprowadza ciąg do konsoli.</span><span class="sxs-lookup"><span data-stu-id="967b8-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="967b8-111">W przykładzie przyjęto założenie, że plik o nazwie *TestFile.txt* już istnieje w tym samym folderze co aplikacja.</span><span class="sxs-lookup"><span data-stu-id="967b8-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="967b8-112">Przykład: Odczyt asynchroniczny w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="967b8-112">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="967b8-113">W poniższym przykładzie przedstawiono operację odczytu asynchronicznego w aplikacji Programu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="967b8-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="967b8-114">W przykładzie przyjęto założenie, że plik o nazwie *TestFile.txt* już istnieje w tym samym folderze co aplikacja.</span><span class="sxs-lookup"><span data-stu-id="967b8-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="967b8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="967b8-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="967b8-116">We/Wy pliku asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="967b8-116">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="967b8-117">[Jak: Tworzenie listy katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="967b8-117">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="967b8-118">Szybki start: czytanie i zapisywanie plików</span><span class="sxs-lookup"><span data-stu-id="967b8-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="967b8-119">Jak: Konwertować między strumieniami programu .NET Framework a strumieniami środowiska uruchomieniowego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="967b8-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="967b8-120">Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="967b8-120">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="967b8-121">Jak: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="967b8-121">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="967b8-122">Jak: Napisać tekst do pliku</span><span class="sxs-lookup"><span data-stu-id="967b8-122">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="967b8-123">Jak: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="967b8-123">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="967b8-124">Jak: Zapisywać znaki do ciągu</span><span class="sxs-lookup"><span data-stu-id="967b8-124">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="967b8-125">Plik i strumień we/wy</span><span class="sxs-lookup"><span data-stu-id="967b8-125">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
