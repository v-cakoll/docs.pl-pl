---
title: Typy danych podstawowych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e88767bd478b4b59e8c395473cfd8a36aaf68f3b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="basic-data-types"></a><span data-ttu-id="28507-102">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="28507-102">Basic Data Types</span></span>
<span data-ttu-id="28507-103">Ponieważ LINQ do SQL zapytań przełożyć na języka Transact-SQL przed są wykonywane w programie Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="28507-103">Because LINQ to SQL queries translate to Transact-SQL before they are executed on the Microsoft SQL Server.</span></span> <span data-ttu-id="28507-104">LINQ do SQL obsługuje wiele wbudowanych funkcji nieistniejącego dla typów podstawowych danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="28507-104">LINQ to SQL supports much of the same built-in functionality that SQL Server does for basic data types.</span></span>  
  
## <a name="casting"></a><span data-ttu-id="28507-105">Rzutowanie</span><span class="sxs-lookup"><span data-stu-id="28507-105">Casting</span></span>  
 <span data-ttu-id="28507-106">Rzutowania jawnych ani niejawnych są włączone ze źródła typu CLR do docelowego typu CLR w przypadku podobne prawidłowa konwersja w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="28507-106">Implicit or explicit casts are enabled from a source CLR type to a target CLR type if there is a similar valid conversion within SQL Server.</span></span> <span data-ttu-id="28507-107">Aby uzyskać więcej informacji na temat rzutowanie CLR, zobacz [CType — funkcja](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) i [jako](~/docs/csharp/language-reference/keywords/as.md).</span><span class="sxs-lookup"><span data-stu-id="28507-107">For more information about CLR casting, see [CType Function](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) and [as](~/docs/csharp/language-reference/keywords/as.md).</span></span> <span data-ttu-id="28507-108">Po przeprowadzeniu konwersji rzutowania zmianę zachowania operacji wykonywanych na wyrażeniu CLR, aby dopasować zachowanie inne wyrażenia CLR, które naturalnie zamapować na typ docelowy.</span><span class="sxs-lookup"><span data-stu-id="28507-108">After conversion, casts change the behavior of operations performed on a CLR expression to match the behavior of other CLR expressions that naturally map to the destination type.</span></span> <span data-ttu-id="28507-109">Rzutowania są również możliwa w kontekście mapowania dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="28507-109">Casts are also translatable in the context of inheritance mapping.</span></span> <span data-ttu-id="28507-110">Obiekty mogą być rzutowane na bardziej szczegółowe podtypów jednostki tak, aby ich dane specyficzne dla podtypu są dostępne.</span><span class="sxs-lookup"><span data-stu-id="28507-110">Objects can be cast to more specific entity subtypes so that their subtype-specific data can be accessed.</span></span>  
  
## <a name="equality-operators"></a><span data-ttu-id="28507-111">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="28507-111">Equality Operators</span></span>  
 <span data-ttu-id="28507-112">LINQ do SQL obsługuje następujące operatory równości w typach podstawowych danych wewnątrz LINQ kwerendy SQL:</span><span class="sxs-lookup"><span data-stu-id="28507-112">LINQ to SQL supports the following equality operators on basic data types inside LINQ to SQL queries:</span></span>  
  
-   <span data-ttu-id="28507-113">Taki sam i Operator nierówności: operatory równości i nierówności są obsługiwane w przypadku liczbowe <xref:System.Boolean>, <xref:System.DateTime>, i <xref:System.TimeSpan> typów.</span><span class="sxs-lookup"><span data-stu-id="28507-113">Equal and Inequality Operator: Equality and inequality operators are supported for numeric <xref:System.Boolean>, <xref:System.DateTime>, and <xref:System.TimeSpan> types.</span></span> <span data-ttu-id="28507-114">Aby uzyskać więcej informacji na temat operatorów Visual Basic `=` i `<>`, zobacz [operatory porównania](~/docs/visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="28507-114">For more about Visual Basic operators `=` and `<>`, see [Comparison Operators](~/docs/visual-basic/language-reference/operators/comparison-operators.md).</span></span> <span data-ttu-id="28507-115">Aby uzyskać więcej informacji na temat operatory porównania języka C# `==` i `!=`, zobacz [== — Operator](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) i [! = — Operator](~/docs/csharp/language-reference/operators/not-equal-operator.md)odpowiednio</span><span class="sxs-lookup"><span data-stu-id="28507-115">For more information about C# comparison operators `==` and `!=`, see [== Operator](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) and [!= Operator](~/docs/csharp/language-reference/operators/not-equal-operator.md), respectively</span></span>  
  
-   <span data-ttu-id="28507-116">Is — operator: `IS` operator ma tłumaczenia obsługiwanych w przypadku mapowania dziedziczenia jest używany.</span><span class="sxs-lookup"><span data-stu-id="28507-116">Is operator: The `IS` operator has a supported translation when inheritance mapping is being used.</span></span> <span data-ttu-id="28507-117">Może służyć zamiast bezpośrednio testowania dyskryminatora, aby określić, czy obiekt jest określonego typu i jest translacja do wyboru w kolumnie rozróżniacza.</span><span class="sxs-lookup"><span data-stu-id="28507-117">It can be used instead of directly testing the discriminator column to determine whether an object is of a specific entity type, and is translated to a check on the discriminator column.</span></span> <span data-ttu-id="28507-118">Aby uzyskać więcej informacji na temat operatorów Visual Basic i C# jest zobacz [operatora Is](~/docs/visual-basic/language-reference/operators/is-operator.md) i [jest](~/docs/csharp/language-reference/keywords/is.md).</span><span class="sxs-lookup"><span data-stu-id="28507-118">For more information about the Visual Basic and C# Is operators, see [Is Operator](~/docs/visual-basic/language-reference/operators/is-operator.md) and [is](~/docs/csharp/language-reference/keywords/is.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28507-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28507-119">See Also</span></span>  
 [<span data-ttu-id="28507-120">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="28507-120">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="28507-121">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="28507-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
