---
title: Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 3945d4fc92bea2c4212da0507618203603ae8aba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191331"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="e4a04-102">Znane problemy i zagadnienia dotyczące składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e4a04-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="e4a04-103">Ta sekcja zawiera informacje o znanych problemach z [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="e4a04-103">This section provides information about known issues with [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
-   [<span data-ttu-id="e4a04-104">Nie można buforować LINQ zapytań</span><span class="sxs-lookup"><span data-stu-id="e4a04-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
-   [<span data-ttu-id="e4a04-105">Kolejność utraty informacji</span><span class="sxs-lookup"><span data-stu-id="e4a04-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
-   [<span data-ttu-id="e4a04-106">Liczb całkowitych bez znaku, nie jest obsługiwane</span><span class="sxs-lookup"><span data-stu-id="e4a04-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
-   [<span data-ttu-id="e4a04-107">Błędy konwersji typu</span><span class="sxs-lookup"><span data-stu-id="e4a04-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
-   [<span data-ttu-id="e4a04-108">Odwoływanie się do zmiennych nieskalarnego nieobsługiwane</span><span class="sxs-lookup"><span data-stu-id="e4a04-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
-   [<span data-ttu-id="e4a04-109">Zapytania zagnieżdżone może zakończyć się niepowodzeniem z programem SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="e4a04-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
-   [<span data-ttu-id="e4a04-110">Wyświetlanie na typ anonimowy</span><span class="sxs-lookup"><span data-stu-id="e4a04-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="e4a04-111">Nie można buforować LINQ zapytań</span><span class="sxs-lookup"><span data-stu-id="e4a04-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="e4a04-112">Począwszy od programu .NET Framework 4.5, programu LINQ do jednostek zapytań są automatycznie buforowane.</span><span class="sxs-lookup"><span data-stu-id="e4a04-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="e4a04-113">Jednak LINQ do zapytań jednostki, stosowane `Enumerable.Contains` operator z kolekcjami w pamięci nie są automatycznie buforowane.</span><span class="sxs-lookup"><span data-stu-id="e4a04-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="e4a04-114">Również parametryzacja kolekcji w skompilowanych zapytań LINQ w pamięci nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="e4a04-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="e4a04-115">Kolejność utraty informacji</span><span class="sxs-lookup"><span data-stu-id="e4a04-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="e4a04-116">Projekcji kolumn do typu anonimowego spowoduje, że szeregowania informacje, aby spowodować utratę niektórych kwerend, które są wykonywane względem [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] bazy danych, Ustaw poziom zgodności, "80".</span><span class="sxs-lookup"><span data-stu-id="e4a04-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] database set to a compatibility level of "80".</span></span>  <span data-ttu-id="e4a04-117">Operacja wykonywana, gdy nazwa kolumny, na liście klauzuli order by pasuje do nazwy kolumny w selektorze, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e4a04-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="e4a04-118">Liczb całkowitych bez znaku, nie jest obsługiwane</span><span class="sxs-lookup"><span data-stu-id="e4a04-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="e4a04-119">Określanie typu Liczba całkowita bez znaku w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania nie jest obsługiwana, ponieważ [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nie obsługuje liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="e4a04-119">Specifying an unsigned integer type in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="e4a04-120">Jeśli określisz liczbę całkowitą bez znaku, <xref:System.ArgumentException> zostanie zgłoszony wyjątek podczas translacji wyrażenie zapytania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e4a04-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="e4a04-121">To przykładowe zapytania dla zamówienia o identyfikatorze 48000.</span><span class="sxs-lookup"><span data-stu-id="e4a04-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="e4a04-122">Błędy konwersji typu</span><span class="sxs-lookup"><span data-stu-id="e4a04-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="e4a04-123">W języku Visual Basic, gdy właściwość jest mapowana na kolumnę typu bit programu SQL Server o wartości 1 przy użyciu `CByte` funkcji <xref:System.Data.SqlClient.SqlException> jest zgłaszany z komunikatem "Błąd przepełnienia arytmetycznego".</span><span class="sxs-lookup"><span data-stu-id="e4a04-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="e4a04-124">Następujące przykładowe kwerendy `Product.MakeFlag` kolumny w przykładowej bazy danych AdventureWorks i wyjątek jest zgłaszany, gdy wyniki zapytania jest powtarzana.</span><span class="sxs-lookup"><span data-stu-id="e4a04-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="e4a04-125">Odwoływanie się do zmiennych nieskalarnego nieobsługiwane</span><span class="sxs-lookup"><span data-stu-id="e4a04-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="e4a04-126">Odwoływanie się do zmiennych nieskalarnego, takich jak jednostki, w zapytaniu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e4a04-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="e4a04-127">Gdy jest wykonywana w przypadku takiego zapytania, <xref:System.NotSupportedException> wyjątek z informacją, że komunikat "nie można utworzyć stałej wartości typu `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="e4a04-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="e4a04-128">Tylko typy pierwotne ("takie jak Int32, String i Guid") są obsługiwane w tym kontekście."</span><span class="sxs-lookup"><span data-stu-id="e4a04-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4a04-129">Odwoływanie się do kolekcji zmienne skalarne są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e4a04-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="e4a04-130">Zapytania zagnieżdżone może zakończyć się niepowodzeniem z programem SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="e4a04-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="e4a04-131">Za pomocą programu SQL Server 2000 jednostek zapytaniach składnika LINQ to może się niepowodzeniem, jeśli produkują zagnieżdżonych zapytań języka Transact-SQL, które są co najmniej trzech poziomów w głąb.</span><span class="sxs-lookup"><span data-stu-id="e4a04-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="e4a04-132">Wyświetlanie na typ anonimowy</span><span class="sxs-lookup"><span data-stu-id="e4a04-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="e4a04-133">Jeśli zdefiniujesz swoją ścieżkę początkowego zapytania, aby dołączyć powiązane obiekty za pomocą <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metody <xref:System.Data.Objects.ObjectQuery%601> i następnie za pomocą LINQ projektu zwracanych obiektów do typu anonimowego, obiekty w metodzie dołączania nie są uwzględnione w zapytaniu wyniki.</span><span class="sxs-lookup"><span data-stu-id="e4a04-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="e4a04-134">Aby uzyskać powiązane obiekty, nie zwracane typy projektów do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="e4a04-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="e4a04-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4a04-135">See also</span></span>

- [<span data-ttu-id="e4a04-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e4a04-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
