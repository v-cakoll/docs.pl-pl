---
title: 'Instrukcje: Odczyt i zapis w plikach w wydzielonej pamięci masowej'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59a89aa354941b7ff22a125a980c2d9c75ac37ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491526"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="ae699-102">Instrukcje: Odczyt i zapis w plikach w wydzielonej pamięci masowej</span><span class="sxs-lookup"><span data-stu-id="ae699-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="ae699-103">Odczyt i zapis do pliku w izolowanym magazynie, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> obiektu z czytnik strumienia (<xref:System.IO.StreamReader> obiekt) lub zapisywania do strumienia (<xref:System.IO.StreamWriter> obiektu).</span><span class="sxs-lookup"><span data-stu-id="ae699-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae699-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae699-104">Example</span></span>  
 <span data-ttu-id="ae699-105">Poniższy przykładowy kod uzyskuje izolowanym magazynie i sprawdza, czy plik o nazwie TestStore.txt istnieje w magazynie.</span><span class="sxs-lookup"><span data-stu-id="ae699-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="ae699-106">Jeśli nie istnieje, tworzy plik i zapisuje "Hello wydzielonej pamięci masowej" do pliku.</span><span class="sxs-lookup"><span data-stu-id="ae699-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="ae699-107">Jeśli istnieje już TestStore.txt, przykładowy kod odczytuje z pliku.</span><span class="sxs-lookup"><span data-stu-id="ae699-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ae699-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae699-108">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [<span data-ttu-id="ae699-109">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="ae699-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="ae699-110">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="ae699-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
