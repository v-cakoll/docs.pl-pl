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
- quantity of isolated storage used
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
ms.openlocfilehash: 5666019e1a65880221261ef5ad704f82c37263b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708118"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="3dcf1-102">Porady: przewidywanie warunków braku miejsca w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="3dcf1-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="3dcf1-103">Kod, który używa izolowanego magazynu jest ograniczony przez [przydział,](../../../docs/standard/io/isolated-storage.md#quotas) który określa maksymalny rozmiar przedziału danych, w którym istnieją izolowane pliki magazynu i katalogi.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="3dcf1-104">Przydział jest definiowany przez zasady zabezpieczeń i jest konfigurowalny przez administratorów.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="3dcf1-105">Jeśli maksymalny dozwolony rozmiar zostanie przekroczony podczas <xref:System.IO.IsolatedStorage.IsolatedStorageException> próby zapisania danych, wyjątek zostanie zgłoszony, a operacja zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="3dcf1-106">Pomaga to zapobiegać złośliwym atakom typu "odmowa usługi", które mogą spowodować, że aplikacja odrzuci żądania, ponieważ magazyn danych jest wypełniony.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="3dcf1-107">Aby ułatwić określenie, czy dana próba zapisu może <xref:System.IO.IsolatedStorage.IsolatedStorage> zakończyć się niepowodzeniem z <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>tego <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>powodu, klasa zawiera trzy właściwości tylko do odczytu: , , i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="3dcf1-108">Można użyć tych właściwości, aby ustalić, czy zapis do magazynu spowoduje maksymalny dozwolony rozmiar magazynu, które mają zostać przekroczone.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="3dcf1-109">Należy pamiętać, że izolowany magazyn jest dostępny jednocześnie; w związku z tym podczas obliczania ilości pozostałego magazynu, miejsce do magazynowania może być zużyte przez czas próby zapisu do magazynu.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="3dcf1-110">Można jednak użyć maksymalnego rozmiaru magazynu, aby określić, czy górny limit dostępnego magazynu ma zostać osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="3dcf1-111">Właściwość <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> zależy od dowodów z zestawu do prawidłowego działania.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="3dcf1-112">Z tego powodu należy pobrać tę <xref:System.IO.IsolatedStorage.IsolatedStorageFile> właściwość tylko na obiekty, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>które <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> zostały utworzone przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, , lub metody.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="3dcf1-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>obiekty, które zostały utworzone w jakikolwiek inny sposób (na <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> przykład obiekty, które zostały zwrócone z metody) nie zwróci dokładny maksymalny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="3dcf1-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="3dcf1-114">Example</span></span>

<span data-ttu-id="3dcf1-115">Poniższy przykład kodu uzyskuje izolowany magazyn, tworzy kilka <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> plików i pobiera właściwość.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="3dcf1-116">Pozostałe miejsce jest zgłaszane w bajtach.</span><span class="sxs-lookup"><span data-stu-id="3dcf1-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="3dcf1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dcf1-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="3dcf1-118">Izolowany magazyn</span><span class="sxs-lookup"><span data-stu-id="3dcf1-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="3dcf1-119">Porady: uzyskiwanie magazynów dla izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="3dcf1-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
