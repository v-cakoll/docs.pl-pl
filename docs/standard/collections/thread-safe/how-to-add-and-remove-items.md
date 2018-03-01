---
title: "Porady: dodawanie i usuwanie elementów ConcurrentDictionary"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4ef7c8050b26cffeed03cc394193116f8f6797a9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a><span data-ttu-id="d92c4-102">Porady: dodawanie i usuwanie elementów ConcurrentDictionary</span><span class="sxs-lookup"><span data-stu-id="d92c4-102">How to: Add and Remove Items from a ConcurrentDictionary</span></span>
<span data-ttu-id="d92c4-103">W tym przykładzie pokazano, jak dodać, pobierania, aktualizowanie i usuwanie elementów z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d92c4-103">This example shows how to add, retrieve, update, and remove items from a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d92c4-104">Ta klasa kolekcji jest implementacją wątkowo.</span><span class="sxs-lookup"><span data-stu-id="d92c4-104">This collection class is a thread-safe implementation.</span></span> <span data-ttu-id="d92c4-105">Zaleca się używania jej w każdym przypadku, gdy wiele wątków może próby uzyskania dostępu do elementów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="d92c4-105">We recommend that you use it whenever multiple threads might be attempting to access the elements concurrently.</span></span>  
  
 <span data-ttu-id="d92c4-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602>zapewnia kilka metod wygody wchodzące niepotrzebnych kodu najpierw sprawdź, czy istnieje klucz przed próbuje dodać lub usunąć dane.</span><span class="sxs-lookup"><span data-stu-id="d92c4-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> provides several convenience methods that make it unnecessary for code to first check whether a key exists before it attempts to add or remove data.</span></span> <span data-ttu-id="d92c4-107">Poniższej tabeli wymieniono te metody wygody oraz opis ich użycie.</span><span class="sxs-lookup"><span data-stu-id="d92c4-107">The following table lists these convenience methods and describes when to use them.</span></span>  
  
