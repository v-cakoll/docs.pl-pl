---
title: Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150145"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="7b757-102">Znane problemy i zagadnienia dotyczące składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7b757-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="7b757-103">Ta sekcja zawiera informacje o znanych problemach z LINQ do kwerend jednostek.</span><span class="sxs-lookup"><span data-stu-id="7b757-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="7b757-104">Zapytania LINQ, których nie można buforować</span><span class="sxs-lookup"><span data-stu-id="7b757-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="7b757-105">Zamówienie utraconych informacji</span><span class="sxs-lookup"><span data-stu-id="7b757-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="7b757-106">Niepodpisane liczby całkowite nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="7b757-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="7b757-107">Błędy konwersji typu</span><span class="sxs-lookup"><span data-stu-id="7b757-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="7b757-108">Odwoływanie się do zmiennych nieskawaralnych, które nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="7b757-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="7b757-109">Zagnieżdżone kwerendy mogą zakończyć się niepowodzeniem w programie SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="7b757-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="7b757-110">Rzutowanie typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="7b757-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="7b757-111">Zapytania LINQ, których nie można buforować</span><span class="sxs-lookup"><span data-stu-id="7b757-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="7b757-112">Począwszy od .NET Framework 4.5, LINQ do jednostek kwerendy są automatycznie buforowane.</span><span class="sxs-lookup"><span data-stu-id="7b757-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="7b757-113">Jednak LINQ do jednostek kwerend, `Enumerable.Contains` które stosują operatora do kolekcji w pamięci nie są automatycznie buforowane.</span><span class="sxs-lookup"><span data-stu-id="7b757-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="7b757-114">Również parametryzowanie kolekcji w pamięci w skompilowanych kwerend LINQ jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="7b757-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a><span data-ttu-id="7b757-115">Zamówienie utraconych informacji</span><span class="sxs-lookup"><span data-stu-id="7b757-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="7b757-116">Rzutowanie kolumn na typ anonimowy spowoduje utratę informacji o zamawianiu w niektórych kwerendach wykonywanych w bazie danych programu SQL Server 2005 ustawionej na poziomie zgodności "80".</span><span class="sxs-lookup"><span data-stu-id="7b757-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="7b757-117">Dzieje się tak, gdy nazwa kolumny na liście kolejność według pasuje do nazwy kolumny w selektorze, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7b757-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="7b757-118">Niepodpisane liczby całkowite nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="7b757-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="7b757-119">Określanie niepodpisanego typu całkowitej w kwerendzie LINQ do jednostek nie jest obsługiwane, ponieważ entity framework nie obsługuje niepodpisanych liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7b757-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the Entity Framework does not support unsigned integers.</span></span> <span data-ttu-id="7b757-120">Jeśli określisz niepodpisaną liczę <xref:System.ArgumentException> całkowitą, podczas tłumaczenia wyrażenia kwerendy zostanie zgłoszony wyjątek, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7b757-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="7b757-121">W tym przykładzie kwerendy dla zamówienia o identyfikatorze 48000.</span><span class="sxs-lookup"><span data-stu-id="7b757-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a><span data-ttu-id="7b757-122">Błędy konwersji typu</span><span class="sxs-lookup"><span data-stu-id="7b757-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="7b757-123">W języku Visual Basic, gdy właściwość jest mapowana na kolumnę typu `CByte` bitowego <xref:System.Data.SqlClient.SqlException> programu SQL Server o wartości 1 przy użyciu funkcji, a jest generowany z komunikatem "Błąd przepełnienia arytmetycznego".</span><span class="sxs-lookup"><span data-stu-id="7b757-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="7b757-124">Poniższy przykład kwerendy `Product.MakeFlag` kolumny w adventureworks przykładowej bazy danych i wyjątek jest generowany, gdy wyniki kwerendy są iterowane ponad.</span><span class="sxs-lookup"><span data-stu-id="7b757-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="7b757-125">Odwoływanie się do zmiennych nieskawaralnych, które nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="7b757-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="7b757-126">Odwoływanie się do zmiennych nieskawaralnych, takich jak jednostka, w kwerendzie nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7b757-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="7b757-127">Podczas wykonywania takiej kwerendy <xref:System.NotSupportedException> wyjątek jest zgłaszany z komunikatem "Nie `EntityType`można utworzyć stałej wartości typu.</span><span class="sxs-lookup"><span data-stu-id="7b757-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="7b757-128">Tylko typy pierwotne ("takie jak Int32, String i Guid") są obsługiwane w tym kontekście."</span><span class="sxs-lookup"><span data-stu-id="7b757-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b757-129">Odwołanie się do kolekcji zmiennych skalarnych jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7b757-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="7b757-130">Zagnieżdżone kwerendy mogą zakończyć się niepowodzeniem w programie SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="7b757-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="7b757-131">Z PROGRAMU SQL Server 2000, LINQ do jednostek kwerendy mogą zakończyć się niepowodzeniem, jeśli produkują zagnieżdżone zapytania Transact-SQL, które są trzy lub więcej poziomów głębokości.</span><span class="sxs-lookup"><span data-stu-id="7b757-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="7b757-132">Rzutowanie typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="7b757-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="7b757-133">Jeśli zdefiniowano ścieżkę zapytania początkowego, <xref:System.Data.Objects.ObjectQuery%601.Include%2A> aby uwzględnić powiązane obiekty przy użyciu metody <xref:System.Data.Objects.ObjectQuery%601> na, a następnie użyć LINQ do projektu zwracanych obiektów do typu anonimowego, obiekty określone w metody include nie są uwzględniane w wynikach kwerendy.</span><span class="sxs-lookup"><span data-stu-id="7b757-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="7b757-134">Aby uzyskać powiązane obiekty, nie projektuj zwrócone typy do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="7b757-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="7b757-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b757-135">See also</span></span>

- [<span data-ttu-id="7b757-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7b757-136">LINQ to Entities</span></span>](linq-to-entities.md)
