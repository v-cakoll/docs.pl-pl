---
title: 'Porady: usuwanie plików i katalogów w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: ec4de3e3a139cfcf66f1f6252c03c467f4ccfbc5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707860"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="6c295-102">Porady: usuwanie plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="6c295-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="6c295-103">Można usunąć katalogi i pliki w izolowanym pliku magazynu.</span><span class="sxs-lookup"><span data-stu-id="6c295-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="6c295-104">W magazynie nazwy plików i katalogów są zależne od systemu operacyjnego i są określane jako względne dla katalogu głównego wirtualnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="6c295-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="6c295-105">W systemach operacyjnych Windows nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="6c295-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="6c295-106">Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> udostępnia dwie metody usuwania katalogów i plików: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c295-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="6c295-107">Wyjątek <xref:System.IO.IsolatedStorage.IsolatedStorageException> jest generowany w przypadku próby usunięcia pliku lub katalogu, który nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="6c295-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="6c295-108">Jeśli w nazwie zostanie uwzględniony symbol wieloznaczny, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> zgłasza wyjątek <xref:System.IO.IsolatedStorage.IsolatedStorageException>, a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> zgłasza wyjątek <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="6c295-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="6c295-109">Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> kończy się niepowodzeniem, jeśli katalog zawiera jakiekolwiek pliki lub podkatalogi.</span><span class="sxs-lookup"><span data-stu-id="6c295-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="6c295-110">Możesz użyć metod <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> do pobierania istniejących plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="6c295-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="6c295-111">Aby uzyskać więcej informacji o przeszukiwaniu wirtualnego systemu plików w sklepie, zobacz [How to: find Existing Files i directorys in the izolowany magazyn](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="6c295-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c295-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c295-112">Example</span></span>  
 <span data-ttu-id="6c295-113">Poniższy przykład kodu tworzy, a następnie usuwa kilka katalogów i plików.</span><span class="sxs-lookup"><span data-stu-id="6c295-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6c295-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c295-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="6c295-115">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="6c295-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
