---
title: 'Instrukcje: Zapisywanie znaków w ciągu'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb35c61b34fa571f35da6691ebe7fa2516eb2df1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947098"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="9f5d8-102">Instrukcje: Zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="9f5d8-102">How to: Write characters to a string</span></span>
<span data-ttu-id="9f5d8-103">Poniższe przykłady kodu zapisywać znaki synchronicznie lub asynchronicznie z tablicy znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="9f5d8-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="9f5d8-104">Przykład: Zapisywanie znaków synchronicznie w aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="9f5d8-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="9f5d8-105">W poniższym przykładzie użyto <xref:System.IO.StringWriter> do zapisu synchronicznego na pięć znaków <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9f5d8-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span> 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="9f5d8-106">Przykład: Asynchronicznie zapisywanie znaków w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="9f5d8-106">Example: Write characters asynchronously in a WPF app</span></span> 
 <span data-ttu-id="9f5d8-107">Następny przykład jest kod związany z aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="9f5d8-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="9f5d8-108">Po załadowaniu okna przykład asynchronicznie odczytuje wszystkie znaki od <xref:System.Windows.Controls.TextBox> kontroli i przechowuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="9f5d8-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="9f5d8-109">Następnie asynchronicznie zapisuje każdy znak litera lub znak odstępu w osobnym wierszu <xref:System.Windows.Controls.TextBlock> kontroli.</span><span class="sxs-lookup"><span data-stu-id="9f5d8-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9f5d8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f5d8-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="9f5d8-111">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="9f5d8-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="9f5d8-112">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="9f5d8-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="9f5d8-113">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="9f5d8-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="9f5d8-114">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="9f5d8-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="9f5d8-115">Instrukcje: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="9f5d8-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="9f5d8-116">Instrukcje: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="9f5d8-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="9f5d8-117">Instrukcje: Zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="9f5d8-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="9f5d8-118">Instrukcje: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="9f5d8-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
