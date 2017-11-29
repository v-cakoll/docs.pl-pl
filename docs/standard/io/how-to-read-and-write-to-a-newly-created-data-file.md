---
title: "Porady: odczyt i zapis we właśnie utworzonym pliku danych"
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
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b547f2c85495a497e5fc384f9a2ea44de7bf861c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="d5b4a-102">Porady: odczyt i zapis we właśnie utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="d5b4a-102">How to: Read and Write to a Newly Created Data File</span></span>
<span data-ttu-id="d5b4a-103"><xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader?displayProperty=nameWithType> klasy służą do zapisywania i odczytywania danych zamiast ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="d5b4a-103">The <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data rather than character strings.</span></span> <span data-ttu-id="d5b4a-104">W poniższym przykładzie pokazano sposób zapisywania danych do i odczytać danych ze strumienia nowy, pusty plik o nazwie `Test.data`.</span><span class="sxs-lookup"><span data-stu-id="d5b4a-104">The following example demonstrates how to write data to, and read data from, a new, empty file stream called `Test.data`.</span></span> <span data-ttu-id="d5b4a-105">Po utworzeniu pliku danych w bieżącym katalogu skojarzonego <xref:System.IO.BinaryWriter> i <xref:System.IO.BinaryReader> obiekty są tworzone i <xref:System.IO.BinaryWriter> obiektu służy do zapisywania liczb całkowitych od 0 do 10, aby `Test.data`, dlatego wskaźnika pliku na końcu plik.</span><span class="sxs-lookup"><span data-stu-id="d5b4a-105">After creating the data file in the current directory, the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects are created, and the <xref:System.IO.BinaryWriter> object is used to write the integers 0 through 10 to `Test.data`, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="d5b4a-106">Po ustawieniu wskaźnika pliku z powrotem do źródła, <xref:System.IO.BinaryReader> obiektu odczytuje określony zawartość.</span><span class="sxs-lookup"><span data-stu-id="d5b4a-106">After setting the file pointer back to the origin, the <xref:System.IO.BinaryReader> object reads out the specified content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5b4a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5b4a-107">Example</span></span>  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d5b4a-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d5b4a-108">Robust Programming</span></span>  
 <span data-ttu-id="d5b4a-109">Jeśli `Test.data` już istnieje w bieżącym katalogu <xref:System.IO.IOException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d5b4a-109">If `Test.data` already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="d5b4a-110">Użyj opcji Tryb pliku <xref:System.IO.FileMode.Create?displayProperty=nameWithType> kiedy należy zainicjować strumień plików, aby zawsze twórz nowych plików bez generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d5b4a-110">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> when you initialize the file stream to always create a new file without throwing an  exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b4a-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5b4a-111">See Also</span></span>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryWriter>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
 <xref:System.IO.SeekOrigin>  
 [<span data-ttu-id="d5b4a-112">Porady: Wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="d5b4a-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="d5b4a-113">Porady: otwieranie i Dołącz do pliku dziennika</span><span class="sxs-lookup"><span data-stu-id="d5b4a-113">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="d5b4a-114">Porady: Odczyt tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="d5b4a-114">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="d5b4a-115">Porady: zapisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="d5b4a-115">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="d5b4a-116">Porady: odczytywanie znaków z ciągu</span><span class="sxs-lookup"><span data-stu-id="d5b4a-116">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="d5b4a-117">Porady: zapisywanie znaków ciągu</span><span class="sxs-lookup"><span data-stu-id="d5b4a-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="d5b4a-118">Plik i strumienia I-O</span><span class="sxs-lookup"><span data-stu-id="d5b4a-118">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
