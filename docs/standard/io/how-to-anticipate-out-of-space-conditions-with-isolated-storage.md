---
title: 'Porady: przewidywanie warunków braku miejsca w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b99803970b205e3dbbb1d78c9bdaf0fefa73a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575583"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="d4588-102">Porady: przewidywanie warunków braku miejsca w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="d4588-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>
<span data-ttu-id="d4588-103">Kod, który korzysta z magazynu izolowanego jest ograniczane przez [przydziału](../../../docs/standard/io/isolated-storage.md#quotas) , który określa maksymalny rozmiar dla przedziału danych, w którym odizolowane pliki i katalogi istnieją.</span><span class="sxs-lookup"><span data-stu-id="d4588-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="d4588-104">Limit przydziału jest definiowana za pomocą zasad zabezpieczeń i jest konfigurowane przez administratorów.</span><span class="sxs-lookup"><span data-stu-id="d4588-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="d4588-105">Jeśli maksymalny dozwolony rozmiar jest przekroczony podczas próby zapisu danych, <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku i kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d4588-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="d4588-106">Pomaga to zapobiec złośliwymi atakami typu "odmowa usługi", które może spowodować aplikacji odrzucać żądania, ponieważ Magazyn danych jest wypełnione.</span><span class="sxs-lookup"><span data-stu-id="d4588-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>  
  
 <span data-ttu-id="d4588-107">Aby ułatwić określenie, czy mogą kończyć się niepowodzeniem z tego powodu, próba zapisu danego <xref:System.IO.IsolatedStorage.IsolatedStorage> klasa udostępnia trzy właściwości tylko do odczytu: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4588-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="d4588-108">Te właściwości można użyć do określenia, czy zapisywanie w magazynie spowoduje, że maksymalny dozwolony rozmiar magazynu przekroczenie.</span><span class="sxs-lookup"><span data-stu-id="d4588-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="d4588-109">Należy pamiętać, że izolowanego magazynu jest możliwy jednocześnie; w związku z tym obliczeniowe ilości pozostałego miejsca, miejsca do magazynowania może być używane podczas próby zapisu w magazynie.</span><span class="sxs-lookup"><span data-stu-id="d4588-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="d4588-110">Jednak służy maksymalny rozmiar magazynu w celu określenia, czy górny limit na dostępny magazyn o się można nawiązać połączenia.</span><span class="sxs-lookup"><span data-stu-id="d4588-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>  
  
 <span data-ttu-id="d4588-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Właściwość zależy od dowód z zestawu do poprawnego działania.</span><span class="sxs-lookup"><span data-stu-id="d4588-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="d4588-112">Z tego powodu tej właściwości powinno pobrać tylko na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które zostały utworzone przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d4588-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="d4588-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiekty, które zostały utworzone w inny sposób (na przykład w przypadku obiektów, które zostały zwrócone z <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda) nie zwróci odpowiedni rozmiar maksymalny.</span><span class="sxs-lookup"><span data-stu-id="d4588-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4588-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4588-114">Example</span></span>  
 <span data-ttu-id="d4588-115">Poniższy przykładowy kod uzyskuje izolowanego magazynu tworzy kilka plików i pobiera <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d4588-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="d4588-116">Pozostałe miejsce jest zgłaszana w bajtach.</span><span class="sxs-lookup"><span data-stu-id="d4588-116">The remaining space is reported in bytes.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="d4588-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4588-117">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="d4588-118">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="d4588-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="d4588-119">Instrukcje: uzyskiwanie magazynów dla wydzielonej pamięci masowej</span><span class="sxs-lookup"><span data-stu-id="d4588-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
