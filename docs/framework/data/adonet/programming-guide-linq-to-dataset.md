---
title: Przewodnik programowania w języku (LINQ do DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: 70fb2d38a055a6b376a711aae28ba69e6c2dd771
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353289"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="db6b4-102">Przewodnik programowania w języku (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="db6b4-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="db6b4-103">Ta sekcja zawiera informacje o pojęciach i przykłady dotyczące programowania za pomocą [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db6b4-103">This section provides conceptual information and examples for programming with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db6b4-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="db6b4-104">In This Section</span></span>  
 [<span data-ttu-id="db6b4-105">Zapytania w LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="db6b4-105">Queries in LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md)  
 <span data-ttu-id="db6b4-106">Informacje na temat pisania [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="db6b4-106">Provides information about how to write [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="db6b4-107">Wykonywanie zapytania do zestawów danych</span><span class="sxs-lookup"><span data-stu-id="db6b4-107">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="db6b4-108">Opisuje sposób zapytania <xref:System.Data.DataSet> obiektów.</span><span class="sxs-lookup"><span data-stu-id="db6b4-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="db6b4-109">Porównywanie wierszy danych</span><span class="sxs-lookup"><span data-stu-id="db6b4-109">Comparing DataRows</span></span>](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="db6b4-110">Informacje dotyczące używania <xref:System.Data.DataRowComparer> obiekt do porównania wierszy danych.</span><span class="sxs-lookup"><span data-stu-id="db6b4-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="db6b4-111">Tworzenie elementu DataTable na podstawie zapytania</span><span class="sxs-lookup"><span data-stu-id="db6b4-111">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="db6b4-112">Zawiera informacje o tworzeniu <xref:System.Data.DataTable> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania przy użyciu <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="db6b4-112">Provides information about creating a <xref:System.Data.DataTable> from a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="db6b4-113">Porady: Implementowanie CopyToDataTable\<T > gdzie ogólny typ T nie jest element DataRow</span><span class="sxs-lookup"><span data-stu-id="db6b4-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="db6b4-114">Opisuje sposób zaimplementowania niestandardowego `CopyToDataTable<T>` metody, gdzie T parametr generyczny nie jest typu <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="db6b4-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="db6b4-115">Pole ogólne i metody SetField</span><span class="sxs-lookup"><span data-stu-id="db6b4-115">Generic Field and SetField Methods</span></span>](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="db6b4-116">Informacje na temat ogólnych <xref:System.Data.DataRowExtensions.Field%2A> i <xref:System.Data.DataRowExtensions.SetField%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="db6b4-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="db6b4-117">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="db6b4-117">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="db6b4-118">Zawiera opis korzystania z wiązania z danymi <xref:System.Data.DataView> obiektu.</span><span class="sxs-lookup"><span data-stu-id="db6b4-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="db6b4-119">Debugowanie zapytań LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="db6b4-119">Debugging LINQ to DataSet Queries</span></span>](../../../../docs/framework/data/adonet/debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="db6b4-120">Informacje na temat debugowania i rozwiązywania problemów [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="db6b4-120">Provides information about debugging and troubleshooting [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries.</span></span>  
  
 [<span data-ttu-id="db6b4-121">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="db6b4-121">Security</span></span>](../../../../docs/framework/data/adonet/security-linq-to-dataset.md)  
 <span data-ttu-id="db6b4-122">W tym artykule opisano problemy z zabezpieczeniami w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db6b4-122">Describes security issues in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span>  
  
 [<span data-ttu-id="db6b4-123">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="db6b4-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 <span data-ttu-id="db6b4-124">Przykłady zapytania, które używają [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operatorów.</span><span class="sxs-lookup"><span data-stu-id="db6b4-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="db6b4-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="db6b4-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="db6b4-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db6b4-126">See Also</span></span>  
 [<span data-ttu-id="db6b4-127">LINQ do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="db6b4-127">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/library/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 [<span data-ttu-id="db6b4-128">NIE w kompilacji: Przewodnik programowania w języku ogólne LINQ</span><span class="sxs-lookup"><span data-stu-id="db6b4-128">NOT IN BUILD: LINQ General Programming Guide</span></span>](http://msdn.microsoft.com/library/609c7a6b-cbdd-429d-99f3-78d13d3bc049)  
 [<span data-ttu-id="db6b4-129">LINQ Framework</span><span class="sxs-lookup"><span data-stu-id="db6b4-129">LINQ Framework</span></span>](http://msdn.microsoft.com/library/897ea0fc-40db-4694-bbe5-7dd339d5bf94)
