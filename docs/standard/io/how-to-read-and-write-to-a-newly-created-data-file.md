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
ms.openlocfilehash: 0bb06f42542d6acb3214fd4a1a3ca5c54f7caab2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706702"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="142a6-102">Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="142a6-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="142a6-103">Klasy <xref:System.IO.BinaryWriter?displayProperty=nameWithType> i <xref:System.IO.BinaryReader?displayProperty=nameWithType> są używane do zapisywania i odczytywania danych innych niż ciągi znaków.</span><span class="sxs-lookup"><span data-stu-id="142a6-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="142a6-104">Poniższy przykład pokazuje, jak utworzyć pusty strumień plików, zapisać w nim dane i odczytać z niego dane.</span><span class="sxs-lookup"><span data-stu-id="142a6-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span> 

<span data-ttu-id="142a6-105">Przykład tworzy plik danych o nazwie *test. Data* w bieżącym katalogu, tworzy skojarzone <xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader> obiektów, a następnie używa obiektu <xref:System.IO.BinaryWriter>, aby napisać liczbę całkowitą od 0 do 10 w celu *przetestowania. dane*, co pozostawia wskaźnik pliku na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="142a6-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="142a6-106">Obiekt <xref:System.IO.BinaryReader> następnie ustawia wskaźnik pliku z powrotem do źródła i odczytuje określoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="142a6-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="142a6-107">Jeśli *test. Data* już istnieje w bieżącym katalogu, zostanie zgłoszony wyjątek <xref:System.IO.IOException>.</span><span class="sxs-lookup"><span data-stu-id="142a6-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="142a6-108">Użyj opcji Tryb plików <xref:System.IO.FileMode.Create?displayProperty=nameWithType>, a nie <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType>, aby zawsze tworzyć nowy plik bez zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="142a6-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="142a6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="142a6-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="142a6-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="142a6-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="142a6-111">Instrukcje: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="142a6-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="142a6-112">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="142a6-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="142a6-113">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="142a6-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="142a6-114">Instrukcje: wpisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="142a6-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="142a6-115">Instrukcje: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="142a6-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="142a6-116">Instrukcje: Wpisywanie znaków do ciągu</span><span class="sxs-lookup"><span data-stu-id="142a6-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="142a6-117">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="142a6-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
