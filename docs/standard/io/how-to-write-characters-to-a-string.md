---
title: "Porady: zapisywanie znaków w ciągach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 336a7fec5e64cc0c45566631c73928e0c1d40a5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="38a3b-102">Porady: zapisywanie znaków w ciągach</span><span class="sxs-lookup"><span data-stu-id="38a3b-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="38a3b-103">W poniższych przykładach kodu wpisz znaki synchronicznego i asynchronicznego z tablicy znaków w ciągu.</span><span class="sxs-lookup"><span data-stu-id="38a3b-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38a3b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="38a3b-104">Example</span></span>  
 <span data-ttu-id="38a3b-105">Poniższy przykład 5 znaków wykonuje synchroniczny zapis z tablicy na ciąg.</span><span class="sxs-lookup"><span data-stu-id="38a3b-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="38a3b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="38a3b-106">Example</span></span>  
 <span data-ttu-id="38a3b-107">Kolejnym przykładzie odczytuje wszystkie znaki asynchronicznie od <xref:System.Windows.Controls.TextBox> kontroli i przechowuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="38a3b-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="38a3b-108">Następnie asynchronicznie zapisuje każdego znaku literą lub biały znak w osobnym wierszu następuje podział wiersza do <xref:System.Windows.Controls.TextBlock> formantu.</span><span class="sxs-lookup"><span data-stu-id="38a3b-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="38a3b-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38a3b-109">See Also</span></span>  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="38a3b-110">Plik i strumienia I-O</span><span class="sxs-lookup"><span data-stu-id="38a3b-110">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="38a3b-111">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="38a3b-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="38a3b-112">Porady: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="38a3b-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="38a3b-113">Porady: Odczyt i zapis do pliku danych nowo utworzony</span><span class="sxs-lookup"><span data-stu-id="38a3b-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="38a3b-114">Porady: otwieranie i Dołącz do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="38a3b-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="38a3b-115">Porady: Odczyt tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="38a3b-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="38a3b-116">Porady: zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="38a3b-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="38a3b-117">Porady: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="38a3b-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
