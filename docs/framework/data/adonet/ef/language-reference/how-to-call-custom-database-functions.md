---
title: "Porady: wywoływać funkcje w niestandardowej bazie danych"
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
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3d3f2e0235c5e141673d0b3f51c85e5e51e86694
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="54abe-102">Porady: wywoływać funkcje w niestandardowej bazie danych</span><span class="sxs-lookup"><span data-stu-id="54abe-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="54abe-103">W tym temacie opisano sposób wywołania funkcji niestandardowych, które są zdefiniowane w bazie danych od w składniku LINQ do jednostek zapytań.</span><span class="sxs-lookup"><span data-stu-id="54abe-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="54abe-104">Funkcje bazy danych, które są wywoływane ze składnika LINQ do jednostek zapytań są wykonywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="54abe-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="54abe-105">Wykonywanie funkcji w bazie danych może poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="54abe-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="54abe-106">Poniższa procedura zawiera WYSOKOPOZIOMOWY zarys wywoływania funkcji w niestandardowej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="54abe-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="54abe-107">Przykład, w którym następuje zawiera więcej szczegółów na temat czynności opisane w procedurze.</span><span class="sxs-lookup"><span data-stu-id="54abe-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="54abe-108">Wywoływanie funkcji niestandardowych, które są zdefiniowane w bazie danych</span><span class="sxs-lookup"><span data-stu-id="54abe-108">To call custom functions that are defined in the database</span></span>  
  
1.  <span data-ttu-id="54abe-109">Tworzenie funkcji niestandardowej w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="54abe-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="54abe-110">Aby uzyskać więcej informacji na temat tworzenia niestandardowych funkcji w programie SQL Server, zobacz [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="54abe-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2.  <span data-ttu-id="54abe-111">Deklarowanie funkcji w magazynie języka definicji schematu (SSDL) pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="54abe-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="54abe-112">Nazwa funkcji musi być taka sama jak nazwa funkcji zadeklarowany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="54abe-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="54abe-113">Aby uzyskać więcej informacji, zobacz [funkcja elementu (SSDL)](http://msdn.microsoft.com/en-us/b60cfc3d-8b93-423e-8c99-b867256640a4).</span><span class="sxs-lookup"><span data-stu-id="54abe-113">For more information, see [Function Element (SSDL)](http://msdn.microsoft.com/en-us/b60cfc3d-8b93-423e-8c99-b867256640a4).</span></span>  
  
3.  <span data-ttu-id="54abe-114">Dodać odpowiedniej metody do klasy w kodzie aplikacji i zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atrybutu jest nazwa przestrzeni nazw modelu koncepcyjnego i nazwa funkcji koncepcyjnego odpowiednio modelu.</span><span class="sxs-lookup"><span data-stu-id="54abe-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="54abe-115">Funkcja rozpoznawania nazw dla LINQ jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="54abe-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4.  <span data-ttu-id="54abe-116">Wywołaj metodę w zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="54abe-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54abe-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="54abe-117">Example</span></span>  
 <span data-ttu-id="54abe-118">W poniższym przykładzie pokazano, jak wywołać funkcję w niestandardowej bazie danych od w LINQ do jednostek zapytania.</span><span class="sxs-lookup"><span data-stu-id="54abe-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="54abe-119">W przykładzie użyto modelu służbowe.</span><span class="sxs-lookup"><span data-stu-id="54abe-119">The example uses the School model.</span></span> <span data-ttu-id="54abe-120">Informacje o modelu służbowe, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) i [generowania edmx służbowe pliku](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="54abe-120">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="54abe-121">Poniższy kod dodaje `AvgStudentGrade` funkcji do przykładowej bazy danych służbowych.</span><span class="sxs-lookup"><span data-stu-id="54abe-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54abe-122">Kroki do wywoływania funkcji w niestandardowej bazie danych są takie same, niezależnie od serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="54abe-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="54abe-123">Poniższy kod jest jednak specyficzne dla tworzenia funkcji w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="54abe-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="54abe-124">Kod Tworzenie funkcji niestandardowej w innych serwerów baz danych może się różnić.</span><span class="sxs-lookup"><span data-stu-id="54abe-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="54abe-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="54abe-125">Example</span></span>  
 <span data-ttu-id="54abe-126">Następnie zadeklarowania funkcji w magazynie języka definicji schematu (SSDL) pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="54abe-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="54abe-127">Poniższy kod deklaruje `AvgStudentGrade` funkcji w pliku SSDL:</span><span class="sxs-lookup"><span data-stu-id="54abe-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="54abe-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="54abe-128">Example</span></span>  
 <span data-ttu-id="54abe-129">Teraz utworzyć metodę i mapowanie go funkcja zadeklarowany w pliku SSDL.</span><span class="sxs-lookup"><span data-stu-id="54abe-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="54abe-130">W klasie następujące metody jest zamapowany na funkcję zdefiniowaną w pliku SSDL (powyżej) przy użyciu <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="54abe-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="54abe-131">Gdy ta metoda jest wywoływana, odpowiednich funkcji w bazie danych jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="54abe-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="54abe-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="54abe-132">Example</span></span>  
 <span data-ttu-id="54abe-133">Na koniec należy wywołać metodę w zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="54abe-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="54abe-134">Poniższy kod wyświetla nazwisk studentów i średnie klas do konsoli:</span><span class="sxs-lookup"><span data-stu-id="54abe-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="54abe-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54abe-135">See Also</span></span>  
 [<span data-ttu-id="54abe-136">Omówienie plików edmx</span><span class="sxs-lookup"><span data-stu-id="54abe-136">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="54abe-137">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="54abe-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
