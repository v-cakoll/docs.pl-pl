---
title: "Porady: usuwanie plików i katalogów w izolowanym magazynie"
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="c6636-102">Porady: usuwanie plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="c6636-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="c6636-103">Można usunąć katalogów i plików znajdujących się w pliku izolowanego magazynu.</span><span class="sxs-lookup"><span data-stu-id="c6636-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="c6636-104">W sklepie nazw plików i katalogów są zależne od systemu operacyjnego i są określone jako względem katalogu głównego wirtualnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="c6636-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="c6636-105">Nie są one z uwzględnieniem wielkości liter w systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="c6636-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="c6636-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Klasa zapewnia dwie metody usuwania plików i katalogów: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="c6636-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="c6636-107"><xref:System.IO.IsolatedStorage.IsolatedStorageException> Wyjątek przy próbie usunięcia pliku lub katalogu, który nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c6636-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="c6636-108">Jeśli dołączysz symbolu wieloznacznego w nazwie, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> zgłasza <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> zgłasza <xref:System.ArgumentException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c6636-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="c6636-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Metody zakończy się niepowodzeniem, jeśli katalog zawiera wszystkie pliki i podkatalogi.</span><span class="sxs-lookup"><span data-stu-id="c6636-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="c6636-110">Można użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody do pobierania istniejących plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="c6636-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="c6636-111">Aby uzyskać więcej informacji na temat wyszukiwanie w wirtualnym systemie plików magazynu, zobacz [porady: znajdowanie istniejących plików i katalogów w izolowanym magazynie](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="c6636-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6636-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6636-112">Example</span></span>  
 <span data-ttu-id="c6636-113">Poniższy przykład kodu tworzy, a następnie usuwa kilka plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="c6636-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c6636-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6636-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [<span data-ttu-id="c6636-115">Izolowany Magazyn</span><span class="sxs-lookup"><span data-stu-id="c6636-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