|<span data-ttu-id="d92c4-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="d92c4-108">Method</span></span>|<span data-ttu-id="d92c4-109">Używany, gdy...</span><span class="sxs-lookup"><span data-stu-id="d92c4-109">Use when…</span></span>|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|<span data-ttu-id="d92c4-110">Aby dodać nową wartość dla określonego klucza i, jeśli klucz już istnieje, chcesz zastąpić jej wartość.</span><span class="sxs-lookup"><span data-stu-id="d92c4-110">You want to add a new value for a specified key and, if the key already exists, you want to replace its value.</span></span>|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|<span data-ttu-id="d92c4-111">Chcesz pobrać istniejące wartości dla określonego klucza i, jeśli klucz nie istnieje, ma zostać określone pary klucza/wartości.</span><span class="sxs-lookup"><span data-stu-id="d92c4-111">You want to retrieve the existing value for a specified key and, if the key does not exist, you want to specify a key/value pair.</span></span>|  
|<span data-ttu-id="d92c4-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span><span class="sxs-lookup"><span data-stu-id="d92c4-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span></span>|<span data-ttu-id="d92c4-113">Chcesz dodać, get, zaktualizować lub usunąć pary klucz wartość, a jeśli klucz już istnieje lub próba nie powiedzie się z jakiegokolwiek powodu, chcesz wykonać niektóre akcje, alternatywnych.</span><span class="sxs-lookup"><span data-stu-id="d92c4-113">You want to add, get, update, or remove a key/value pair, and, if the key already exists or the attempt fails for any other reason, you want to take some alternative action.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d92c4-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d92c4-114">Example</span></span>  
 <span data-ttu-id="d92c4-115">W poniższym przykładzie użyto dwóch <xref:System.Threading.Tasks.Task> wystąpień, aby dodać niektóre elementy do <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jednocześnie, a następnie wyświetla całą zawartość, aby pokazać, że elementy nie zostały dodane pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d92c4-115">The following example uses two <xref:System.Threading.Tasks.Task> instances to add some elements to a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> concurrently, and then outputs all of the contents to show that the elements were added successfully.</span></span> <span data-ttu-id="d92c4-116">W przykładzie przedstawiono również sposób użycia <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody dodawania, aktualizacji i pobierania elementów z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d92c4-116">The example also shows how to use the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to add, update, and retrieve  items from the collection.</span></span>  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <span data-ttu-id="d92c4-117"><xref:System.Collections.Concurrent.ConcurrentDictionary%602>jest przeznaczony do scenariuszy wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="d92c4-117"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> is designed for multithreaded scenarios.</span></span> <span data-ttu-id="d92c4-118">Nie trzeba stosować blokady w kodzie, aby dodać lub usunąć elementy z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d92c4-118">You do not have to use locks in your code to add or remove items from the collection.</span></span> <span data-ttu-id="d92c4-119">Jednak zawsze jest jeden wątek, aby pobrać wartości i inny wątek natychmiast zaktualizować kolekcji, zapewniając nową wartość w taki sam klucz.</span><span class="sxs-lookup"><span data-stu-id="d92c4-119">However, it is always possible for one thread to retrieve a value, and another thread to immediately update the collection by giving the same key a new value.</span></span>  
  
 <span data-ttu-id="d92c4-120">Ponadto mimo że wszystkie metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są wątkowo, nie wszystkie metody są atomic, w szczególności <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.</span><span class="sxs-lookup"><span data-stu-id="d92c4-120">Also, although all methods of <xref:System.Collections.Concurrent.ConcurrentDictionary%602> are thread-safe, not all methods are atomic, specifically <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.</span></span> <span data-ttu-id="d92c4-121">Delegowanie użytkownika, który jest przekazywany do tych metod jest wywoływany poza słownik wewnętrzny blokady.</span><span class="sxs-lookup"><span data-stu-id="d92c4-121">The user delegate that is passed to these methods is invoked outside of the dictionary's internal lock.</span></span> <span data-ttu-id="d92c4-122">(Jest to na celu zapobieganie blokuje wszystkie wątki nieznany kod.) Dlatego możliwe jest dla tej sekwencji zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="d92c4-122">(This is done to prevent unknown code from blocking all threads.) Therefore it is possible for this sequence of events to occur:</span></span>  
  
 <span data-ttu-id="d92c4-123">1\) wywołania threadA <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, znajdzie żadnego elementu i tworzy nowy element do dodania, wywołując delegata obiekt valueFactory.</span><span class="sxs-lookup"><span data-stu-id="d92c4-123">1\) threadA calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, finds no item and creates a new item to Add by invoking the valueFactory delegate.</span></span>  
  
 <span data-ttu-id="d92c4-124">2\) wywołania threadB <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> jednocześnie, swojego delegata obiekt valueFactory jest wywoływana dociera wewnętrzny blokady przed threadA i dlatego jego nowej pary klucz wartość zostanie dodany do słownika.</span><span class="sxs-lookup"><span data-stu-id="d92c4-124">2\) threadB calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> concurrently, its valueFactory delegate is invoked and it arrives at the internal lock before threadA, and so its new key-value pair is added to the dictionary.</span></span>  
  
 <span data-ttu-id="d92c4-125">3\) ukończeniu delegowanie użytkownika w threadA i Wątek dociera blokady, ale teraz widzi element już istnieje</span><span class="sxs-lookup"><span data-stu-id="d92c4-125">3\) threadA's user delegate completes, and the thread arrives at the lock, but now sees that the item exists already</span></span>  
  
 <span data-ttu-id="d92c4-126">4\) threadA wykonuje procedurę "Get" i zwraca dane, które zostało dodane wcześniej threadB.</span><span class="sxs-lookup"><span data-stu-id="d92c4-126">4\) threadA performs a "Get", and returns the data that was previously added by threadB.</span></span>  
  
 <span data-ttu-id="d92c4-127">W związku z tym nie jest gwarancję, że dane, który jest zwracany przez <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> jest tych samych danych, który został utworzony przez obiekt valueFactory wątku.</span><span class="sxs-lookup"><span data-stu-id="d92c4-127">Therefore, it is not guaranteed that the data that is returned by <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> is the same data that was created by the thread's valueFactory.</span></span> <span data-ttu-id="d92c4-128">Podobne sekwencję zdarzeń, może wystąpić podczas <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d92c4-128">A similar sequence of events can occur when <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d92c4-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d92c4-129">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="d92c4-130">Kolekcje bezpieczne wątkowo</span><span class="sxs-lookup"><span data-stu-id="d92c4-130">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
