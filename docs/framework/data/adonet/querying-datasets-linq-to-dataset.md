---
title: "Wykonywanie zapytania zestawów danych (LINQ do DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c9830587e70d7671200fac20c8384f1a470a751e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="61ce7-102">Wykonywanie zapytania zestawów danych (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="61ce7-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="61ce7-103">Po <xref:System.Data.DataSet> obiekt został wypełniony danymi, można rozpocząć, badając ją.</span><span class="sxs-lookup"><span data-stu-id="61ce7-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="61ce7-104">Formułowania zapytań dotyczących [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] jest podobny do sposobu używania [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] względem innych [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]— włączone źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="61ce7-104">Formulating queries with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="61ce7-105">Należy jednak pamiętać, że gdy używasz [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] odpytuje za pośrednictwem <xref:System.Data.DataSet> obiektu wyszukując wyliczenie <xref:System.Data.DataRow> obiektów zamiast wyliczenia typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="61ce7-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="61ce7-106">Oznacza to, że można użyć dowolnego z elementów członkowskich <xref:System.Data.DataRow> klasy w Twojej [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="61ce7-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="61ce7-107">Dzięki temu można tworzyć zaawansowane, złożone kwerendy.</span><span class="sxs-lookup"><span data-stu-id="61ce7-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="61ce7-108">Tak jak w innych implementacjach [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], można utworzyć [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania w dwóch różnych formularzach: wyrażenie składnia zapytania i metody zapytań.</span><span class="sxs-lookup"><span data-stu-id="61ce7-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="61ce7-109">Aby uzyskać więcej informacji o tych dwóch form, zobacz [wprowadzenie do LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span><span class="sxs-lookup"><span data-stu-id="61ce7-109">For more information about these two forms, see [Getting Started with LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span></span> <span data-ttu-id="61ce7-110">Za pomocą składni wyrażenia zapytania lub składnia zapytania oparte na metodzie do wykonania zapytania względem jednej tabel w <xref:System.Data.DataSet>, dla wielu tabel w <xref:System.Data.DataSet>, lub dla tabel w typizowanych <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="61ce7-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61ce7-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="61ce7-111">In This Section</span></span>  
 [<span data-ttu-id="61ce7-112">Zapytania jednotabelowe</span><span class="sxs-lookup"><span data-stu-id="61ce7-112">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="61ce7-113">Opisuje sposób wykonywania zapytań pojedynczej tabeli.</span><span class="sxs-lookup"><span data-stu-id="61ce7-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="61ce7-114">Zapytania wielotabelowe</span><span class="sxs-lookup"><span data-stu-id="61ce7-114">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="61ce7-115">Opisuje sposób wykonywania zapytań między tabelami.</span><span class="sxs-lookup"><span data-stu-id="61ce7-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="61ce7-116">Wykonywanie zapytania do typizowanych zestawów danych</span><span class="sxs-lookup"><span data-stu-id="61ce7-116">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="61ce7-117">Opisuje sposób tworzenia zapytań wpisany <xref:System.Data.DataSet> obiektów.</span><span class="sxs-lookup"><span data-stu-id="61ce7-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ce7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61ce7-118">See Also</span></span>  
 [<span data-ttu-id="61ce7-119">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="61ce7-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="61ce7-120">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="61ce7-120">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
