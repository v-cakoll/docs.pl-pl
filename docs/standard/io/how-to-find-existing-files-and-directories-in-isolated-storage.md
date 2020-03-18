---
title: 'Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
ms.openlocfilehash: dfebcc9acf0b699f898c106921d15ce0294bc5d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707136"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="d8343-102">Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="d8343-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="d8343-103">Aby wyszukać katalog w izolowanym <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> magazynie, użyj tej metody.</span><span class="sxs-lookup"><span data-stu-id="d8343-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d8343-104">Ta metoda przyjmuje ciąg, który reprezentuje wzorzec wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d8343-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="d8343-105">We wzorcu wyszukiwania można używać zarówno jednoznakowych (?), jak i wieloznakowych (\*) symboli wieloznacznych, ale symbole wieloznaczne muszą pojawić się w końcowej części nazwy.</span><span class="sxs-lookup"><span data-stu-id="d8343-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="d8343-106">Na przykład `directory1/*ect*` jest prawidłowyciąg `*ect*/directory2` wyszukiwania, ale nie jest.</span><span class="sxs-lookup"><span data-stu-id="d8343-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="d8343-107">Aby wyszukać plik, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> użyj tej metody.</span><span class="sxs-lookup"><span data-stu-id="d8343-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d8343-108">Ograniczenie dla znaków wieloznacznych w ciągach <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> wyszukiwania, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>które mają zastosowanie również do .</span><span class="sxs-lookup"><span data-stu-id="d8343-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="d8343-109">Żadna z tych metod nie jest rekurencyjne; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> klasa nie dostarcza żadnych metod wyświetlania wszystkich katalogów lub plików w sklepie.</span><span class="sxs-lookup"><span data-stu-id="d8343-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="d8343-110">Jednak metody cykliczne są wyświetlane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d8343-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8343-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8343-111">Example</span></span>  
 <span data-ttu-id="d8343-112">W poniższym przykładzie kodu przedstawiono sposób tworzenia plików i katalogów w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="d8343-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="d8343-113">Po pierwsze magazyn, który jest izolowany dla użytkownika, domeny `isoStore` i zestawu jest pobierana i umieszczana w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d8343-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="d8343-114">Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> jest używana do konfigurowania kilku różnych <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> katalogów, a konstruktor tworzy niektóre pliki w tych katalogach.</span><span class="sxs-lookup"><span data-stu-id="d8343-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="d8343-115">Kod następnie pętli za pośrednictwem `GetAllDirectories` wyników metody.</span><span class="sxs-lookup"><span data-stu-id="d8343-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="d8343-116">Ta metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> służy do znajdowania wszystkich nazw katalogów w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d8343-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="d8343-117">Nazwy te są przechowywane w `GetAllDirectories` tablicy, a następnie wywołuje się, przekazując w każdym katalogu, który znalazł.</span><span class="sxs-lookup"><span data-stu-id="d8343-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="d8343-118">W rezultacie wszystkie nazwy katalogów są zwracane w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d8343-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="d8343-119">Następnie kod wywołuje `GetAllFiles` metodę.</span><span class="sxs-lookup"><span data-stu-id="d8343-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="d8343-120">Ta metoda `GetAllDirectories` wywołuje, aby dowiedzieć się nazwy wszystkich katalogów, a następnie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> sprawdza każdy katalog dla plików przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="d8343-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="d8343-121">Wynik jest zwracany w tablicy do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="d8343-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="d8343-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8343-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="d8343-123">Izolowany magazyn</span><span class="sxs-lookup"><span data-stu-id="d8343-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
