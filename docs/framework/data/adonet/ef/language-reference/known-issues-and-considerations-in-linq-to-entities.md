---
title: "Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 85fea34f6044c99a58fd27dbf5a03198741294ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="5e668-102">Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5e668-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="5e668-103">Ta sekcja zawiera informacje o znanych problemach z [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="5e668-103">This section provides information about known issues with [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
-   [<span data-ttu-id="5e668-104">Nie można buforować LINQ kwerend czy</span><span class="sxs-lookup"><span data-stu-id="5e668-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
-   [<span data-ttu-id="5e668-105">Porządkowanie utraty informacji</span><span class="sxs-lookup"><span data-stu-id="5e668-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
-   [<span data-ttu-id="5e668-106">Liczb całkowitych bez znaku, które nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="5e668-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
-   [<span data-ttu-id="5e668-107">Błędy konwersji typu</span><span class="sxs-lookup"><span data-stu-id="5e668-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
-   [<span data-ttu-id="5e668-108">Tworzenie odwołań nie są obsługiwane zmienne nieskalarnego</span><span class="sxs-lookup"><span data-stu-id="5e668-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
-   [<span data-ttu-id="5e668-109">Zapytania zagnieżdżone może zakończyć się niepowodzeniem z programem SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="5e668-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
-   [<span data-ttu-id="5e668-110">Projekcji do typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="5e668-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="5e668-111">Nie można buforować LINQ kwerend czy</span><span class="sxs-lookup"><span data-stu-id="5e668-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="5e668-112">Począwszy od programu .NET Framework 4.5, składnika LINQ to Entities zapytania są automatycznie buforowane.</span><span class="sxs-lookup"><span data-stu-id="5e668-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="5e668-113">Jednak LINQ do jednostek zapytań, które są stosowane `Enumerable.Contains` operator do kolekcji w pamięci nie są automatycznie buforowane.</span><span class="sxs-lookup"><span data-stu-id="5e668-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="5e668-114">Parametryzacja również kolekcji w pamięci w skompilowanych zapytań LINQ jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="5e668-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="5e668-115">Porządkowanie utraty informacji</span><span class="sxs-lookup"><span data-stu-id="5e668-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="5e668-116">Projekcji kolumny typu anonimowego spowoduje, że porządkowania informacje, aby spowodować utratę niektórych kwerend, które są wykonywane przed [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] bazy danych Ustaw poziom zgodności "80".</span><span class="sxs-lookup"><span data-stu-id="5e668-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] database set to a compatibility level of "80".</span></span>  <span data-ttu-id="5e668-117">Występuje, gdy nazwa kolumny w liście order by odpowiada nazwie kolumny w selektorze, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5e668-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="5e668-118">Liczb całkowitych bez znaku, które nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="5e668-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="5e668-119">Określanie typu Liczba całkowita bez znaku w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania nie jest obsługiwana, ponieważ [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nie obsługuje liczb całkowitych bez znaku.</span><span class="sxs-lookup"><span data-stu-id="5e668-119">Specifying an unsigned integer type in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="5e668-120">Jeśli określisz całkowitą bez znaku <xref:System.ArgumentException> zostanie wygenerowany wyjątek podczas tłumaczenia wyrażenia zapytania, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5e668-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="5e668-121">To przykładowe zapytania o identyfikatorze 48000 zamówienia.</span><span class="sxs-lookup"><span data-stu-id="5e668-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="5e668-122">Błędy konwersji typu</span><span class="sxs-lookup"><span data-stu-id="5e668-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="5e668-123">W języku Visual Basic, gdy właściwość jest zamapowana na kolumnę typu bit programu SQL Server o wartości 1 przy użyciu `CByte` funkcji <xref:System.Data.SqlClient.SqlException> jest zgłaszany z komunikatem "Błąd przepełnienia arytmetycznego".</span><span class="sxs-lookup"><span data-stu-id="5e668-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="5e668-124">Następujące przykładowe zapytania `Product.MakeFlag` kolumny przykładową bazę danych AdventureWorks i wyjątek jest generowany, gdy wyniki zapytania są iterowane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="5e668-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="5e668-125">Tworzenie odwołań nie są obsługiwane zmienne nieskalarnego</span><span class="sxs-lookup"><span data-stu-id="5e668-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="5e668-126">Odwołanie do zmiennych nieskalarnego, takich jak jednostki w zapytaniu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5e668-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="5e668-127">Podczas takiej kwerendy, <xref:System.NotSupportedException> wyjątku z komunikat "nie można utworzyć wartości stałej typu `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="5e668-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="5e668-128">Tylko typy pierwotne ("takie jak Int32, typ String i identyfikator Guid") są obsługiwane w tym kontekście."</span><span class="sxs-lookup"><span data-stu-id="5e668-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e668-129">Odwołanie do kolekcji zmienne skalara jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="5e668-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="5e668-130">Zapytania zagnieżdżone może zakończyć się niepowodzeniem z programem SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="5e668-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="5e668-131">Programu SQL Server 2000 Jeśli wygenerowanie zagnieżdżonych zapytań języka Transact-SQL, które są co najmniej trzech poziomów w głąb może nie powieść składnika LINQ to Entities zapytania.</span><span class="sxs-lookup"><span data-stu-id="5e668-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="5e668-132">Projekcji do typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="5e668-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="5e668-133">Jeśli zdefiniujesz ścieżki początkowego zapytania zawierają obiekty powiązane przy użyciu <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metoda <xref:System.Data.Objects.ObjectQuery%601> , a następnie za pomocą LINQ projektu zwracanych obiektów do typu anonimowego, obiektów w metodzie include nie są uwzględnione w zapytaniu wyniki.</span><span class="sxs-lookup"><span data-stu-id="5e668-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="5e668-134">Aby uzyskać powiązanych obiektów, nie projektu zwracanych typów do typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="5e668-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="5e668-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e668-135">See Also</span></span>  
 [<span data-ttu-id="5e668-136">LINQ do jednostek</span><span class="sxs-lookup"><span data-stu-id="5e668-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
