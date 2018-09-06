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
ms.openlocfilehash: 08beb44fdb58ab1c1d53f70ac0653348b96fcb18
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886464"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="13a31-102">Porady: tworzenie plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="13a31-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="13a31-103">Po uzyskaniu izolowanym magazynie, można utworzyć katalogów i plików do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="13a31-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="13a31-104">W magazynie i nazw plików i katalogów są określane względem katalogu głównego w wirtualnym systemie plików.</span><span class="sxs-lookup"><span data-stu-id="13a31-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="13a31-105">Aby utworzyć katalog, należy użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metodę wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="13a31-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="13a31-106">Jeśli określisz podkatalogiem katalogu, który nie istnieje, oba katalogi są tworzone.</span><span class="sxs-lookup"><span data-stu-id="13a31-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="13a31-107">Jeśli określisz katalogu, który już istnieje, metoda zwraca bez tworzenia katalogu, a jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="13a31-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="13a31-108">Jednakże, jeśli określisz nazwę katalogu, zawiera nieprawidłowe znaki <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="13a31-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="13a31-109">Aby utworzyć plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="13a31-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="13a31-110">W systemie operacyjnym Windows, wydzielona pamięć masowa plików i katalogów nazw jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="13a31-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="13a31-111">Oznacza to jeśli utworzysz plik o nazwie `ThisFile.txt`, a następnie utwórz inny plik o nazwie `THISFILE.TXT`, jest tworzony tylko jeden plik.</span><span class="sxs-lookup"><span data-stu-id="13a31-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="13a31-112">Nazwa pliku przechowuje swoje oryginalne wielkość liter w wyrazie w celach wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="13a31-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a31-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="13a31-113">Example</span></span>  
 <span data-ttu-id="13a31-114">Poniższy przykładowy kod przedstawia sposób tworzenia plików i katalogów w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="13a31-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="13a31-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13a31-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
- [<span data-ttu-id="13a31-116">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="13a31-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
