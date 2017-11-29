---
title: "Obsługa wyjątków w wyrażeniach zapytań"
description: "Sposób obsługi wyjątków w wyrażeniach zapytań."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="335ea-104">Obsługa wyjątków w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="335ea-104">Handle exceptions in query expressions</span></span>

<span data-ttu-id="335ea-105">Istnieje możliwość wywołania dowolnej metody w kontekście wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="335ea-105">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="335ea-106">Firma Microsoft zaleca jednak uniknąć wywołaniem jakiejkolwiek jego metody w wyrażeniu zapytania, który może tworzyć efektu ubocznego, takich jak modyfikowania zawartości ze źródłem danych i zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="335ea-106">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="335ea-107">W tym przykładzie pokazano, jak można uniknąć występowanie wyjątków podczas wywołania metody w wyrażeniu zapytania bez naruszania ogólne wytyczne .NET Framework dla obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="335ea-107">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="335ea-108">Stan te wskazówki można przechwytywać określony wyjątek, podczas zrozumienie, dlaczego będzie zostać zgłoszony w danym kontekście.</span><span class="sxs-lookup"><span data-stu-id="335ea-108">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="335ea-109">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące wyjątków](../../standard/exceptions/best-practices-for-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="335ea-109">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="335ea-110">Końcowy przykład przedstawia sposób obsługi tych przypadkach, gdy należy zgłosić wyjątek w trakcie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="335ea-110">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="335ea-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="335ea-111">Example</span></span>  

 <span data-ttu-id="335ea-112">Poniższy przykład przedstawia sposób przenoszenia kodu poza wyrażenie zapytania obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="335ea-112">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="335ea-113">Jest to możliwe tylko wtedy, gdy metoda nie zależy od żadnych zmiennych lokalnych do zapytania.</span><span class="sxs-lookup"><span data-stu-id="335ea-113">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="335ea-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="335ea-114">Example</span></span> 

 <span data-ttu-id="335ea-115">W niektórych przypadkach najlepsze odpowiedzi na wyjątek zgłaszany w obrębie zapytania może być natychmiastowe zatrzymanie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="335ea-115">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="335ea-116">Poniższy przykład przedstawia sposób obsługi wyjątków, które może zostać zgłoszone z wewnątrz treści zapytania.</span><span class="sxs-lookup"><span data-stu-id="335ea-116">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="335ea-117">Przyjęto założenie, że `SomeMethodThatMightThrow` potencjalnie może spowodować wyjątek, który wymaga wykonywania zapytania, aby zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="335ea-117">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="335ea-118">Należy pamiętać, że `try` umieszcza bloku `foreach` pętli i nie zapytania.</span><span class="sxs-lookup"><span data-stu-id="335ea-118">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="335ea-119">Jest to spowodowane `foreach` pętli jest punktem, jaką faktycznie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="335ea-119">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="335ea-120">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="335ea-120">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="335ea-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="335ea-121">See Also</span></span>  
 [<span data-ttu-id="335ea-122">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="335ea-122">LINQ query expressions</span></span>](index.md)
