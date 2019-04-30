---
title: 'Instrukcje: Otwieranie i dołączanie do pliku dziennika'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 921b13e057929d7d6b283b26014a4c1f195f39c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751725"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="cef66-102">Instrukcje: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="cef66-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="cef66-103"><xref:System.IO.StreamWriter> i <xref:System.IO.StreamReader> zapisu znaków do i odczytywanie znaków ze strumieni.</span><span class="sxs-lookup"><span data-stu-id="cef66-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="cef66-104">Poniższy kod przykładowy otwiera *log.txt* plików dla danych wejściowych lub go utworzy, jeśli nie istnieje i dołącza informacje dziennika na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="cef66-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="cef66-105">Przykład następnie zapisuje zawartość pliku do wyjścia standardowego do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="cef66-105">The example then writes the contents of the file to standard output for display.</span></span> 

<span data-ttu-id="cef66-106">Jako alternatywę do tego przykładu, można przechowywać informacje jako pojedynczy ciąg lub tablicę ciągów i użyj <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> lub <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> metodę, aby osiągnąć te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="cef66-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cef66-107">Użytkownicy języka Visual Basic mogą zdecydować się na metody i właściwości dostarczonych przez <xref:Microsoft.VisualBasic.Logging.Log> klasy lub <xref:Microsoft.VisualBasic.FileIO.FileSystem> klasa do tworzenia lub zapisywanie w plikach dziennika.</span><span class="sxs-lookup"><span data-stu-id="cef66-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cef66-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="cef66-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cef66-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cef66-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="cef66-110">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="cef66-110">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="cef66-111">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="cef66-111">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="cef66-112">Instrukcje: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="cef66-112">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="cef66-113">Instrukcje: Zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="cef66-113">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="cef66-114">Instrukcje: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="cef66-114">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="cef66-115">Instrukcje: Zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="cef66-115">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="cef66-116">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="cef66-116">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
