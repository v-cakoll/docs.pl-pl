---
title: 'Porady: odczytywanie znaków z ciągów'
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
ms.openlocfilehash: c2e128f1011b6daa5c0e8b62252c8adc3175586c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572778"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="1f286-102">Porady: odczytywanie znaków z ciągów</span><span class="sxs-lookup"><span data-stu-id="1f286-102">How to: Read Characters from a String</span></span>
<span data-ttu-id="1f286-103">W poniższych przykładach kodu przedstawiają sposób synchronicznego i asynchronicznego odczytywanie znaków z ciągu.</span><span class="sxs-lookup"><span data-stu-id="1f286-103">The following code examples show how to read characters synchronously and asynchronously from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f286-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f286-104">Example</span></span>  
 <span data-ttu-id="1f286-105">Ten przykład odczytuje 13 znaków synchronicznie z ciągiem i przechowuje je w tablicy i wyświetla te znaki.</span><span class="sxs-lookup"><span data-stu-id="1f286-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays those characters.</span></span> <span data-ttu-id="1f286-106">Następnie odczytuje pozostałych znaków w ciągu, przechowuje je w tablicy, zaczynając od elementu szóstego i wyświetla zawartość tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f286-106">It then reads the remaining characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="1f286-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f286-107">Example</span></span>  
 <span data-ttu-id="1f286-108">Kolejnym przykładzie odczytuje wszystkie znaki asynchronicznie od <xref:System.Windows.Controls.TextBox> kontroli i przechowuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f286-108">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="1f286-109">Następnie asynchronicznie zapisuje każdego znaku literą lub biały znak w osobnym wierszu następuje podział wiersza do <xref:System.Windows.Controls.TextBlock> formantu.</span><span class="sxs-lookup"><span data-stu-id="1f286-109">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1f286-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f286-110">See Also</span></span>  
 <xref:System.IO.StringReader>  
 <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1f286-111">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="1f286-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="1f286-112">NIB: Porady: Tworzenie listy katalogów</span><span class="sxs-lookup"><span data-stu-id="1f286-112">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [<span data-ttu-id="1f286-113">Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="1f286-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="1f286-114">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="1f286-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="1f286-115">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="1f286-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="1f286-116">Instrukcje: zapisywanie tekstu w pliku</span><span class="sxs-lookup"><span data-stu-id="1f286-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="1f286-117">Instrukcje: zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="1f286-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="1f286-118">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="1f286-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
