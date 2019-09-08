---
title: Procedury składowane
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 80ea105eef33ebb2a0e52d91a631258400ea3dff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792480"
---
# <a name="stored-procedures"></a><span data-ttu-id="5c2cf-102">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="5c2cf-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5c2cf-103">używa metod w modelu obiektu do reprezentowania procedur składowanych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-103">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="5c2cf-104">Należy wyznaczyć metody jako procedury składowane <xref:System.Data.Linq.Mapping.FunctionAttribute> , stosując atrybut i, w razie <xref:System.Data.Linq.Mapping.ParameterAttribute> potrzeby, atrybut.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="5c2cf-105">Aby uzyskać więcej informacji, zobacz [model obiektów LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="5c2cf-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="5c2cf-106">Deweloperzy korzystający z programu Visual Studio zwykle używają Object Relational Designer, aby mapować procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-106">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="5c2cf-107">W tematach w tej sekcji pokazano, jak tworzyć i wywoływać te metody w aplikacji, jeśli piszesz kod samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c2cf-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5c2cf-108">In This Section</span></span>  
 [<span data-ttu-id="5c2cf-109">Instrukcje: Zwracane zestawy wierszy</span><span class="sxs-lookup"><span data-stu-id="5c2cf-109">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="5c2cf-110">Opisuje sposób zwracania wierszy danych i pokazuje, jak używać parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="5c2cf-111">Instrukcje: Korzystanie z procedur składowanych przyjmujących parametry</span><span class="sxs-lookup"><span data-stu-id="5c2cf-111">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="5c2cf-112">Opisuje sposób używania parametrów wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="5c2cf-113">Instrukcje: Korzystanie z procedur składowanych mapowanych na wiele kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="5c2cf-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="5c2cf-114">Opisuje, jak zapewnić zwroty wielu kształtów w tej samej procedurze składowanej.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="5c2cf-115">Instrukcje: Użyj procedur składowanych mapowanych dla sekwencyjnych kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="5c2cf-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="5c2cf-116">Opisuje, w jaki sposób zapewnić wiele kształtów, w których jest znana sekwencja powrotu.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="5c2cf-117">Dostosowywanie operacji przy użyciu procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="5c2cf-117">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="5c2cf-118">Opisuje, jak używać procedur składowanych do implementowania operacji INSERT, Update i DELETE.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="5c2cf-119">Dostosowywanie operacji przy użyciu wyłącznie procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="5c2cf-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="5c2cf-120">Opisuje, jak używać niczego, ale procedury składowane do implementowania operacji INSERT, Update i DELETE.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5c2cf-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5c2cf-121">Related Sections</span></span>  
 [<span data-ttu-id="5c2cf-122">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="5c2cf-122">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="5c2cf-123">Zawiera informacje o sposobach tworzenia i używania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="5c2cf-124">Przewodnik: Używanie tylko procedur składowanych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c2cf-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="5c2cf-125">Obejmuje procedury, które ilustrują sposób korzystania z procedur składowanych w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="5c2cf-126">Przewodnik: Używanie tylko procedur składowanychC#()</span><span class="sxs-lookup"><span data-stu-id="5c2cf-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="5c2cf-127">Obejmuje procedury, które ilustrują sposób korzystania z procedur składowanych w programie C#.</span><span class="sxs-lookup"><span data-stu-id="5c2cf-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
