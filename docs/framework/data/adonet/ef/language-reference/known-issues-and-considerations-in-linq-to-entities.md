---
title: Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 7be3491af48ad29cd7892dd31a077aa7ac44ca63
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250497"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="1624f-102">Znane problemy i zagadnienia dotyczące składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1624f-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="1624f-103">Ta sekcja zawiera informacje o znanych problemach dotyczących LINQ to Entities zapytań.</span><span class="sxs-lookup"><span data-stu-id="1624f-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="1624f-104">Zapytania LINQ, które nie mogą być buforowane</span><span class="sxs-lookup"><span data-stu-id="1624f-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="1624f-105">Utracone informacje o uporządkowaniu</span><span class="sxs-lookup"><span data-stu-id="1624f-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="1624f-106">Liczby całkowite bez znaku są nieobsługiwane</span><span class="sxs-lookup"><span data-stu-id="1624f-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="1624f-107">Błędy konwersji typów</span><span class="sxs-lookup"><span data-stu-id="1624f-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="1624f-108">Odwołania do zmiennych nieskalarnych nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="1624f-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="1624f-109">Zapytania zagnieżdżone mogą zakończyć się niepowodzeniem z SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="1624f-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="1624f-110">Projekcja do typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="1624f-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="1624f-111">Zapytania LINQ, które nie mogą być buforowane</span><span class="sxs-lookup"><span data-stu-id="1624f-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="1624f-112">Począwszy od .NET Framework 4,5, zapytania LINQ to Entities są buforowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="1624f-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="1624f-113">Jednak LINQ to Entities zapytania, które stosują `Enumerable.Contains` operator do kolekcji w pamięci, nie są automatycznie buforowane.</span><span class="sxs-lookup"><span data-stu-id="1624f-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="1624f-114">Parametryzacja również kolekcje w pamięci w skompilowanych zapytaniach LINQ są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="1624f-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="1624f-115">Utracone informacje o uporządkowaniu</span><span class="sxs-lookup"><span data-stu-id="1624f-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="1624f-116">Projekcja kolumn na typ anonimowy spowoduje utratę informacji o uporządkowaniu w niektórych zapytaniach, które są wykonywane w odniesieniu do bazy danych SQL Server 2005 z ustawionym poziomem zgodności równym "80".</span><span class="sxs-lookup"><span data-stu-id="1624f-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="1624f-117">Dzieje się tak, gdy nazwa kolumny w liście order by jest zgodna z nazwą kolumny w selektorze, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1624f-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="1624f-118">Liczby całkowite bez znaku są nieobsługiwane</span><span class="sxs-lookup"><span data-stu-id="1624f-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="1624f-119">Określanie typu liczby całkowitej bez znaku w zapytaniu LINQ to Entities nie jest obsługiwane, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ponieważ nie obsługuje liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="1624f-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="1624f-120">Jeśli określisz liczbę całkowitą bez znaku, <xref:System.ArgumentException> podczas tłumaczenia wyrażenia zapytania zostanie zgłoszony wyjątek, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1624f-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="1624f-121">To przykładowe zapytanie dla zamówienia o IDENTYFIKATORze 48000.</span><span class="sxs-lookup"><span data-stu-id="1624f-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="1624f-122">Błędy konwersji typów</span><span class="sxs-lookup"><span data-stu-id="1624f-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="1624f-123">W Visual Basic, gdy właściwość jest zamapowana do kolumny typu SQL Server bitowego o wartości 1 przy użyciu `CByte` funkcji <xref:System.Data.SqlClient.SqlException> , jest generowany z komunikatem "błąd przepełnienia arytmetycznego".</span><span class="sxs-lookup"><span data-stu-id="1624f-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="1624f-124">Poniższy przykład wysyła zapytanie do `Product.MakeFlag` kolumny w przykładowej bazie danych AdventureWorks, a wyjątek jest zgłaszany, gdy wyniki zapytania są powtarzane.</span><span class="sxs-lookup"><span data-stu-id="1624f-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="1624f-125">Odwołania do zmiennych nieskalarnych nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="1624f-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="1624f-126">Odwoływanie się do zmiennych nieskalarnych, takich jak jednostka, w zapytaniu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1624f-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="1624f-127">Gdy takie zapytanie jest wykonywane, <xref:System.NotSupportedException> zostanie zgłoszony wyjątek z komunikatem informującym o tym, że nie można utworzyć stałej wartości typu. `EntityType`</span><span class="sxs-lookup"><span data-stu-id="1624f-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="1624f-128">W tym kontekście są obsługiwane tylko typy pierwotne (takie jak Int32, String i GUID). "</span><span class="sxs-lookup"><span data-stu-id="1624f-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1624f-129">Obsługiwane jest odwołanie do kolekcji zmiennych skalarnych.</span><span class="sxs-lookup"><span data-stu-id="1624f-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="1624f-130">Zapytania zagnieżdżone mogą zakończyć się niepowodzeniem z SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="1624f-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="1624f-131">W przypadku SQL Server 2000 zapytania LINQ to Entities mogą zakończyć się niepowodzeniem, jeśli generują zagnieżdżone zapytania Transact-SQL, które są trzy lub więcej poziomów głębokości.</span><span class="sxs-lookup"><span data-stu-id="1624f-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="1624f-132">Projekcja do typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="1624f-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="1624f-133">W przypadku zdefiniowania początkowej ścieżki zapytania w celu uwzględnienia pokrewnych <xref:System.Data.Objects.ObjectQuery%601.Include%2A> obiektów przy użyciu <xref:System.Data.Objects.ObjectQuery%601> metody w programie, a następnie użycie LINQ do zaprojektowania zwracanych obiektów do typu anonimowego, obiekty określone w metodzie include nie zostaną uwzględnione w zapytaniu uzyskane.</span><span class="sxs-lookup"><span data-stu-id="1624f-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="1624f-134">Aby uzyskać powiązane obiekty, nie należy projektować zwracanych typów do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="1624f-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="1624f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1624f-135">See also</span></span>

- [<span data-ttu-id="1624f-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1624f-136">LINQ to Entities</span></span>](linq-to-entities.md)
