---
title: Wykonywanie zapytania dotyczącego zestawów danych (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783048"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="8704e-102">Wykonywanie zapytania dotyczącego zestawów danych (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8704e-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="8704e-103">Po wypełnieniu <xref:System.Data.DataSet> obiektu danymi można rozpocząć wykonywanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="8704e-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="8704e-104">Formułowanie zapytań w LINQ to DataSet jest podobne do użycia [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] z innymi [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="8704e-104">Formulating queries with LINQ to DataSet is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="8704e-105">Należy jednak pamiętać, że w przypadku używania [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytań <xref:System.Data.DataSet> względem obiektu, który wykonuje <xref:System.Data.DataRow> zapytanie o Wyliczenie obiektów, zamiast wyliczania typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="8704e-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="8704e-106">Oznacza to, że można użyć dowolnego z elementów członkowskich <xref:System.Data.DataRow> klasy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] w zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="8704e-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="8704e-107">Pozwala to na tworzenie rozbudowanych, złożonych zapytań.</span><span class="sxs-lookup"><span data-stu-id="8704e-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="8704e-108">Podobnie jak w przypadku innych [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]implementacji programu, można utworzyć zapytania LINQ to DataSet w dwóch różnych formularzach: składni wyrażeń zapytania i składni zapytania opartego na metodzie.</span><span class="sxs-lookup"><span data-stu-id="8704e-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="8704e-109">Można użyć składni wyrażeń zapytania lub składni zapytania opartej na metodzie <xref:System.Data.DataSet>, aby wykonywać zapytania dotyczące pojedynczych tabel w, względem wielu tabel <xref:System.Data.DataSet>w, lub względem tabel w określonym typie <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8704e-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8704e-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8704e-110">In This Section</span></span>  
 [<span data-ttu-id="8704e-111">Zapytania jednotabelowe</span><span class="sxs-lookup"><span data-stu-id="8704e-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="8704e-112">Opisuje sposób wykonywania zapytań pojedynczej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8704e-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="8704e-113">Zapytania wielotabelowe</span><span class="sxs-lookup"><span data-stu-id="8704e-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="8704e-114">Opisuje sposób wykonywania zapytań między tabelami.</span><span class="sxs-lookup"><span data-stu-id="8704e-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="8704e-115">Wykonywanie zapytania do typizowanych zestawów danych</span><span class="sxs-lookup"><span data-stu-id="8704e-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="8704e-116">Opisuje sposób wykonywania zapytań względem <xref:System.Data.DataSet> wpisanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="8704e-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8704e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8704e-117">See also</span></span>

- [<span data-ttu-id="8704e-118">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8704e-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="8704e-119">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="8704e-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
