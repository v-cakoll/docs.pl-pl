---
title: 'Instrukcje: Odczyt i zapis w plikach w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
ms.openlocfilehash: d0c95f418ff85654dceed296b7a891c025ab2e62
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291802"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="272e5-102">Instrukcje: Odczyt i zapis w plikach w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="272e5-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="272e5-103">Aby odczytywać lub zapisywać dane w pliku w izolowanym magazynie, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> obiektu z czytnikiem strumienia ( <xref:System.IO.StreamReader> obiektem) lub składnikiem zapisywania strumienia ( <xref:System.IO.StreamWriter> Object).</span><span class="sxs-lookup"><span data-stu-id="272e5-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="272e5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="272e5-104">Example</span></span>  
 <span data-ttu-id="272e5-105">Poniższy przykład kodu uzyskuje izolowany magazyn i sprawdza, czy plik o nazwie TestStore. txt istnieje w sklepie.</span><span class="sxs-lookup"><span data-stu-id="272e5-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="272e5-106">Jeśli nie istnieje, tworzy plik i zapisuje "Hello izolowany magazyn" do pliku.</span><span class="sxs-lookup"><span data-stu-id="272e5-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="272e5-107">Jeśli TestStore. txt już istnieje, przykładowy kod odczytuje z pliku.</span><span class="sxs-lookup"><span data-stu-id="272e5-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="272e5-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="272e5-108">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [<span data-ttu-id="272e5-109">We/wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="272e5-109">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="272e5-110">Magazyn izolowany</span><span class="sxs-lookup"><span data-stu-id="272e5-110">Isolated Storage</span></span>](isolated-storage.md)
