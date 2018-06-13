---
title: Tworzenie strumieni
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 231bd98b556dafeb69091de4a6770c1462824659
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572856"
---
# <a name="composing-streams"></a><span data-ttu-id="f15a9-102">Tworzenie strumieni</span><span class="sxs-lookup"><span data-stu-id="f15a9-102">Composing Streams</span></span>
<span data-ttu-id="f15a9-103">Magazynu zapasowego jest nośniku, takie jak dysk lub pamięci.</span><span class="sxs-lookup"><span data-stu-id="f15a9-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="f15a9-104">Każdy magazyn zapasowy różnych implementuje własną strumienia jako implementacja <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="f15a9-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="f15a9-105">Każdy typ strumienia odczytuje i zapisuje bajty od i do jego magazynu zapasowego danego.</span><span class="sxs-lookup"><span data-stu-id="f15a9-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="f15a9-106">Strumienie łączący się tworzenie kopii magazynów są nazywane podstawowe strumienie.</span><span class="sxs-lookup"><span data-stu-id="f15a9-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="f15a9-107">Podstawowe strumienie mieć konstruktorów, które mają parametry niezbędne do nawiązania połączenia magazynu zapasowego strumienia.</span><span class="sxs-lookup"><span data-stu-id="f15a9-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="f15a9-108">Na przykład <xref:System.IO.FileStream> ma konstruktorów określić parametr path, która określa, jak plik zostanie udostępniony przez procesy i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f15a9-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="f15a9-109">Projekt <xref:System.IO> klasy zawiera redagowania uproszczony strumienia.</span><span class="sxs-lookup"><span data-stu-id="f15a9-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="f15a9-110">Podstawowe strumienie może zostać dołączona do co najmniej jeden strumieni przekazujące, które udostępniają funkcje, które mają.</span><span class="sxs-lookup"><span data-stu-id="f15a9-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="f15a9-111">Odczytywania lub zapisywania może zostać dołączona na końcu łańcucha, tak aby typy preferowane można odczytu lub zapisu w prosty sposób.</span><span class="sxs-lookup"><span data-stu-id="f15a9-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="f15a9-112">Poniższy przykład kodu tworzy **FileStream** wokół istniejące `MyFile.txt` w kolejności do buforu `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="f15a9-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="f15a9-113">(Należy pamiętać, że **FileStreams** są buforowane domyślnie.) Następnie <xref:System.IO.StreamReader> utworzeniu znaków z **FileStream**, przekazywany do **StreamReader** jako jej argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f15a9-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="f15a9-114"><xref:System.IO.StreamReader.ReadLine%2A> odczytuje do <xref:System.IO.StreamReader.Peek%2A> znajdzie nie więcej znaków.</span><span class="sxs-lookup"><span data-stu-id="f15a9-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="f15a9-115">Poniższy przykład kodu tworzy **FileStream** wokół istniejące `MyFile.txt` w kolejności do buforu `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="f15a9-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="f15a9-116">(Należy pamiętać, że **FileStreams** są buforowane domyślnie.) Dalej **BinaryReader** służy do odczytywania bajtów z **FileStream**, która jest przekazywana do **BinaryReader** jako jej argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f15a9-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="f15a9-117"><xref:System.IO.BinaryReader.ReadByte%2A> odczytuje do <xref:System.IO.BinaryReader.PeekChar%2A> znajdzie nie większej liczby bajtów.</span><span class="sxs-lookup"><span data-stu-id="f15a9-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="f15a9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f15a9-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
