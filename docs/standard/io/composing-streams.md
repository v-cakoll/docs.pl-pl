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
ms.openlocfilehash: 5e52b827f337892c33ec61b9affa1cc646a759c5
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841180"
---
# <a name="composing-streams"></a><span data-ttu-id="53ab2-102">Tworzenie strumieni</span><span class="sxs-lookup"><span data-stu-id="53ab2-102">Composing Streams</span></span>
<span data-ttu-id="53ab2-103">Magazyn zapasowy jest na nośniku, na przykład dysk lub pamięć.</span><span class="sxs-lookup"><span data-stu-id="53ab2-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="53ab2-104">Każdy magazyn zapasowy różnych implementuje własne strumienia jako implementacja <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="53ab2-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="53ab2-105">Każdy typ strumienia odczytuje i zapisuje bajty od i do jego podanej zapasowego magazynu.</span><span class="sxs-lookup"><span data-stu-id="53ab2-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="53ab2-106">Strumienie, łączących się z magazynami kopii są nazywane podstawowe strumienie.</span><span class="sxs-lookup"><span data-stu-id="53ab2-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="53ab2-107">Podstawowe strumienie ma konstruktorów, które mają parametry, które są wymagane do nawiązania strumienia magazyn zapasowy.</span><span class="sxs-lookup"><span data-stu-id="53ab2-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="53ab2-108">Na przykład <xref:System.IO.FileStream> ma konstruktorów, które określają parametr ścieżki, która określa, jak plik zostanie udostępniony przez procesy i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="53ab2-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="53ab2-109">Projekt <xref:System.IO> klasy oferuje uproszczone strumienia redagowania.</span><span class="sxs-lookup"><span data-stu-id="53ab2-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="53ab2-110">Podstawowe strumienie można dołączyć do co najmniej jeden strumień przekazujące, które zapewniają funkcjonalność, którą chcesz.</span><span class="sxs-lookup"><span data-stu-id="53ab2-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="53ab2-111">Odczytywania lub zapisywania można dołączyć do końca łańcucha tak, aby typy preferowane może odczytać lub zapisywane w prosty sposób.</span><span class="sxs-lookup"><span data-stu-id="53ab2-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="53ab2-112">Poniższy przykład kodu tworzy **FileStream** wokół istniejącego `MyFile.txt` w kolejności do buforu `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="53ab2-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="53ab2-113">(Należy pamiętać, że **FileStreams** są buforowane domyślnie.) Następnie <xref:System.IO.StreamReader> jest tworzony na odczytywanie znaków z **FileStream**, która jest przekazywana do **StreamReader** jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="53ab2-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="53ab2-114"><xref:System.IO.StreamReader.ReadLine%2A> odczytuje do momentu <xref:System.IO.StreamReader.Peek%2A> znajdzie nie więcej znaków.</span><span class="sxs-lookup"><span data-stu-id="53ab2-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="53ab2-115">Poniższy przykład kodu tworzy **FileStream** wokół istniejącego `MyFile.txt` w kolejności do buforu `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="53ab2-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="53ab2-116">(Należy pamiętać, że **FileStreams** są buforowane domyślnie.) Następnie **BinaryReader** służy do odczytywania bajtów z **FileStream**, która jest przekazywana do **BinaryReader** jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="53ab2-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="53ab2-117"><xref:System.IO.BinaryReader.ReadByte%2A> odczytuje do momentu <xref:System.IO.BinaryReader.PeekChar%2A> znajdzie nie większą liczbę bajtów.</span><span class="sxs-lookup"><span data-stu-id="53ab2-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="53ab2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53ab2-118">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
