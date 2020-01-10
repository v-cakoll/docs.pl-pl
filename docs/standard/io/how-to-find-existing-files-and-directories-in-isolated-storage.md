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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707136"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="fe2b3-102">Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="fe2b3-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="fe2b3-103">Aby wyszukać katalog w izolowanym magazynie, użyj metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe2b3-104">Ta metoda pobiera ciąg, który reprezentuje wzorzec wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="fe2b3-105">W wzorcu wyszukiwania można używać znaków wieloznacznych (?) i wieloznakowych (\*), ale symbole wieloznaczne muszą pojawić się w końcowej części nazwy.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="fe2b3-106">Na przykład `directory1/*ect*` jest prawidłowym ciągiem wyszukiwania, ale `*ect*/directory2` nie jest.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="fe2b3-107">Aby wyszukać plik, użyj metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe2b3-108">Ograniczenie symboli wieloznacznych w ciągach wyszukiwania odnoszące się do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> ma zastosowanie również do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="fe2b3-109">Żadna z tych metod nie jest cykliczna; Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nie dostarcza żadnych metod wyświetlania wszystkich katalogów lub plików w sklepie.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="fe2b3-110">Jednak metody cykliczne są wyświetlane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe2b3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe2b3-111">Example</span></span>  
 <span data-ttu-id="fe2b3-112">Poniższy przykład kodu ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="fe2b3-113">Po pierwsze magazyn, który jest izolowany dla użytkownika, domeny i zestawu, jest pobierany i umieszczany w zmiennej `isoStore`.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="fe2b3-114">Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> służy do konfigurowania kilku różnych katalogów, a Konstruktor <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> tworzy niektóre pliki w tych katalogach.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="fe2b3-115">Kod następnie pętle przez wyniki metody `GetAllDirectories`.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="fe2b3-116">Ta metoda używa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> do znajdowania wszystkich nazw katalogów w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="fe2b3-117">Te nazwy są przechowywane w tablicy, a następnie `GetAllDirectories` wywołuje same, przekazując w każdy znaleziony katalog.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="fe2b3-118">W związku z tym wszystkie nazwy katalogów są zwracane w tablicy.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="fe2b3-119">Następnie kod wywołuje metodę `GetAllFiles`.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="fe2b3-120">Ta metoda wywołuje `GetAllDirectories`, aby znaleźć nazwy wszystkich katalogów, a następnie sprawdza każdy katalog dla plików przy użyciu metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="fe2b3-121">Wynik jest zwracany w tablicy do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="fe2b3-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="fe2b3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe2b3-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="fe2b3-123">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="fe2b3-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
