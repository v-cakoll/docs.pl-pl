---
title: 'Instrukcje: Odczytywanie znaków z ciągu'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e890e4172e645e9919ea88ec5835aaed7432c0c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947189"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="477ac-102">Instrukcje: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="477ac-102">How to: Read characters from a string</span></span>
<span data-ttu-id="477ac-103">Następujące przykłady kodu przedstawiają sposób synchronicznie lub asynchronicznie odczytywanie znaków z ciągu.</span><span class="sxs-lookup"><span data-stu-id="477ac-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="477ac-104">Przykład: Odczytywanie znaków synchronicznie</span><span class="sxs-lookup"><span data-stu-id="477ac-104">Example: Read characters synchronously</span></span> 
 <span data-ttu-id="477ac-105">W tym przykładzie odczytuje 13 znaków synchronicznie z ciągu, przechowuje je w tablicy, a następnie wyświetli je.</span><span class="sxs-lookup"><span data-stu-id="477ac-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="477ac-106">Następnie przykład odczytuje pozostałe znaki do ciągu, przechowuje je w tablicy, zaczynając od szóstego elementu i wyświetla zawartość tablicy.</span><span class="sxs-lookup"><span data-stu-id="477ac-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="477ac-107">Przykład: Odczytywanie znaków asynchronicznie</span><span class="sxs-lookup"><span data-stu-id="477ac-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="477ac-108">Następny przykład jest kod związany z aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="477ac-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="477ac-109">Po załadowaniu okna przykład asynchronicznie odczytuje wszystkie znaki od <xref:System.Windows.Controls.TextBox> kontroli i przechowuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="477ac-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="477ac-110">Następnie asynchronicznie zapisuje każdy znak litera lub znak odstępu w osobnym wierszu <xref:System.Windows.Controls.TextBlock> kontroli.</span><span class="sxs-lookup"><span data-stu-id="477ac-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="477ac-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="477ac-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="477ac-112">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="477ac-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="477ac-113">[Instrukcje: Utwórz listę katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="477ac-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="477ac-114">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="477ac-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="477ac-115">Instrukcje: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="477ac-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="477ac-116">Instrukcje: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="477ac-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="477ac-117">Instrukcje: Zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="477ac-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="477ac-118">Instrukcje: Zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="477ac-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="477ac-119">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="477ac-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
