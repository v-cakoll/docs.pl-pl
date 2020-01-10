---
title: 'Instrukcje: otwieranie pliku dziennika i dołączanie do niego'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: b0e399ba3c0cfa0ad3b92afbc7e07af7659e8ae6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706715"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="fced7-102">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="fced7-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="fced7-103"><xref:System.IO.StreamWriter> i <xref:System.IO.StreamReader> pisać znaki do i odczytywanie znaków ze strumieni.</span><span class="sxs-lookup"><span data-stu-id="fced7-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="fced7-104">Poniższy przykład kodu otwiera plik *log. txt* dla danych wejściowych lub tworzy go, jeśli nie istnieje, i dołącza informacje dziennika na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="fced7-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="fced7-105">Przykład zapisuje zawartość pliku do standardowego wyjścia na potrzeby wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="fced7-105">The example then writes the contents of the file to standard output for display.</span></span> 

<span data-ttu-id="fced7-106">Alternatywą dla tego przykładu jest zapisanie informacji jako jednego ciągu lub tablicy ciągów i użycie metody <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> lub <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> do osiągnięcia tych samych funkcji.</span><span class="sxs-lookup"><span data-stu-id="fced7-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fced7-107">Visual Basic użytkownicy mogą zdecydować się na użycie metod i właściwości dostarczonych przez klasę <xref:Microsoft.VisualBasic.Logging.Log> lub klasę <xref:Microsoft.VisualBasic.FileIO.FileSystem> do tworzenia lub zapisywania w plikach dziennika.</span><span class="sxs-lookup"><span data-stu-id="fced7-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fced7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="fced7-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fced7-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fced7-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="fced7-110">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="fced7-110">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="fced7-111">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="fced7-111">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="fced7-112">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="fced7-112">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="fced7-113">Instrukcje: wpisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="fced7-113">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="fced7-114">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="fced7-114">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="fced7-115">Instrukcje: Wpisywanie znaków do ciągu</span><span class="sxs-lookup"><span data-stu-id="fced7-115">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="fced7-116">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="fced7-116">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
