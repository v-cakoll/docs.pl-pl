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
ms.openlocfilehash: 83e8c800dc74d9689f1bfdb506a6b454e87b36ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707873"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="66c2c-102">Porady: tworzenie plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="66c2c-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="66c2c-103">Po uzyskaniu izolowanego magazynu można utworzyć katalogi i pliki do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="66c2c-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="66c2c-104">W magazynie nazwy plików i katalogów są określone w odniesieniu do katalogu głównego wirtualnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="66c2c-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="66c2c-105">Aby utworzyć katalog, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> należy użyć metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="66c2c-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="66c2c-106">Jeśli określisz podkatalog katalogu, który nie istnieje, zostaną utworzone oba katalogi.</span><span class="sxs-lookup"><span data-stu-id="66c2c-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="66c2c-107">Jeśli określisz katalog, który już istnieje, metoda zwraca bez tworzenia katalogu i nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="66c2c-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="66c2c-108">Jeśli jednak określisz nazwę katalogu zawierającą <xref:System.IO.IsolatedStorage.IsolatedStorageException> nieprawidłowe znaki, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="66c2c-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="66c2c-109">Aby utworzyć plik, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> użyj tej metody.</span><span class="sxs-lookup"><span data-stu-id="66c2c-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="66c2c-110">W systemie operacyjnym Windows izolowane nazwy plików magazynu i katalogów są niewrażliwe.</span><span class="sxs-lookup"><span data-stu-id="66c2c-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="66c2c-111">Oznacza to, że jeśli `ThisFile.txt`utworzysz plik `THISFILE.TXT`o nazwie , a następnie utworzysz inny plik o nazwie , zostanie utworzony tylko jeden plik.</span><span class="sxs-lookup"><span data-stu-id="66c2c-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="66c2c-112">Nazwa pliku zachowuje oryginalną obudowę do celów wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="66c2c-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66c2c-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="66c2c-113">Example</span></span>  
 <span data-ttu-id="66c2c-114">W poniższym przykładzie kodu przedstawiono sposób tworzenia plików i katalogów w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="66c2c-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="66c2c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66c2c-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="66c2c-116">Izolowany magazyn</span><span class="sxs-lookup"><span data-stu-id="66c2c-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
