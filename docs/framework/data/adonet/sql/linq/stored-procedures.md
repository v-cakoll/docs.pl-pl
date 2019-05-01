---
title: Procedury składowane
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 9201965192f300de62679c1e5be75cf98a24e700
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917946"
---
# <a name="stored-procedures"></a><span data-ttu-id="da394-102">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="da394-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="da394-103">używa metody w modelu obiektu, który reprezentuje procedur składowanych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="da394-103">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="da394-104">Wyznaczenie jako procedury składowane metod, stosując <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu i, jeśli to konieczne, <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="da394-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="da394-105">Aby uzyskać więcej informacji, zobacz [LINQ to SQL Model obiektów](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="da394-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="da394-106">Deweloperzy korzystający z programu Visual Studio zazwyczaj użyje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do procedurom składowanym w mapie.</span><span class="sxs-lookup"><span data-stu-id="da394-106">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map stored procedures.</span></span> <span data-ttu-id="da394-107">Tematy w tej sekcji przedstawiają sposób utworzenia i wywoływanie tych metod w aplikacji, jeśli możesz napisać kod.</span><span class="sxs-lookup"><span data-stu-id="da394-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da394-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="da394-108">In This Section</span></span>  
 [<span data-ttu-id="da394-109">Instrukcje: Zwracane zestawy wierszy</span><span class="sxs-lookup"><span data-stu-id="da394-109">How to: Return Rowsets</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 <span data-ttu-id="da394-110">W tym artykule opisano sposób zwrócenia wierszy danych i sposobu używania parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="da394-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="da394-111">Instrukcje: Używanie procedur składowanych, które przyjmują parametry</span><span class="sxs-lookup"><span data-stu-id="da394-111">How to: Use Stored Procedures that Take Parameters</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="da394-112">Opisuje sposób używania parametrów wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="da394-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="da394-113">Instrukcje: Używanie procedur składowanych zmapowanych do wielu kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="da394-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="da394-114">Opisuje sposób zapewnienia zwraca wielu kształtów w tej samej procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="da394-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="da394-115">Instrukcje: Używanie procedur składowanych zmapowanych do sekwencyjnych kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="da394-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="da394-116">Opisuje sposób zapewnienia wielu kształtów, gdzie jest znany zwracanej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="da394-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="da394-117">Dostosowywanie operacji przy użyciu procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="da394-117">Customizing Operations By Using Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="da394-118">W tym artykule opisano sposób użycia procedur składowanych na potrzeby implementacji insert, update i operacje usuwania.</span><span class="sxs-lookup"><span data-stu-id="da394-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="da394-119">Dostosowywanie operacji przy użyciu wyłącznie procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="da394-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="da394-120">Opisuje sposób używania nothing, ale procedur składowanych na potrzeby implementacji insert, update i operacje usuwania.</span><span class="sxs-lookup"><span data-stu-id="da394-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da394-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="da394-121">Related Sections</span></span>  
 [<span data-ttu-id="da394-122">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="da394-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="da394-123">Zawiera informacje o sposobie tworzenia i używania usługi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="da394-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="da394-124">Przewodnik: Przy użyciu wyłącznie procedur składowanych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da394-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="da394-125">Zawiera procedury, które ilustrują sposób korzystania z procedur składowanych w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="da394-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="da394-126">Przewodnik: Przy użyciu wyłącznie procedur składowanych (C#)</span><span class="sxs-lookup"><span data-stu-id="da394-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="da394-127">Zawiera procedury, które ilustrują sposób korzystania z procedur składowanych w programie C#.</span><span class="sxs-lookup"><span data-stu-id="da394-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
