---
title: 'Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych'
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
ms.openlocfilehash: 3772aeeb25d1251a13fde2a0e51a913e5e39eabc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155753"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="21a4c-102">Jak: Odczytywanie i zapisywanie w nowo utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="21a4c-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="21a4c-103">I <xref:System.IO.BinaryWriter?displayProperty=nameWithType> <xref:System.IO.BinaryReader?displayProperty=nameWithType> klasy są używane do zapisywania i odczytywania danych innych niż ciągi znaków.</span><span class="sxs-lookup"><span data-stu-id="21a4c-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="21a4c-104">W poniższym przykładzie pokazano, jak utworzyć pusty strumień plików, zapisać do niego dane i odczytać z niego dane.</span><span class="sxs-lookup"><span data-stu-id="21a4c-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="21a4c-105">Przykład tworzy plik danych o nazwie *Test.data* w <xref:System.IO.BinaryWriter> bieżącym <xref:System.IO.BinaryReader> katalogu, tworzy <xref:System.IO.BinaryWriter> skojarzone i obiekty i używa obiektu do zapisu liczb całkowitych od 0 do 10 do *Test.data*, który pozostawia wskaźnik pliku na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="21a4c-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="21a4c-106">Następnie <xref:System.IO.BinaryReader> obiekt ustawia wskaźnik pliku z powrotem do początku i odczytuje określoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="21a4c-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21a4c-107">Jeśli *Test.data* już istnieje w <xref:System.IO.IOException> bieżącym katalogu, wyjątek.</span><span class="sxs-lookup"><span data-stu-id="21a4c-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="21a4c-108">Użyj opcji <xref:System.IO.FileMode.Create?displayProperty=nameWithType> trybu pliku, <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> a nie zawsze utworzyć nowy plik bez zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="21a4c-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21a4c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="21a4c-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="21a4c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21a4c-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="21a4c-111">Jak: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="21a4c-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="21a4c-112">Jak: Otwieranie i dołączanie do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="21a4c-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="21a4c-113">Jak: Odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="21a4c-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="21a4c-114">Jak: Napisać tekst do pliku</span><span class="sxs-lookup"><span data-stu-id="21a4c-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="21a4c-115">Jak: Odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="21a4c-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="21a4c-116">Jak: Zapisywać znaki do ciągu</span><span class="sxs-lookup"><span data-stu-id="21a4c-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="21a4c-117">Plik i strumień we/wy</span><span class="sxs-lookup"><span data-stu-id="21a4c-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
