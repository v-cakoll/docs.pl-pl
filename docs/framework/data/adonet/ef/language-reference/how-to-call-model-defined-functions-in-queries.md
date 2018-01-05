---
title: "Porady: Wywołaj funkcje zdefiniowane przez Model w zapytaniach"
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
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d639297764333b99675cb9e076e816314f3567c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="0c7db-102">Porady: Wywołaj funkcje zdefiniowane przez Model w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="0c7db-102">How to: Call Model-Defined Functions in Queries</span></span>
<span data-ttu-id="0c7db-103">W tym temacie opisano sposób wywołania funkcji, które są zdefiniowane w modelu koncepcyjnym z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="0c7db-103">This topic describes how to call functions that are defined in the conceptual model from within [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="0c7db-104">Poniższa procedura zawiera WYSOKOPOZIOMOWY zarys wywoływania funkcję zdefiniowaną w modelu z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="0c7db-104">The procedure below provides a high-level outline for calling a model-defined function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="0c7db-105">Przykład, w którym następuje zawiera więcej szczegółów na temat czynności opisane w procedurze.</span><span class="sxs-lookup"><span data-stu-id="0c7db-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="0c7db-106">W procedurze założono, że funkcja ma zdefiniowany w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="0c7db-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="0c7db-107">Aby uzyskać więcej informacji, zobacz [porady: Definiowanie funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span><span class="sxs-lookup"><span data-stu-id="0c7db-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="0c7db-108">Wywoływanie funkcji zdefiniowanej w modelu koncepcyjnym</span><span class="sxs-lookup"><span data-stu-id="0c7db-108">To call a function defined in the conceptual model</span></span>  
  
1.  <span data-ttu-id="0c7db-109">Dodaj powszechnie używaną metodą języka wspólnego (CLR) do aplikacji, który jest mapowany na funkcję zdefiniowaną w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="0c7db-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="0c7db-110">Aby mapować metody, należy zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody.</span><span class="sxs-lookup"><span data-stu-id="0c7db-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="0c7db-111">Należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> atrybutu są odpowiednio nazwę przestrzeni nazw modelu koncepcyjnego i nazwa funkcji w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="0c7db-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="0c7db-112">Funkcja rozpoznawania nazw dla LINQ jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="0c7db-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2.  <span data-ttu-id="0c7db-113">Wywołanie funkcji [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="0c7db-113">Call the function in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c7db-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c7db-114">Example</span></span>  
 <span data-ttu-id="0c7db-115">W poniższym przykładzie pokazano sposób wywołania funkcji, która jest zdefiniowana w modelu koncepcyjnym z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="0c7db-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="0c7db-116">W przykładzie użyto modelu służbowe.</span><span class="sxs-lookup"><span data-stu-id="0c7db-116">The example uses the School model.</span></span> <span data-ttu-id="0c7db-117">Informacje o modelu służbowe, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) i [generowania edmx służbowe pliku](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="0c7db-117">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="0c7db-118">Następująca funkcja modelu koncepcyjnego zwraca liczbę lat, ponieważ został dzierżawione instruktora.</span><span class="sxs-lookup"><span data-stu-id="0c7db-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="0c7db-119">Aby uzyskać informacje na temat dodawania funkcji do modelu koncepcyjnego, zobacz [porady: Definiowanie funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span><span class="sxs-lookup"><span data-stu-id="0c7db-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="0c7db-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c7db-120">Example</span></span>  
 <span data-ttu-id="0c7db-121">Następnie dodaj następującą metodę do aplikacji i użyj <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do mapowany na funkcję modelu koncepcyjnego:</span><span class="sxs-lookup"><span data-stu-id="0c7db-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="0c7db-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c7db-122">Example</span></span>  
 <span data-ttu-id="0c7db-123">Teraz można wywołać funkcję modelu koncepcyjnego z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="0c7db-123">Now you can call the conceptual model function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="0c7db-124">Poniższy kod wywołuje metodę w celu wyświetlenia wszystkich instruktorów, którzy zostali zatrudnieni ponad 10 lat temu:</span><span class="sxs-lookup"><span data-stu-id="0c7db-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="0c7db-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c7db-125">See Also</span></span>  
 [<span data-ttu-id="0c7db-126">Omówienie plików edmx</span><span class="sxs-lookup"><span data-stu-id="0c7db-126">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="0c7db-127">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0c7db-127">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="0c7db-128">Wywoływanie funkcji w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0c7db-128">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="0c7db-129">Instrukcje: Wywoływanie funkcji definiowanych przez model jako metod obiektu</span><span class="sxs-lookup"><span data-stu-id="0c7db-129">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
