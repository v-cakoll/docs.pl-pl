---
title: 'Instrukcje: Wyszukiwanie istniejących plików i katalogów w izolowanym magazynie'
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
ms.openlocfilehash: ec1d1fbdefdad3ec0dd2c07fbc1278e4d1d217c6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291854"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="42b70-102">Instrukcje: Wyszukiwanie istniejących plików i katalogów w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="42b70-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="42b70-103">Aby wyszukać katalog w izolowanym magazynie, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="42b70-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42b70-104">Ta metoda pobiera ciąg, który reprezentuje wzorzec wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="42b70-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="42b70-105">W wzorcu wyszukiwania można używać znaków wieloznacznych (?) i wieloznakowych ( \* ), ale symbole wieloznaczne muszą pojawić się w końcowej części nazwy.</span><span class="sxs-lookup"><span data-stu-id="42b70-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="42b70-106">Na przykład, `directory1/*ect*` jest prawidłowym ciągiem wyszukiwania, ale `*ect*/directory2` nie jest.</span><span class="sxs-lookup"><span data-stu-id="42b70-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="42b70-107">Aby wyszukać plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="42b70-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42b70-108">Ograniczenie symboli wieloznacznych w ciągach wyszukiwania, które mają zastosowanie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> również do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> .</span><span class="sxs-lookup"><span data-stu-id="42b70-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="42b70-109">Żadna z tych metod nie jest cykliczna; <xref:System.IO.IsolatedStorage.IsolatedStorageFile>Klasa nie dostarcza żadnych metod wyświetlania wszystkich katalogów lub plików w sklepie.</span><span class="sxs-lookup"><span data-stu-id="42b70-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="42b70-110">Jednak metody cykliczne są wyświetlane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="42b70-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42b70-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="42b70-111">Example</span></span>  
 <span data-ttu-id="42b70-112">Poniższy przykład kodu ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="42b70-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="42b70-113">Po pierwsze magazyn, który jest izolowany dla użytkownika, domeny i zestawu, jest pobierany i umieszczany w `isoStore` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="42b70-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="42b70-114">Ta <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Metoda służy do konfigurowania kilku różnych katalogów, a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Konstruktor tworzy niektóre pliki w tych katalogach.</span><span class="sxs-lookup"><span data-stu-id="42b70-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="42b70-115">Kod następnie pętle przez wyniki `GetAllDirectories` metody.</span><span class="sxs-lookup"><span data-stu-id="42b70-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="42b70-116">Ta metoda używa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> do znajdowania wszystkich nazw katalogów w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="42b70-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="42b70-117">Te nazwy są przechowywane w tablicy, a następnie `GetAllDirectories` wywołują się do siebie, przekazując w każdy znaleziony katalog.</span><span class="sxs-lookup"><span data-stu-id="42b70-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="42b70-118">W związku z tym wszystkie nazwy katalogów są zwracane w tablicy.</span><span class="sxs-lookup"><span data-stu-id="42b70-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="42b70-119">Następnie kod wywołuje `GetAllFiles` metodę.</span><span class="sxs-lookup"><span data-stu-id="42b70-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="42b70-120">Ta metoda wywołuje `GetAllDirectories` wszystkie nazwy katalogów, a następnie sprawdza każdy katalog dla plików przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="42b70-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="42b70-121">Wynik jest zwracany w tablicy do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="42b70-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="42b70-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42b70-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="42b70-123">Magazyn izolowany</span><span class="sxs-lookup"><span data-stu-id="42b70-123">Isolated Storage</span></span>](isolated-storage.md)
