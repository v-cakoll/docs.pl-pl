---
title: 'Instrukcje: Zapisywanie znaków w ciągu'
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
ms.openlocfilehash: 125c8ba03c4d1006535dd1e10cbd162b32fede4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740986"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="28fe1-102">Instrukcje: Zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="28fe1-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="28fe1-103">Poniższe przykłady kodu zapisywać znaki synchronicznie i asynchronicznie z tablicy znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="28fe1-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28fe1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="28fe1-104">Example</span></span>  
 <span data-ttu-id="28fe1-105">Poniższy przykład zapisuje 5 znaków synchronicznie z tablicy na ciąg.</span><span class="sxs-lookup"><span data-stu-id="28fe1-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="28fe1-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="28fe1-106">Example</span></span>  
 <span data-ttu-id="28fe1-107">Następny przykład odczytuje wszystkie znaki asynchronicznie z <xref:System.Windows.Controls.TextBox> kontrolować i przechowuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="28fe1-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="28fe1-108">Następnie asynchronicznie zapisuje każdy literę lub biały znak w osobnym wierszu następuje znak końca wiersza, aby <xref:System.Windows.Controls.TextBlock> kontroli.</span><span class="sxs-lookup"><span data-stu-id="28fe1-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="28fe1-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28fe1-109">See also</span></span>

- <xref:System.IO.StringWriter>
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="28fe1-110">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="28fe1-110">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="28fe1-111">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="28fe1-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="28fe1-112">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="28fe1-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="28fe1-113">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="28fe1-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="28fe1-114">Instrukcje: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="28fe1-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="28fe1-115">Instrukcje: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="28fe1-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="28fe1-116">Instrukcje: Zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="28fe1-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="28fe1-117">Instrukcje: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="28fe1-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
