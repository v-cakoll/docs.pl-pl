---
title: 'Instrukcje: Wpisywanie znaków do ciągu'
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
ms.openlocfilehash: 04fc21c452258a88292a886d952353ac55573121
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288254"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="baa03-102">Instrukcje: Wpisywanie znaków do ciągu</span><span class="sxs-lookup"><span data-stu-id="baa03-102">How to: Write characters to a string</span></span>
<span data-ttu-id="baa03-103">Poniższe przykłady kodu zapisują znaki synchronicznie lub asynchronicznie z tablicy znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="baa03-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="baa03-104">Przykład: zapisuj znaki synchronicznie w aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="baa03-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="baa03-105">Poniższy przykład używa <xref:System.IO.StringWriter> do zapisu pięciu znaków synchronicznie do <xref:System.Text.StringBuilder> obiektu.</span><span class="sxs-lookup"><span data-stu-id="baa03-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="baa03-106">Przykład: zapisuj znaki asynchronicznie w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="baa03-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="baa03-107">Następny przykład to kod związany z aplikacją WPF.</span><span class="sxs-lookup"><span data-stu-id="baa03-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="baa03-108">W przypadku ładowania okna przykład Asynchronicznie odczytuje wszystkie znaki z <xref:System.Windows.Controls.TextBox> kontrolki i zapisuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="baa03-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="baa03-109">Następnie asynchronicznie zapisuje każdą literę lub biały znak w osobnym wierszu <xref:System.Windows.Controls.TextBlock> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="baa03-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="baa03-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baa03-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="baa03-111">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="baa03-111">File and stream I/O</span></span>](index.md)  
- [<span data-ttu-id="baa03-112">Asynchroniczne operacje we/wy pliku</span><span class="sxs-lookup"><span data-stu-id="baa03-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- [<span data-ttu-id="baa03-113">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="baa03-113">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="baa03-114">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="baa03-114">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="baa03-115">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="baa03-115">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="baa03-116">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="baa03-116">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="baa03-117">Instrukcje: wpisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="baa03-117">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="baa03-118">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="baa03-118">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)
