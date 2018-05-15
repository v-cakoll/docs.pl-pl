---
title: 'Porady: zapisywanie znaków w ciągach'
ms.date: 03/30/2017
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
ms.openlocfilehash: 969a511f6b3d93450866d7a85cf2bcb198d2581e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="5885c-102">Porady: zapisywanie znaków w ciągach</span><span class="sxs-lookup"><span data-stu-id="5885c-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="5885c-103">W poniższych przykładach kodu wpisz znaki synchronicznego i asynchronicznego z tablicy znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="5885c-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5885c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5885c-104">Example</span></span>  
 <span data-ttu-id="5885c-105">Poniższy przykład 5 znaków wykonuje synchroniczny zapis z tablicy na ciąg.</span><span class="sxs-lookup"><span data-stu-id="5885c-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="5885c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5885c-106">Example</span></span>  
 <span data-ttu-id="5885c-107">Kolejnym przykładzie odczytuje wszystkie znaki asynchronicznie od <xref:System.Windows.Controls.TextBox> kontroli i przechowuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="5885c-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="5885c-108">Następnie asynchronicznie zapisuje każdego znaku literą lub biały znak w osobnym wierszu następuje podział wiersza do <xref:System.Windows.Controls.TextBlock> formantu.</span><span class="sxs-lookup"><span data-stu-id="5885c-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5885c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5885c-109">See Also</span></span>  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="5885c-110">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="5885c-110">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="5885c-111">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="5885c-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="5885c-112">Instrukcje: wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="5885c-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="5885c-113">Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="5885c-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="5885c-114">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="5885c-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="5885c-115">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="5885c-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="5885c-116">Instrukcje: zapisywanie tekstu w pliku</span><span class="sxs-lookup"><span data-stu-id="5885c-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="5885c-117">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="5885c-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
