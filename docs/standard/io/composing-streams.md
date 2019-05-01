---
title: Tworzenie strumieni
ms.date: 01/21/2019
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
ms.openlocfilehash: 452071e9726a95b4b3d9bb9cefe720d39bbc3e0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950374"
---
# <a name="compose-streams"></a><span data-ttu-id="13e23-102">Tworzenie strumieni</span><span class="sxs-lookup"><span data-stu-id="13e23-102">Compose streams</span></span>
<span data-ttu-id="13e23-103">A *magazyn zapasowy* się na nośniku, na przykład dysk lub pamięć.</span><span class="sxs-lookup"><span data-stu-id="13e23-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="13e23-104">Każdy magazyn zapasowy różnych implementuje własne strumienia jako implementacja <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="13e23-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> 

<span data-ttu-id="13e23-105">Każdy typ strumienia odczytuje i zapisuje bajty od i do jego podanej zapasowego magazynu.</span><span class="sxs-lookup"><span data-stu-id="13e23-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="13e23-106">Strumienie, łączących się z magazynami kopii są nazywane *podstawowa strumieni*.</span><span class="sxs-lookup"><span data-stu-id="13e23-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="13e23-107">Podstawowe strumienie mieć konstruktorów z parametrami, które są wymagane do nawiązania strumienia magazyn zapasowy.</span><span class="sxs-lookup"><span data-stu-id="13e23-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="13e23-108">Na przykład <xref:System.IO.FileStream> ma konstruktorów, które określają parametr ścieżki, która określa, jak plik zostanie udostępniony przez procesy.</span><span class="sxs-lookup"><span data-stu-id="13e23-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="13e23-109">Projekt <xref:System.IO> klasy oferuje uproszczone strumienia kompozycji.</span><span class="sxs-lookup"><span data-stu-id="13e23-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="13e23-110">Podstawowe strumienie można dołączyć do co najmniej jeden strumień przekazujące, które zapewniają funkcjonalność, którą chcesz.</span><span class="sxs-lookup"><span data-stu-id="13e23-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="13e23-111">Odczytywania lub zapisywania może dołączać do końca łańcucha, co typy preferowane może odczytać lub zapisywane w prosty sposób.</span><span class="sxs-lookup"><span data-stu-id="13e23-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="13e23-112">Utwórz następujące przykłady kodu **FileStream** wokół istniejącego *mójplik.txt* w kolejności do buforu *mójplik.txt*.</span><span class="sxs-lookup"><span data-stu-id="13e23-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="13e23-113">Należy pamiętać, że **FileStreams** są buforowane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="13e23-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="13e23-114">W przykładach założono, że plik o nazwie *mójplik.txt* już istnieje w tym samym folderze co aplikacja.</span><span class="sxs-lookup"><span data-stu-id="13e23-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="13e23-115">Przykład: Użyj StreamReader</span><span class="sxs-lookup"><span data-stu-id="13e23-115">Example: Use StreamReader</span></span>
<span data-ttu-id="13e23-116">Poniższy przykład tworzy <xref:System.IO.StreamReader> na odczytywanie znaków z **FileStream**, która jest przekazywana do **StreamReader** jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="13e23-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="13e23-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> następnie odczytuje aż <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> znajdzie nie więcej znaków.</span><span class="sxs-lookup"><span data-stu-id="13e23-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="13e23-118">Przykład: Użyj BinaryReader</span><span class="sxs-lookup"><span data-stu-id="13e23-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="13e23-119">Poniższy przykład tworzy <xref:System.IO.BinaryReader> do odczytywania bajtów z **FileStream**, która jest przekazywana do **BinaryReader** jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="13e23-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="13e23-120"><xref:System.IO.BinaryReader.ReadByte%2A> następnie odczytuje aż <xref:System.IO.BinaryReader.PeekChar%2A> znajdzie nie większą liczbę bajtów.</span><span class="sxs-lookup"><span data-stu-id="13e23-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="13e23-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13e23-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
