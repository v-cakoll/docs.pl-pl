---
title: 'Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 065907ae0d4a38ff2ef68de6025251e28220ee96
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674623"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="d5b7d-102">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="d5b7d-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="d5b7d-103"><xref:System.IO.BinaryWriter?displayProperty=nameWithType> i <xref:System.IO.BinaryReader?displayProperty=nameWithType> klasy są używane do zapisywania i odczytywania danych innych niż ciągi znaków.</span><span class="sxs-lookup"><span data-stu-id="d5b7d-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="d5b7d-104">Poniższy przykład pokazuje, jak utworzyć pusty plik strumienia w nim zapisywać dane i odczytywać dane.</span><span class="sxs-lookup"><span data-stu-id="d5b7d-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span> 

<span data-ttu-id="d5b7d-105">Przykład tworzy plik danych o nazwie *Test.data* w bieżącym katalogu, tworzy skojarzonego <xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader> obiektów i używa <xref:System.IO.BinaryWriter> obiektu do zapisania liczbami całkowitymi od 0 do 10 na *Test.data*, dlatego wskaźnikiem pliku, na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="d5b7d-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="d5b7d-106"><xref:System.IO.BinaryReader> Obiektu następnie ustawia wskaźnik pliku źródła i odczytuje się określonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="d5b7d-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5b7d-107">Jeśli *Test.data* już istnieje w bieżącym katalogu <xref:System.IO.IOException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d5b7d-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="d5b7d-108">Użyj opcji Tryb pliku <xref:System.IO.FileMode.Create?displayProperty=nameWithType> zamiast <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> zawsze utworzyć nowy plik bez zgłoszenia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d5b7d-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5b7d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5b7d-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d5b7d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5b7d-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="d5b7d-111">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="d5b7d-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="d5b7d-112">Instrukcje: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="d5b7d-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="d5b7d-113">Instrukcje: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="d5b7d-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="d5b7d-114">Instrukcje: Zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="d5b7d-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="d5b7d-115">Instrukcje: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="d5b7d-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="d5b7d-116">Instrukcje: Zapisywanie znaków w ciągu</span><span class="sxs-lookup"><span data-stu-id="d5b7d-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="d5b7d-117">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="d5b7d-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
