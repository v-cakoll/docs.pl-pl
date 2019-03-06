---
title: 'Instrukcje: Przewidywanie warunków limit miejsca w wydzielonej pamięci masowej'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf5144cb1abd3a916d2b5afc361c8c96a221d47e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372298"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="abc10-102">Instrukcje: Przewidywanie warunków limit miejsca w wydzielonej pamięci masowej</span><span class="sxs-lookup"><span data-stu-id="abc10-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="abc10-103">Kod, który używa wydzielona pamięć masowa jest ograniczony przez [przydziału](../../../docs/standard/io/isolated-storage.md#quotas) , który określa maksymalny rozmiar przedział danych, w którym izolowany magazyn plików i katalogów istnieje.</span><span class="sxs-lookup"><span data-stu-id="abc10-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="abc10-104">Limit przydziału jest definiowany przez zasady zabezpieczeń i jest konfigurowane przez administratorów.</span><span class="sxs-lookup"><span data-stu-id="abc10-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="abc10-105">Gdy maksymalny dozwolony rozmiar zostanie przekroczony podczas próby zapisu danych, <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku i kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="abc10-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="abc10-106">Pozwala to zapobiec złośliwymi atakami typu "odmowa usługi", które może spowodować, że aplikacja odmowy żądania, ponieważ Magazyn danych jest wypełnione.</span><span class="sxs-lookup"><span data-stu-id="abc10-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="abc10-107">Aby ułatwić ustalenie, czy próba zapisu danego prawdopodobnie się nie powieść z tego powodu <xref:System.IO.IsolatedStorage.IsolatedStorage> klasa udostępnia trzy właściwości tylko do odczytu: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span><span class="sxs-lookup"><span data-stu-id="abc10-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="abc10-108">Te właściwości można użyć do określenia, czy zapisywanie w magazynie spowoduje, że maksymalny dozwolony rozmiar magazynu zostać przekroczony.</span><span class="sxs-lookup"><span data-stu-id="abc10-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="abc10-109">Należy pamiętać, że isolated storage może być uzyskiwany współbieżnie, w związku z tym gdy obliczeniowe ilości pozostałego magazynu miejsca do magazynowania może być używana przez czas podczas próby zapisu w magazynie.</span><span class="sxs-lookup"><span data-stu-id="abc10-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="abc10-110">Jednak można użyć maksymalny rozmiar magazynu w celu określenia, czy górny limit na dostępny magazyn jest wkrótce osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="abc10-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="abc10-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Właściwości zależy od dowodów z zestawu, aby zapewnić prawidłowe działanie.</span><span class="sxs-lookup"><span data-stu-id="abc10-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="abc10-112">Z tego powodu należy pobrać tej właściwości, tylko na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które zostały utworzone przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="abc10-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="abc10-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiekty, które zostały utworzone w jakikolwiek inny sposób (na przykład, obiekty, które zostały zwrócone przez <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda) nie będzie zwracać odpowiedni rozmiar maksymalny.</span><span class="sxs-lookup"><span data-stu-id="abc10-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="abc10-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="abc10-114">Example</span></span>

<span data-ttu-id="abc10-115">Poniższy przykładowy kod uzyskuje w izolowanym magazynie, tworzy kilka plików i pobiera <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="abc10-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="abc10-116">Ilość wolnego miejsca jest zgłaszany w bajtach.</span><span class="sxs-lookup"><span data-stu-id="abc10-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="abc10-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abc10-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="abc10-118">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="abc10-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="abc10-119">Instrukcje: Uzyskiwanie magazynów dla wydzielonej pamięci masowej</span><span class="sxs-lookup"><span data-stu-id="abc10-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
