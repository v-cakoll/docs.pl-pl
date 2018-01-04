---
title: "Bezpieczeństwo wątków w wyrażeniach regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 804f83d85206b5f49a0bea290f281b36e18bb847
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="21c25-102">Bezpieczeństwo wątków w wyrażeniach regularnych</span><span class="sxs-lookup"><span data-stu-id="21c25-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="21c25-103"><xref:System.Text.RegularExpressions.Regex> Samej klasy jest wątku bezpieczne i modyfikować (tylko do odczytu).</span><span class="sxs-lookup"><span data-stu-id="21c25-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="21c25-104">Oznacza to **Regex** obiektów można tworzyć w którymkolwiek wątku i udostępniane między wątkami; metod może być wywołana z dowolnego wątku i nigdy nie zmienia żadnych stan globalny.</span><span class="sxs-lookup"><span data-stu-id="21c25-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="21c25-105">Jednak obiekty wynikowe (**dopasowania** i **matchcollection —**) zwrócone przez **Regex** powinien być używany w jednym wątku.</span><span class="sxs-lookup"><span data-stu-id="21c25-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="21c25-106">Mimo że wiele z tych obiektów są logicznie niezmienne, ich implementacji można opóźnić obliczeń pewnych wyników, aby zwiększyć wydajność, a w związku z tym wywołującym musi serializować uzyskiwania do nich dostępu.</span><span class="sxs-lookup"><span data-stu-id="21c25-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="21c25-107">Jeśli trzeba udostępnić **Regex** wynik obiektów na wiele wątków, przez wywołanie jego metody zsynchronizowane można przekonwertować na wątkowo wystąpień tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="21c25-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="21c25-108">Z wyjątkiem moduły wyliczające wszystkie wyrażenia regularnego klasy są bezpieczne dla wątków lub można przekonwertować na obiekty wątkowo Metoda zsynchronizowana.</span><span class="sxs-lookup"><span data-stu-id="21c25-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="21c25-109">Jedynym wyjątkiem są wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="21c25-109">Enumerators are the only exception.</span></span> <span data-ttu-id="21c25-110">Aplikacja musi serializować wywołania wyliczenia kolekcji.</span><span class="sxs-lookup"><span data-stu-id="21c25-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="21c25-111">Reguła jest, że jeśli kolekcja mogą być wyliczane w więcej niż jeden wątek jednocześnie, należy synchronizować modułu wyliczającego metody do obiektu głównego kolekcji przechodzić przez moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="21c25-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c25-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21c25-112">See Also</span></span>  
 [<span data-ttu-id="21c25-113">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="21c25-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
