---
title: Obsługa wyjątków w wyrażeniach zapytań
description: Sposób obsługi wyjątków w wyrażeniach zapytań.
ms.date: 12/1/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 691373fabeb3934ecc454cbc3b36a5f7bf477bee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284854"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="ad234-103">Obsługa wyjątków w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="ad234-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="ad234-104">Istnieje możliwość wywołania dowolnej metody w kontekście wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="ad234-104">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="ad234-105">Firma Microsoft zaleca jednak uniknąć wywołaniem jakiejkolwiek jego metody w wyrażeniu zapytania, który może tworzyć efektu ubocznego, takich jak modyfikowania zawartości ze źródłem danych i zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ad234-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="ad234-106">W tym przykładzie pokazano, jak można uniknąć występowanie wyjątków podczas wywołania metody w wyrażeniu zapytania bez naruszania ogólne wytyczne .NET Framework dla obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ad234-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="ad234-107">Stan te wskazówki można przechwytywać określony wyjątek, podczas zrozumienie, dlaczego będzie zostać zgłoszony w danym kontekście.</span><span class="sxs-lookup"><span data-stu-id="ad234-107">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="ad234-108">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące wyjątków](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="ad234-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="ad234-109">Końcowy przykład przedstawia sposób obsługi tych przypadkach, gdy należy zgłosić wyjątek w trakcie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="ad234-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad234-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad234-110">Example</span></span>  

 <span data-ttu-id="ad234-111">Poniższy przykład przedstawia sposób przenoszenia kodu poza wyrażenie zapytania obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ad234-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="ad234-112">Jest to możliwe tylko wtedy, gdy metoda nie zależy od żadnych zmiennych lokalnych do zapytania.</span><span class="sxs-lookup"><span data-stu-id="ad234-112">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ad234-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad234-113">Example</span></span> 

 <span data-ttu-id="ad234-114">W niektórych przypadkach najlepsze odpowiedzi na wyjątek zgłaszany w obrębie zapytania może być natychmiastowe zatrzymanie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="ad234-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="ad234-115">Poniższy przykład przedstawia sposób obsługi wyjątków, które może zostać zgłoszone z wewnątrz treści zapytania.</span><span class="sxs-lookup"><span data-stu-id="ad234-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="ad234-116">Przyjęto założenie, że `SomeMethodThatMightThrow` potencjalnie może spowodować wyjątek, który wymaga wykonywania zapytania, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="ad234-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="ad234-117">Należy pamiętać, że `try` umieszcza bloku `foreach` pętli i nie zapytania.</span><span class="sxs-lookup"><span data-stu-id="ad234-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="ad234-118">Jest to spowodowane `foreach` pętli jest punktem, jaką faktycznie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="ad234-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="ad234-119">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="ad234-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="ad234-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad234-120">See Also</span></span>  
 [<span data-ttu-id="ad234-121">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="ad234-121">LINQ query expressions</span></span>](index.md)
