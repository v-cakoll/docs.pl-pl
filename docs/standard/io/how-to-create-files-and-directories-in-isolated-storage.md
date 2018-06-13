---
title: 'Porady: tworzenie plików i katalogów w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7fa96e4f28e92e0890acf6ffc105ca11a97d575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575190"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="dd7c2-102">Porady: tworzenie plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="dd7c2-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="dd7c2-103">Po uzyskaniu izolowanego magazynu można utworzyć katalogów i plików do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="dd7c2-104">W sklepie nazwy plików i katalogów są określane względem katalogu głównego wirtualnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="dd7c2-105">Aby utworzyć katalog, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="dd7c2-106">Jeśli określisz podkatalogiem katalogu, który nie istnieje, obie katalogi są tworzone.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="dd7c2-107">Jeśli określisz katalogu, który już istnieje, metoda zwraca bez tworzenia katalogu, a nie wyjątek.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="dd7c2-108">Jednak jeśli określono nazwę katalogu zawiera nieprawidłowe znaki <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="dd7c2-109">Aby utworzyć plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="dd7c2-110">W systemie operacyjnym Windows, izolowanego magazynu plików i katalogów nazwy jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="dd7c2-111">Oznacza to czy utworzony plik o nazwie `ThisFile.txt`, a następnie utwórz plik o nazwie `THISFILE.TXT`, tworzony jest tylko jeden plik.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="dd7c2-112">Nazwa pliku zachowuje jego oryginalnej wielkości liter podczas wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd7c2-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd7c2-113">Example</span></span>  
 <span data-ttu-id="dd7c2-114">Poniższy przykładowy kod ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="dd7c2-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dd7c2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd7c2-115">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [<span data-ttu-id="dd7c2-116">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="dd7c2-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
