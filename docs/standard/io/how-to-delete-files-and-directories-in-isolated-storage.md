---
title: 'Instrukcje: Usuwanie plików i katalogów w wydzielonej pamięci masowej'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05b7fa3010ab089d1a97e9a0516096326fd4bb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538027"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="25d57-102">Instrukcje: Usuwanie plików i katalogów w wydzielonej pamięci masowej</span><span class="sxs-lookup"><span data-stu-id="25d57-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="25d57-103">Można usunąć katalogów i plików w pliku wydzielonej pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="25d57-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="25d57-104">W magazynie i nazw plików i katalogów jest zależna od systemu operacyjnego i są określane względem katalogu głównego w wirtualnym systemie plików.</span><span class="sxs-lookup"><span data-stu-id="25d57-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="25d57-105">Nie są one wielkość liter w systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="25d57-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="25d57-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Klasa zapewnia dwie metody usuwania plików i katalogów: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="25d57-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="25d57-107"><xref:System.IO.IsolatedStorage.IsolatedStorageException> Wyjątek jest generowany, jeśli zostanie podjęta próba usunięcia pliku lub katalogu, który nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="25d57-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="25d57-108">Jeśli dołączysz symbolu wieloznacznego w nazwie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> zgłasza <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątek, i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> zgłasza <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="25d57-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="25d57-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Metoda kończy się niepowodzeniem, jeśli katalog zawiera wszystkie pliki i podkatalogi.</span><span class="sxs-lookup"><span data-stu-id="25d57-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="25d57-110">Możesz użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody pobierania istniejących plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="25d57-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="25d57-111">Aby uzyskać więcej informacji na temat wyszukiwania w wirtualnym systemie plików magazynu, zobacz [jak: Wyszukiwanie istniejących plików i katalogów w wydzielonej pamięci masowej](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="25d57-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25d57-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="25d57-112">Example</span></span>  
 <span data-ttu-id="25d57-113">Poniższy przykład kodu tworzy i usuwa kilka plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="25d57-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="25d57-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25d57-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="25d57-115">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="25d57-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
