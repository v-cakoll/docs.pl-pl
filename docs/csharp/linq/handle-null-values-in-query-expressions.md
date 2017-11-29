---
title: "Obsługa wartości zerowych w wyrażeniach zapytań"
description: "Jak Obsługa wartości zerowych w wyrażeniach zapytań."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="handle-null-values-in-query-expressions"></a><span data-ttu-id="f3e87-104">Obsługa wartości zerowych w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="f3e87-104">Handle null values in query expressions</span></span>

<span data-ttu-id="f3e87-105">Ten przykład przedstawia sposób obsługi możliwych wartości null w kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="f3e87-105">This example shows how to handle possible null values in source collections.</span></span> <span data-ttu-id="f3e87-106">Kolekcji obiektów, takich jak <xref:System.Collections.Generic.IEnumerable%601> może zawierać elementy o wartości [null](../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="f3e87-106">An object collection such as an <xref:System.Collections.Generic.IEnumerable%601> can contain elements whose value is [null](../language-reference/keywords/null.md).</span></span> <span data-ttu-id="f3e87-107">Jeśli kolekcja źródłowa ma wartość null lub zawiera element, którego wartość jest równa null, a zapytanie nie obsługuje wartości null, <xref:System.NullReferenceException> zostanie zgłoszony podczas wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="f3e87-107">If a source collection is null or contains an element whose value is null, and your query does not handle null values, a <xref:System.NullReferenceException> will be thrown when you execute the query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e87-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3e87-108">Example</span></span>

 <span data-ttu-id="f3e87-109">Można pamiętać o kodu w celu uniknięcia wyjątek odwołania zerowego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f3e87-109">You can code defensively to avoid a null reference exception as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 <span data-ttu-id="f3e87-110">W poprzednim przykładzie `where` klauzuli odfiltrowuje wszystkie elementy null w sekwencji kategorii.</span><span class="sxs-lookup"><span data-stu-id="f3e87-110">In the previous example, the `where` clause filters out all null elements in the categories sequence.</span></span> <span data-ttu-id="f3e87-111">Ta technika jest niezależna od sprawdzania wartości null w klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="f3e87-111">This technique is independent of the null check in the join clause.</span></span> <span data-ttu-id="f3e87-112">Wyrażenie warunkowe przy użyciu wartości null w tym przykładzie działa, ponieważ `Products.CategoryID` jest typu `int?` który jest skróconą formą `Nullable<int>`.</span><span class="sxs-lookup"><span data-stu-id="f3e87-112">The conditional expression with null in this example works because `Products.CategoryID` is of type `int?` which is shorthand for `Nullable<int>`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e87-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3e87-113">Example</span></span>

 <span data-ttu-id="f3e87-114">W klauzuli join jeśli tylko jeden z kluczy porównania jest typem wartości NULL można rzutować drugą do typu dopuszczającego wartość null w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="f3e87-114">In a join clause, if only one of the comparison keys is a nullable value type, you can cast the other to a nullable type in the query expression.</span></span> <span data-ttu-id="f3e87-115">W poniższym przykładzie przyjęto założenie, że `EmployeeID` jest kolumna zawierająca wartości typu `int?`:</span><span class="sxs-lookup"><span data-stu-id="f3e87-115">In the following example, assume that `EmployeeID` is a column that contains values of type `int?`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f3e87-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3e87-116">See also</span></span>  
 <xref:System.Nullable%601>  
 [<span data-ttu-id="f3e87-117">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="f3e87-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="f3e87-118">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="f3e87-118">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
