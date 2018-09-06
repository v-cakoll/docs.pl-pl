---
title: 'Porady: wywoływanie niestandardowych funkcji bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 4e7c94dce5b50fe93f00aaaa72206be3394faf62
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042286"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="afe13-102">Porady: wywoływanie niestandardowych funkcji bazy danych</span><span class="sxs-lookup"><span data-stu-id="afe13-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="afe13-103">W tym temacie opisano sposób wywołania funkcji niestandardowych, które są zdefiniowane w bazie danych z w ramach programu LINQ do zapytań jednostki.</span><span class="sxs-lookup"><span data-stu-id="afe13-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="afe13-104">Funkcje bazy danych, które są wywoływane z LINQ do zapytań jednostki są wykonywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="afe13-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="afe13-105">Wykonywanie funkcji w bazie danych może zwiększyć wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="afe13-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="afe13-106">Poniższa procedura zawiera WYSOKOPOZIOMOWY zarys wywoływania funkcji niestandardowej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="afe13-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="afe13-107">W poniższym przykładzie zapewnia więcej szczegółów na temat czynności opisane w procedurze.</span><span class="sxs-lookup"><span data-stu-id="afe13-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="afe13-108">Aby wywołać funkcje niestandardowe, które są zdefiniowane w bazie danych</span><span class="sxs-lookup"><span data-stu-id="afe13-108">To call custom functions that are defined in the database</span></span>  
  
1.  <span data-ttu-id="afe13-109">Tworzenie funkcji niestandardowej w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="afe13-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="afe13-110">Aby uzyskać więcej informacji na temat tworzenia funkcji niestandardowych w programie SQL Server, zobacz [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="afe13-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2.  <span data-ttu-id="afe13-111">Deklarowanie funkcji w język definicji schematu magazynu (SSDL) pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="afe13-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="afe13-112">Nazwa funkcji musi być taka sama jak nazwa funkcji zadeklarowanych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="afe13-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="afe13-113">Aby uzyskać więcej informacji, zobacz [elementu — funkcja (SSDL)](https://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).</span><span class="sxs-lookup"><span data-stu-id="afe13-113">For more information, see [Function Element (SSDL)](https://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).</span></span>  
  
3.  <span data-ttu-id="afe13-114">Dodaj odpowiadającą im metodę do klasy w kodzie aplikacji i zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metody należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atrybutu jest nazwa przestrzeni nazw modelu koncepcyjnego i nazwą funkcji w treści koncepcyjnej model, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="afe13-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="afe13-115">Funkcja rozpoznawania nazw dla programu LINQ jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="afe13-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4.  <span data-ttu-id="afe13-116">Wywołaj metodę w zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="afe13-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afe13-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="afe13-117">Example</span></span>  
 <span data-ttu-id="afe13-118">Poniższy przykład pokazuje, jak wywołać funkcję niestandardową bazę danych z w LINQ do kwerendy jednostek.</span><span class="sxs-lookup"><span data-stu-id="afe13-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="afe13-119">W przykładzie użyto modelu szkoły.</span><span class="sxs-lookup"><span data-stu-id="afe13-119">The example uses the School model.</span></span> <span data-ttu-id="afe13-120">Aby uzyskać informacje na temat modelu szkoły, zobacz [tworzenie przykładowej bazy danych School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) i [generowania edmx School pliku](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="afe13-120">For information about the School model, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="afe13-121">Poniższy kod dodaje `AvgStudentGrade` funkcji przykładowej bazy danych School.</span><span class="sxs-lookup"><span data-stu-id="afe13-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afe13-122">Kroki do wywoływania funkcji niestandardowej bazy danych są takie same, niezależnie od serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="afe13-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="afe13-123">Jednak kod poniżej dotyczy tworzenia funkcji w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="afe13-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="afe13-124">Kod dla tworzenia niestandardowych funkcji na inne serwery baz danych mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="afe13-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="afe13-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="afe13-125">Example</span></span>  
 <span data-ttu-id="afe13-126">Następnie można zadeklarować funkcji w język definicji schematu magazynu (SSDL) pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="afe13-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="afe13-127">Poniższy kod deklaruje `AvgStudentGrade` funkcji w SSDL:</span><span class="sxs-lookup"><span data-stu-id="afe13-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="afe13-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="afe13-128">Example</span></span>  
 <span data-ttu-id="afe13-129">Teraz Utwórz metodę i mapowany do funkcji zadeklarowanych w SSDL.</span><span class="sxs-lookup"><span data-stu-id="afe13-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="afe13-130">Metoda następujące klasy jest mapowany na funkcję zdefiniowaną w SSDL (powyżej) przy użyciu <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="afe13-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="afe13-131">Gdy ta metoda jest wywoływana, odpowiednich funkcji w bazie danych jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="afe13-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="afe13-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="afe13-132">Example</span></span>  
 <span data-ttu-id="afe13-133">Na koniec Wywołaj metodę w zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="afe13-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="afe13-134">Poniższy kod Wyświetla nazwiska uczniów i średni klas do konsoli:</span><span class="sxs-lookup"><span data-stu-id="afe13-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="afe13-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afe13-135">See Also</span></span>  
 [<span data-ttu-id="afe13-136">Omówienie pliku edmx</span><span class="sxs-lookup"><span data-stu-id="afe13-136">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="afe13-137">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="afe13-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
