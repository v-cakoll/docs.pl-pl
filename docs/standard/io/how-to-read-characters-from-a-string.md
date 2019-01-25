---
title: 'Instrukcje: Odczytywanie znaków z ciągu'
ms.date: 03/30/2017
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
ms.openlocfilehash: cbf213c783d1688e9168265cedc27d2ac7a5a96d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504820"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="d8da7-102">Instrukcje: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="d8da7-102">How to: Read Characters from a String</span></span>
<span data-ttu-id="d8da7-103">Następujące przykłady kodu przedstawiają sposób synchronicznie i asynchronicznie odczytywanie znaków z ciągu.</span><span class="sxs-lookup"><span data-stu-id="d8da7-103">The following code examples show how to read characters synchronously and asynchronously from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8da7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8da7-104">Example</span></span>  
 <span data-ttu-id="d8da7-105">W tym przykładzie odczytuje 13 znaków synchronicznie z ciągu, przechowuje je w tablicy i wyświetla te znaki.</span><span class="sxs-lookup"><span data-stu-id="d8da7-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays those characters.</span></span> <span data-ttu-id="d8da7-106">Następnie odczytuje pozostałych znaków w ciągu, przechowuje je w tablicy, zaczynając od szóstego elementu i wyświetla zawartość tablicy.</span><span class="sxs-lookup"><span data-stu-id="d8da7-106">It then reads the remaining characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d8da7-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8da7-107">Example</span></span>  
 <span data-ttu-id="d8da7-108">Następny przykład odczytuje wszystkie znaki asynchronicznie z <xref:System.Windows.Controls.TextBox> kontrolować i przechowuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d8da7-108">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="d8da7-109">Następnie asynchronicznie zapisuje każdy literę lub biały znak w osobnym wierszu następuje znak końca wiersza, aby <xref:System.Windows.Controls.TextBlock> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d8da7-109">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d8da7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8da7-110">See also</span></span>

- <xref:System.IO.StringReader>
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d8da7-111">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="d8da7-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="d8da7-112">NIB: Instrukcje: Utwórz listę katalogów</span><span class="sxs-lookup"><span data-stu-id="d8da7-112">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)
- [<span data-ttu-id="d8da7-113">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="d8da7-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="d8da7-114">Instrukcje: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="d8da7-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="d8da7-115">Instrukcje: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="d8da7-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="d8da7-116">Instrukcje: Zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="d8da7-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="d8da7-117">Instrukcje: Zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="d8da7-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [<span data-ttu-id="d8da7-118">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="d8da7-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
