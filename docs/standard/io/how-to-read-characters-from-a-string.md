---
title: 'Instrukcje: odczytywanie znaków z ciągu'
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
ms.openlocfilehash: 0c3516c4abadfd22609c3568beffc14e027ef69e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706676"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="ac444-102">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="ac444-102">How to: Read characters from a string</span></span>
<span data-ttu-id="ac444-103">Poniższy przykład kodu pokazuje, jak odczytywać znaki synchronicznie lub asynchronicznie z ciągu.</span><span class="sxs-lookup"><span data-stu-id="ac444-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="ac444-104">Przykład: Odczytaj znaki synchronicznie</span><span class="sxs-lookup"><span data-stu-id="ac444-104">Example: Read characters synchronously</span></span> 
 <span data-ttu-id="ac444-105">Ten przykład odczytuje 13 znaków synchronicznie z ciągu, zapisuje je w tablicy i wyświetla je.</span><span class="sxs-lookup"><span data-stu-id="ac444-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="ac444-106">Przykład odczytuje pozostałe znaki w ciągu, zapisuje je w tablicy, zaczynając od szóstego elementu i wyświetla zawartość tablicy.</span><span class="sxs-lookup"><span data-stu-id="ac444-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="ac444-107">Przykład: odczytywanie znaków asynchronicznie</span><span class="sxs-lookup"><span data-stu-id="ac444-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="ac444-108">Następny przykład to kod związany z aplikacją WPF.</span><span class="sxs-lookup"><span data-stu-id="ac444-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="ac444-109">W przypadku ładowania okna przykład Asynchronicznie odczytuje wszystkie znaki z kontrolki <xref:System.Windows.Controls.TextBox> i zapisuje je w tablicy.</span><span class="sxs-lookup"><span data-stu-id="ac444-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="ac444-110">Następnie asynchronicznie zapisuje każdą literę lub biały znak w osobnym wierszu kontrolki <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="ac444-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ac444-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac444-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="ac444-112">Asynchroniczne operacje we/wy pliku</span><span class="sxs-lookup"><span data-stu-id="ac444-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="ac444-113">[Instrukcje: Tworzenie listy katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac444-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="ac444-114">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="ac444-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="ac444-115">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="ac444-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="ac444-116">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="ac444-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="ac444-117">Instrukcje: wpisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="ac444-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="ac444-118">Instrukcje: Wpisywanie znaków do ciągu</span><span class="sxs-lookup"><span data-stu-id="ac444-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="ac444-119">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="ac444-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
