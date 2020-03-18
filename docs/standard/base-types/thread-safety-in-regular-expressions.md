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
ms.openlocfilehash: db25028e10872cfca08d28518c795414d06c5d49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124799"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="05618-102">Bezpieczeństwo wątków w wyrażeniach regularnych</span><span class="sxs-lookup"><span data-stu-id="05618-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="05618-103">Sama <xref:System.Text.RegularExpressions.Regex> klasa jest bezpieczna i niezmienna wątku (tylko do odczytu).</span><span class="sxs-lookup"><span data-stu-id="05618-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="05618-104">Oznacza to, **że Regex** obiekty mogą być tworzone na dowolnym wątku i współużytkowane między wątkami; pasujące metody można wywołać z dowolnego wątku i nigdy nie zmieniać żadnego stanu globalnego.</span><span class="sxs-lookup"><span data-stu-id="05618-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="05618-105">Jednak obiekty wynik (**Match** i **MatchCollection**) zwracane przez **Regex** powinny być używane w jednym wątku.</span><span class="sxs-lookup"><span data-stu-id="05618-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="05618-106">Mimo że wiele z tych obiektów są logicznie niezmienne, ich implementacje może opóźnić obliczenia niektórych wyników w celu zwiększenia wydajności, a w rezultacie obiekty wywołujące muszą serializować dostęp do nich.</span><span class="sxs-lookup"><span data-stu-id="05618-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="05618-107">Jeśli istnieje potrzeba udostępniania obiektów wyników **Regex** w wielu wątkach, obiekty te można przekonwertować na wystąpienia bezpieczne dla wątków, wywołując ich zsynchronizowane metody.</span><span class="sxs-lookup"><span data-stu-id="05618-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="05618-108">Z wyjątkiem wyliczaczy wszystkie klasy wyrażeń regularnych są bezpieczne dla wątków lub mogą zostać przekształcone w obiekty bezpieczne dla wątków za pomocą metody zsynchronizowanej.</span><span class="sxs-lookup"><span data-stu-id="05618-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="05618-109">Wyliczacze są jedynym wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="05618-109">Enumerators are the only exception.</span></span> <span data-ttu-id="05618-110">Aplikacja musi serializować wywołania modułów wyliczania kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05618-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="05618-111">Regułą jest, że jeśli kolekcja może być wyliczana na więcej niż jeden wątek jednocześnie, należy zsynchronizować metody wyliczania na obiekt główny kolekcji przechodzenie przez wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="05618-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05618-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05618-112">See also</span></span>

- [<span data-ttu-id="05618-113">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="05618-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
