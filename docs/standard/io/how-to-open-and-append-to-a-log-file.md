---
title: 'Porady: otwieranie pliku dziennika i dołączanie do niego'
ms.date: 03/30/2017
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
ms.openlocfilehash: cd2d13a49d9b696541ac278b9f1847c8e4a48cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="88770-102">Porady: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="88770-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="88770-103"><xref:System.IO.StreamWriter> i <xref:System.IO.StreamReader> znaków do zapisu i odczytywanie znaków ze strumieni.</span><span class="sxs-lookup"><span data-stu-id="88770-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="88770-104">Poniższy kod przykładowy otwiera `log.txt` plików dla danych wejściowych lub tworzy plik, jeśli jeszcze nie istnieje i dołącza informacje na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="88770-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="88770-105">Zawartość pliku następnie są zapisywane do wyjścia standardowego do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="88770-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="88770-106">Zamiast tego przykładu, informacje można przechowywane jako pojedynczy ciąg lub tablicę ciągów i <xref:System.IO.File.WriteAllText%2A> lub <xref:System.IO.File.WriteAllLines%2A> — metoda może być stosowana te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="88770-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88770-107">Visual Basic użytkownicy mogą wybierać metody i właściwości udostępniane przez <xref:Microsoft.VisualBasic.Logging.Log> klasy lub <xref:Microsoft.VisualBasic.FileIO.FileSystem> klasy związane z tworzeniem lub zapisywanie w plikach dziennika.</span><span class="sxs-lookup"><span data-stu-id="88770-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88770-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="88770-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="88770-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88770-109">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="88770-110">Instrukcje: wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="88770-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="88770-111">Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="88770-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="88770-112">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="88770-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="88770-113">Instrukcje: zapisywanie tekstu w pliku</span><span class="sxs-lookup"><span data-stu-id="88770-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="88770-114">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="88770-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="88770-115">Instrukcje: zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="88770-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="88770-116">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="88770-116">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
