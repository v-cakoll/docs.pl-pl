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
ms.openlocfilehash: 689cc9537cd7a5fe6a677d42e5790bbcf1b3aefa
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708151"
---
# <a name="compose-streams"></a><span data-ttu-id="60549-102">Tworzenie strumieni</span><span class="sxs-lookup"><span data-stu-id="60549-102">Compose streams</span></span>
<span data-ttu-id="60549-103">*Magazyn zapasowy* jest nośnikiem magazynującym, takim jak dysk lub pamięć.</span><span class="sxs-lookup"><span data-stu-id="60549-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="60549-104">Każdy inny magazyn zapasowy implementuje swój własny strumień jako implementację klasy <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="60549-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> 

<span data-ttu-id="60549-105">Każdy typ strumienia odczytuje i zapisuje bajty z i do danego magazynu zapasowego.</span><span class="sxs-lookup"><span data-stu-id="60549-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="60549-106">Strumienie łączące się z magazynami zapasowymi są nazywane *strumieniami podstawowymi*.</span><span class="sxs-lookup"><span data-stu-id="60549-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="60549-107">Strumienie podstawowe mają konstruktory z parametrami niezbędnymi do połączenia strumienia z magazynem zapasowym.</span><span class="sxs-lookup"><span data-stu-id="60549-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="60549-108">Na przykład <xref:System.IO.FileStream> ma konstruktory, które określają parametr path, który określa sposób, w jaki plik będzie współużytkowany przez procesy.</span><span class="sxs-lookup"><span data-stu-id="60549-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="60549-109">Projekt klas <xref:System.IO> zapewnia uproszczoną transkompozycję strumienia.</span><span class="sxs-lookup"><span data-stu-id="60549-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="60549-110">Można dołączyć strumienie podstawowe do co najmniej jednego strumienia przekazującego, który zapewnia odpowiednie funkcje.</span><span class="sxs-lookup"><span data-stu-id="60549-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="60549-111">Do końca łańcucha można dołączyć czytelnika lub moduł zapisujący, dzięki czemu preferowane typy mogą być łatwo odczytywane lub zapisywane.</span><span class="sxs-lookup"><span data-stu-id="60549-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="60549-112">Poniższy przykład kodu tworzy obiekt **FILESTREAM** wokół istniejącego *pliku. txt* w celu buforowania *pliku. txt*.</span><span class="sxs-lookup"><span data-stu-id="60549-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="60549-113">Należy pamiętać, że **FILESTREAM** domyślnie są buforowane.</span><span class="sxs-lookup"><span data-stu-id="60549-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="60549-114">W przykładach założono, że plik o nazwie mój *plik. txt* już istnieje w tym samym folderze, w którym znajduje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="60549-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="60549-115">Przykład: Użyj StreamReader</span><span class="sxs-lookup"><span data-stu-id="60549-115">Example: Use StreamReader</span></span>
<span data-ttu-id="60549-116">Poniższy przykład tworzy <xref:System.IO.StreamReader> do odczytywania znaków z **FILESTREAM**, który jest przesyłany do **StreamReader** jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="60549-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="60549-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> następnie odczytuje do momentu, gdy <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nie znajdzie więcej znaków.</span><span class="sxs-lookup"><span data-stu-id="60549-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="60549-118">Przykład: Użyj BinaryReader</span><span class="sxs-lookup"><span data-stu-id="60549-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="60549-119">Poniższy przykład tworzy <xref:System.IO.BinaryReader> do odczytywania bajtów z **FILESTREAM**, który jest przesyłany do **BinaryReader** jako argument konstruktora.</span><span class="sxs-lookup"><span data-stu-id="60549-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="60549-120"><xref:System.IO.BinaryReader.ReadByte%2A> następnie odczytuje do momentu, gdy <xref:System.IO.BinaryReader.PeekChar%2A> nie znajdzie więcej bajtów.</span><span class="sxs-lookup"><span data-stu-id="60549-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="60549-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60549-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
