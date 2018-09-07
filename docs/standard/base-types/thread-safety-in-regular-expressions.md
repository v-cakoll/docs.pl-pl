---
title: Bezpieczeństwo wątków w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0bcab0757bc48f6a8216dd5878f0289e49a275
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44046882"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="36827-102">Bezpieczeństwo wątków w wyrażeniach regularnych</span><span class="sxs-lookup"><span data-stu-id="36827-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="36827-103"><xref:System.Text.RegularExpressions.Regex> Samej klasy jest wątek, bezpieczne i niezmienne (tylko do odczytu).</span><span class="sxs-lookup"><span data-stu-id="36827-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="36827-104">Oznacza to, że **wyrażenia regularnego** obiekty można tworzyć na żadnym z wątków i udostępniane między wątkami; metod dopasowania mogą być wywoływane z żadnym z wątków i nigdy nie zmienia żadnych stan globalny.</span><span class="sxs-lookup"><span data-stu-id="36827-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="36827-105">Jednak obiekty wynikowe (**dopasowanie** i **matchcollection —**) zwróciło **wyrażenia regularnego** powinny być używane w jednym wątku.</span><span class="sxs-lookup"><span data-stu-id="36827-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="36827-106">Chociaż wiele z tych obiektów są logicznie niezmienne, ich implementacji może opóźnić obliczenie niektórych wyników, aby zwiększyć wydajność, a w rezultacie obiekty wywołujące muszą serializację do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="36827-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="36827-107">Jeśli zachodzi potrzeba udostępniania **wyrażenia regularnego** wynik obiektów w wielu wątkach, te obiekty mogą być konwertowane do wystąpień wątków przez wywołanie metody ich zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="36827-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="36827-108">Z wyjątkiem moduły wyliczające wszystkie klasy wyrażeń regularnych są bezpieczne dla wątków lub mogą być konwertowane na obiekty wątków przez metodę zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="36827-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="36827-109">Jedynym wyjątkiem są wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="36827-109">Enumerators are the only exception.</span></span> <span data-ttu-id="36827-110">Aplikację należy serializować wywołania do kolekcji wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="36827-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="36827-111">Reguła jest, że jeśli kolekcji mogą być wyliczane w więcej niż jeden wątek jednocześnie, należy zsynchronizować modułu wyliczającego metod w głównym obiekcie kolekcji-przenoszone przez moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="36827-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36827-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36827-112">See also</span></span>

- [<span data-ttu-id="36827-113">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="36827-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
