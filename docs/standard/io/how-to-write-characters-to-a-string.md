---
title: 'Jak: Zapisywać znaki do ciągu'
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
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160286"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="fce13-102">Jak: Zapisywać znaki do ciągu</span><span class="sxs-lookup"><span data-stu-id="fce13-102">How to: Write characters to a string</span></span>
<span data-ttu-id="fce13-103">Poniższe przykłady kodu zapisują znaki synchronicznie lub asynchronicznie z tablicy znaków do ciągu.</span><span class="sxs-lookup"><span data-stu-id="fce13-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="fce13-104">Przykład: synchronicznie zapisuj znaki w aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="fce13-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="fce13-105">W poniższym <xref:System.IO.StringWriter> przykładzie użyto do zapisu <xref:System.Text.StringBuilder> pięciu znaków synchronicznie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="fce13-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="fce13-106">Przykład: Pisanie znaków asynchronicznie w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="fce13-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="fce13-107">Następnym przykładem jest kod za aplikacją WPF.</span><span class="sxs-lookup"><span data-stu-id="fce13-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="fce13-108">Na obciążenie okna przykład asynchronicznie odczytuje <xref:System.Windows.Controls.TextBox> wszystkie znaki z formantu i przechowuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="fce13-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="fce13-109">Następnie asynchronicznie zapisuje każdą literę lub znak odstępu <xref:System.Windows.Controls.TextBlock> do osobnego wiersza formantu.</span><span class="sxs-lookup"><span data-stu-id="fce13-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fce13-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fce13-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="fce13-111">Plik i strumień we/wy</span><span class="sxs-lookup"><span data-stu-id="fce13-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="fce13-112">We/Wy pliku asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="fce13-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="fce13-113">Jak: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="fce13-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="fce13-114">Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="fce13-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="fce13-115">Jak: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="fce13-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="fce13-116">Jak: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="fce13-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="fce13-117">Jak: Napisać tekst do pliku</span><span class="sxs-lookup"><span data-stu-id="fce13-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="fce13-118">Jak: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="fce13-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
