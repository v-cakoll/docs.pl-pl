---
title: "Porady: otwieranie pliku dziennika i dołączanie do niego"
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
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="85291-102">Porady: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="85291-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="85291-103"><xref:System.IO.StreamWriter>i <xref:System.IO.StreamReader> znaków do zapisu i odczytywanie znaków ze strumieni.</span><span class="sxs-lookup"><span data-stu-id="85291-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="85291-104">Poniższy kod przykładowy otwiera `log.txt` plików dla danych wejściowych lub tworzy plik, jeśli jeszcze nie istnieje i dołącza informacje na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="85291-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="85291-105">Zawartość pliku następnie są zapisywane do wyjścia standardowego do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="85291-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="85291-106">Zamiast tego przykładu, informacje można przechowywane jako pojedynczy ciąg lub tablicę ciągów i <xref:System.IO.File.WriteAllText%2A> lub <xref:System.IO.File.WriteAllLines%2A> — metoda może być stosowana te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="85291-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85291-107">Visual Basic użytkownicy mogą wybierać metody i właściwości udostępniane przez <xref:Microsoft.VisualBasic.Logging.Log> klasy lub <xref:Microsoft.VisualBasic.FileIO.FileSystem> klasy związane z tworzeniem lub zapisywanie w plikach dziennika.</span><span class="sxs-lookup"><span data-stu-id="85291-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85291-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="85291-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="85291-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85291-109">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="85291-110">Porady: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="85291-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="85291-111">Porady: Odczyt i zapis do pliku danych nowo utworzony</span><span class="sxs-lookup"><span data-stu-id="85291-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="85291-112">Porady: Odczyt tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="85291-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="85291-113">Porady: zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="85291-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="85291-114">Porady: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="85291-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="85291-115">Porady: zapisywanie znaków ciągu</span><span class="sxs-lookup"><span data-stu-id="85291-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="85291-116">Plik i strumienia I-O</span><span class="sxs-lookup"><span data-stu-id="85291-116">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
