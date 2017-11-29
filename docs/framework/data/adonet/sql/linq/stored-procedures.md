---
title: "Procedury składowane"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1cf8d155dd04cd4f7b3f860186428c14ce4e462e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="stored-procedures"></a><span data-ttu-id="e8eec-102">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="e8eec-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e8eec-103">używa metody w modelu obiektu do reprezentowania procedur przechowywanych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e8eec-103"> uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="e8eec-104">Wyznaczyć procedur składowanych jako metody, stosując <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu i, jeżeli jest to wymagane, <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e8eec-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="e8eec-105">Aby uzyskać więcej informacji, zobacz [LINQ w modelu obiektu SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="e8eec-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="e8eec-106">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] zwykle użyje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="e8eec-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map stored procedures.</span></span> <span data-ttu-id="e8eec-107">Tematy w tej sekcji przedstawiają sposób tworzą i wywołania tych metod w aplikacji, podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="e8eec-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8eec-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e8eec-108">In This Section</span></span>  
 [<span data-ttu-id="e8eec-109">Porady: zwracać zestawy wierszy</span><span class="sxs-lookup"><span data-stu-id="e8eec-109">How to: Return Rowsets</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 <span data-ttu-id="e8eec-110">Zawiera opis sposobu zwracanie wszystkich wierszy danych i przedstawia sposób użycia parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="e8eec-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="e8eec-111">Porady: Użyj procedur składowanych, które przyjmują parametrów</span><span class="sxs-lookup"><span data-stu-id="e8eec-111">How to: Use Stored Procedures that Take Parameters</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="e8eec-112">Informacje dotyczące używania parametrów wejściowych i wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e8eec-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="e8eec-113">Porady: Użyj procedur składowanych mapowane do wielu kształtów wyników</span><span class="sxs-lookup"><span data-stu-id="e8eec-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="e8eec-114">Opisuje sposób zapewnienia zwraca wiele kształtów w tej samej procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="e8eec-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="e8eec-115">Porady: Użyj procedur składowanych mapowane do wyniku sekwencyjnych kształtów</span><span class="sxs-lookup"><span data-stu-id="e8eec-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="e8eec-116">Opisuje sposób zapewnienia wielu kształtów, gdzie jest znany sekwencji zwrotnej.</span><span class="sxs-lookup"><span data-stu-id="e8eec-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="e8eec-117">Dostosowywanie operacje przy użyciu procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="e8eec-117">Customizing Operations By Using Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="e8eec-118">W tym artykule opisano sposób użycia procedury składowane służące do implementacji insert, update i operacji usuwania.</span><span class="sxs-lookup"><span data-stu-id="e8eec-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="e8eec-119">Wyłącznie Dostosowywanie operacje przy użyciu procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="e8eec-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="e8eec-120">Informacje dotyczące używania nic, ale procedury składowane służące do implementacji insert, update i operacji usuwania.</span><span class="sxs-lookup"><span data-stu-id="e8eec-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e8eec-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e8eec-121">Related Sections</span></span>  
 [<span data-ttu-id="e8eec-122">Przewodnik programowania w języku</span><span class="sxs-lookup"><span data-stu-id="e8eec-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="e8eec-123">Zawiera informacje o sposobie tworzenia i używania programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="e8eec-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="e8eec-124">Wskazówki: Tylko przy użyciu przechowywanych procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8eec-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="e8eec-125">Zawiera procedury, które przedstawiają sposób użycia procedury składowane w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e8eec-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="e8eec-126">Wskazówki: Tylko przy użyciu przechowywanych procedur (C#)</span><span class="sxs-lookup"><span data-stu-id="e8eec-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="e8eec-127">Zawiera procedury, które przedstawiają sposób użycia procedury składowane w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e8eec-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
