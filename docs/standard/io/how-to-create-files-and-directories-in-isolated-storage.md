---
title: 'Instrukcje: Tworzenie plików i katalogów w izolowanym magazynie'
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
ms.openlocfilehash: d5e086e77ab6309fa0757ef32b620e0fdbc1f627
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413044"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="f5942-102">Instrukcje: Tworzenie plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="f5942-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="f5942-103">Po uzyskaniu izolowanego magazynu można utworzyć katalogi i pliki do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="f5942-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="f5942-104">W magazynie nazwy plików i katalogów są określone w odniesieniu do katalogu głównego wirtualnego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="f5942-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="f5942-105">Aby utworzyć katalog, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metody Instance.</span><span class="sxs-lookup"><span data-stu-id="f5942-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="f5942-106">W przypadku określenia podkatalogu katalogu, który nie istnieje, tworzone są oba katalogi.</span><span class="sxs-lookup"><span data-stu-id="f5942-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="f5942-107">Jeśli określisz katalog, który już istnieje, metoda zwraca bez tworzenia katalogu i nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f5942-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="f5942-108">Jednak w przypadku określenia nazwy katalogu, która zawiera nieprawidłowe znaki, <xref:System.IO.IsolatedStorage.IsolatedStorageException> zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f5942-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="f5942-109">Aby utworzyć plik, należy użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f5942-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f5942-110">W systemie operacyjnym Windows, izolowany plik magazynu i nazwy katalogów nie uwzględnia wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="f5942-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="f5942-111">Oznacza to, że jeśli utworzysz plik o nazwie `ThisFile.txt` , a następnie utworzysz inny plik o nazwie `THISFILE.TXT` , zostanie utworzony tylko jeden plik.</span><span class="sxs-lookup"><span data-stu-id="f5942-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="f5942-112">Nazwa pliku zachowuje pierwotną wielkość liter na potrzeby wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="f5942-112">The file name keeps its original casing for display purposes.</span></span>  

 <span data-ttu-id="f5942-113">Utworzenie pliku magazynu izolowanego spowoduje zgłoszenie, <xref:System.IO.IsolatedStorage.IsolatedStorageException> czy ścieżka zawiera katalog, który nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f5942-113">Isolated storage file creation will throw an <xref:System.IO.IsolatedStorage.IsolatedStorageException> if the path contains a directory that does not exist.</span></span>
  
## <a name="example"></a><span data-ttu-id="f5942-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5942-114">Example</span></span>  
 <span data-ttu-id="f5942-115">Poniższy przykład kodu ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="f5942-115">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f5942-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5942-116">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="f5942-117">Magazyn izolowany</span><span class="sxs-lookup"><span data-stu-id="f5942-117">Isolated Storage</span></span>](isolated-storage.md)
