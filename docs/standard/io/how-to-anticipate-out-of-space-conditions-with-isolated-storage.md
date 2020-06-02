---
title: 'Instrukcje: Przewidywanie warunków braku miejsca w izolowanym magazynie'
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
ms.openlocfilehash: bdc2cee343e9d9be44230e84ff45d6fa54901f48
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288592"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="f6c09-102">Instrukcje: Przewidywanie warunków braku miejsca w izolowanym magazynie</span><span class="sxs-lookup"><span data-stu-id="f6c09-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="f6c09-103">Kod korzystający z izolowanego magazynu jest ograniczony przez [przydział](isolated-storage.md#quotas) , który określa maksymalny rozmiar przedziału danych, w którym znajdują się pliki i katalogi izolowanych magazynów.</span><span class="sxs-lookup"><span data-stu-id="f6c09-103">Code that uses isolated storage is constrained by a [quota](isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="f6c09-104">Przydział jest definiowany przez zasady zabezpieczeń i jest konfigurowalny przez administratorów.</span><span class="sxs-lookup"><span data-stu-id="f6c09-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="f6c09-105">Jeśli maksymalny dozwolony rozmiar zostanie przekroczony podczas próby zapisu danych, <xref:System.IO.IsolatedStorage.IsolatedStorageException> zgłaszany jest wyjątek, a operacja kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f6c09-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="f6c09-106">Pomaga to zapobiegać złośliwym atakom typu "odmowa usługi", co może spowodować odrzucenie żądań przez aplikację, ponieważ magazyn danych jest wypełniony.</span><span class="sxs-lookup"><span data-stu-id="f6c09-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="f6c09-107">Aby ułatwić określenie, czy dana próba zapisu prawdopodobnie nie powiedzie się z tego powodu, <xref:System.IO.IsolatedStorage.IsolatedStorage> Klasa zawiera trzy właściwości tylko do odczytu: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> , <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> , i <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> .</span><span class="sxs-lookup"><span data-stu-id="f6c09-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="f6c09-108">Za pomocą tych właściwości można określić, czy zapis w sklepie spowoduje przekroczenie maksymalnego dozwolonego rozmiaru magazynu.</span><span class="sxs-lookup"><span data-stu-id="f6c09-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="f6c09-109">Należy pamiętać, że dostęp do wydzielonego magazynu jest możliwy współbieżnie; w związku z tym podczas obliczania ilości pozostałego miejsca do magazynowania mogą być używane przez czas, w którym próbujesz zapisać w sklepie.</span><span class="sxs-lookup"><span data-stu-id="f6c09-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="f6c09-110">Można jednak użyć maksymalnego rozmiaru magazynu, aby określić, czy górny limit dostępnego magazynu ma zostać osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="f6c09-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="f6c09-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>Właściwość zależy od dowodów z zestawu, aby działała prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="f6c09-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="f6c09-112">Z tego powodu należy pobrać tę właściwość tylko dla <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które zostały utworzone przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> metody, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> .</span><span class="sxs-lookup"><span data-stu-id="f6c09-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="f6c09-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>obiekty, które zostały utworzone w inny sposób (na przykład obiekty, które zostały zwrócone z <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody) nie będą zwracać dokładnego maksymalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="f6c09-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="f6c09-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6c09-114">Example</span></span>

<span data-ttu-id="f6c09-115">Poniższy przykład kodu uzyskuje izolowany magazyn, tworzy kilka plików i pobiera <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="f6c09-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="f6c09-116">Pozostałe miejsce jest raportowane w bajtach.</span><span class="sxs-lookup"><span data-stu-id="f6c09-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="f6c09-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6c09-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="f6c09-118">Magazyn izolowany</span><span class="sxs-lookup"><span data-stu-id="f6c09-118">Isolated Storage</span></span>](isolated-storage.md)
- [<span data-ttu-id="f6c09-119">Instrukcje: Uzyskiwanie magazynów dla izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="f6c09-119">How to: Obtain Stores for Isolated Storage</span></span>](how-to-obtain-stores-for-isolated-storage.md)
