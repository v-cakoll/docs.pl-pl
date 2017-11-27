---
title: "Porady: tworzenie plików i katalogów w izolowanym magazynie"
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
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="8843f-102">Porady: tworzenie plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="8843f-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="8843f-103">Po uzyskaniu izolowanego magazynu można utworzyć katalogów i plików do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="8843f-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="8843f-104">W sklepie nazwy plików i katalogów są określane względem katalogu głównego wirtualnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="8843f-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="8843f-105">Aby utworzyć katalog, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8843f-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="8843f-106">Jeśli określisz podkatalogiem katalogu, który nie istnieje, obie katalogi są tworzone.</span><span class="sxs-lookup"><span data-stu-id="8843f-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="8843f-107">Jeśli określisz katalogu, który już istnieje, metoda zwraca bez tworzenia katalogu, a nie wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8843f-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="8843f-108">Jednak jeśli określono nazwę katalogu zawiera nieprawidłowe znaki <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8843f-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="8843f-109">Aby utworzyć plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="8843f-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="8843f-110">W systemie operacyjnym Windows, izolowanego magazynu plików i katalogów nazwy jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="8843f-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="8843f-111">Oznacza to czy utworzony plik o nazwie `ThisFile.txt`, a następnie utwórz plik o nazwie `THISFILE.TXT`, tworzony jest tylko jeden plik.</span><span class="sxs-lookup"><span data-stu-id="8843f-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="8843f-112">Nazwa pliku zachowuje jego oryginalnej wielkości liter podczas wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="8843f-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8843f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8843f-113">Example</span></span>  
 <span data-ttu-id="8843f-114">Poniższy przykładowy kod ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="8843f-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8843f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8843f-115">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [<span data-ttu-id="8843f-116">Izolowany Magazyn</span><span class="sxs-lookup"><span data-stu-id="8843f-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
