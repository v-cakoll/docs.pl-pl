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
ms.openlocfilehash: 3f18712793254f4942c092c87a3e64c73b492ae0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160108"
---
# <a name="compose-streams"></a><span data-ttu-id="df18e-102">Tworzenie strumieni</span><span class="sxs-lookup"><span data-stu-id="df18e-102">Compose streams</span></span>
<span data-ttu-id="df18e-103">*Magazyn zapasowy* jest nośnikiem pamięci masowej, takim jak dysk lub pamięć.</span><span class="sxs-lookup"><span data-stu-id="df18e-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="df18e-104">Każdy inny magazyn zapasowy implementuje swój własny <xref:System.IO.Stream> strumień jako implementację klasy.</span><span class="sxs-lookup"><span data-stu-id="df18e-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="df18e-105">Każdy typ strumienia odczytuje i zapisuje bajty z i do danego magazynu zapasowego.</span><span class="sxs-lookup"><span data-stu-id="df18e-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="df18e-106">Strumienie, które łączą się z magazynami zapasowymi, są nazywane *strumieniami bazowymi*.</span><span class="sxs-lookup"><span data-stu-id="df18e-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="df18e-107">Strumienie bazowe mają konstruktorów z parametrami niezbędnymi do połączenia strumienia do magazynu kopii zapasowych.</span><span class="sxs-lookup"><span data-stu-id="df18e-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="df18e-108">Na przykład <xref:System.IO.FileStream> ma konstruktorów, które określają parametr ścieżki, który określa, jak plik będzie współużytkowany przez procesy.</span><span class="sxs-lookup"><span data-stu-id="df18e-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="df18e-109">Projekt klas <xref:System.IO> zapewnia uproszczony skład strumienia.</span><span class="sxs-lookup"><span data-stu-id="df18e-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="df18e-110">Strumienie podstawowe można dołączyć do jednego lub większej liczby strumieni przekazu, które zapewniają żądaną funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="df18e-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="df18e-111">Czytnik lub moduł zapisujący można dołączyć do końca łańcucha, dzięki czemu preferowane typy można łatwo odczytać lub zapisać.</span><span class="sxs-lookup"><span data-stu-id="df18e-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="df18e-112">Poniższe przykłady kodu tworzą **FileStream** wokół istniejącego *pliku MyFile.txt* w celu buforowania *pliku MyFile.txt*.</span><span class="sxs-lookup"><span data-stu-id="df18e-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="df18e-113">Należy zauważyć, że **FileStreams** są buforowane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="df18e-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="df18e-114">W przykładach przyjęto założenie, że plik o nazwie *MyFile.txt* już istnieje w tym samym folderze co aplikacja.</span><span class="sxs-lookup"><span data-stu-id="df18e-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="df18e-115">Przykład: Korzystanie z streamreadera</span><span class="sxs-lookup"><span data-stu-id="df18e-115">Example: Use StreamReader</span></span>
<span data-ttu-id="df18e-116">Poniższy przykład tworzy <xref:System.IO.StreamReader> do odczytu znaków z **FileStream**, który jest przekazywany do **StreamReader** jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="df18e-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="df18e-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>następnie odczytuje, dopóki <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nie znajdzie więcej znaków.</span><span class="sxs-lookup"><span data-stu-id="df18e-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="df18e-118">Przykład: Użyj czytnika binarnego</span><span class="sxs-lookup"><span data-stu-id="df18e-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="df18e-119">Poniższy przykład tworzy <xref:System.IO.BinaryReader> do odczytu bajtów z **FileStream**, który jest przekazywany do **BinaryReader** jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="df18e-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="df18e-120"><xref:System.IO.BinaryReader.ReadByte%2A>następnie odczytuje, dopóki <xref:System.IO.BinaryReader.PeekChar%2A> nie znajdzie więcej bajtów.</span><span class="sxs-lookup"><span data-stu-id="df18e-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="df18e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df18e-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
