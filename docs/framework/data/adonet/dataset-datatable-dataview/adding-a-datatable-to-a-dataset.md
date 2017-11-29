---
title: Dodawanie elementu DataTable z zestawem danych
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
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f70292794866530de5b7abf7dac1edd09d300c94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="adding-a-datatable-to-a-dataset"></a><span data-ttu-id="99b21-102">Dodawanie elementu DataTable z zestawem danych</span><span class="sxs-lookup"><span data-stu-id="99b21-102">Adding a DataTable to a DataSet</span></span>
<span data-ttu-id="99b21-103">ADO.NET umożliwia utworzenie <xref:System.Data.DataTable> obiekty i dodaj je do istniejącej <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="99b21-103">ADO.NET enables you to create <xref:System.Data.DataTable> objects and add them to an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="99b21-104">Można ustawić informacji ograniczenia dla <xref:System.Data.DataTable> za pomocą <xref:System.Data.DataTable.PrimaryKey%2A> i <xref:System.Data.DataColumn.Unique%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="99b21-104">You can set constraint information for a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.PrimaryKey%2A> and <xref:System.Data.DataColumn.Unique%2A> properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99b21-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="99b21-105">Example</span></span>  
 <span data-ttu-id="99b21-106">Poniższy przykład tworzy <xref:System.Data.DataSet>, dodaje nową <xref:System.Data.DataTable> do obiektu <xref:System.Data.DataSet>, a następnie dodaje trzy <xref:System.Data.DataColumn> obiektów do tabeli.</span><span class="sxs-lookup"><span data-stu-id="99b21-106">The following example constructs a <xref:System.Data.DataSet>, adds a new <xref:System.Data.DataTable> object to the <xref:System.Data.DataSet>, and then adds three <xref:System.Data.DataColumn> objects to the table.</span></span> <span data-ttu-id="99b21-107">Na koniec kod ustawia jednej kolumny jako kolumny klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="99b21-107">Finally, the code sets one column as the primary key column.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a><span data-ttu-id="99b21-108">Uwzględniana wielkość liter</span><span class="sxs-lookup"><span data-stu-id="99b21-108">Case Sensitivity</span></span>  
 <span data-ttu-id="99b21-109">Co najmniej dwie tabele lub relacji z tej samej nazwy, ale o innej wielkości znaków, może istnieć w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="99b21-109">Two or more tables or relations with the same name, but different casing, can exist in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="99b21-110">W takich przypadkach odwołania według nazwy tabel i relacji jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="99b21-110">In such cases, references by name to tables and relations are case sensitive.</span></span> <span data-ttu-id="99b21-111">Na przykład jeśli <xref:System.Data.DataSet> **zestawu danych** zawiera tabele **Table1** i **table1**, czy odwołanie **Tabela1** według nazwy jako **dataSet.Tables["Table1"]**, i **table1** jako **dataSet.Tables["table1"]**.</span><span class="sxs-lookup"><span data-stu-id="99b21-111">For example, if the <xref:System.Data.DataSet> **dataSet** contains tables **Table1** and **table1**, you would reference **Table1** by name as **dataSet.Tables["Table1"]**, and **table1** as **dataSet.Tables["table1"]**.</span></span> <span data-ttu-id="99b21-112">Próby odwołania jednej z tabel jako **dataSet.Tables["TABLE1"]** wygenerowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="99b21-112">Attempting to reference either of the tables as **dataSet.Tables["TABLE1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="99b21-113">Zachowanie uwzględnianie wielkości liter nie ma zastosowania, jeśli tylko jedna tabela lub relacji o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="99b21-113">The case-sensitivity behavior does not apply if only one table or relation has a particular name.</span></span> <span data-ttu-id="99b21-114">Na przykład, jeśli <xref:System.Data.DataSet> ma tylko **Table1**, można odwoływać się za pomocą **dataSet.Tables["TABLE1"]**.</span><span class="sxs-lookup"><span data-stu-id="99b21-114">For example, if the <xref:System.Data.DataSet> has only **Table1**, you can reference it using **dataSet.Tables["TABLE1"]**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99b21-115"><xref:System.Data.DataSet.CaseSensitive%2A> Właściwość <xref:System.Data.DataSet> nie ma wpływu na tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="99b21-115">The <xref:System.Data.DataSet.CaseSensitive%2A> property of the <xref:System.Data.DataSet> does not affect this behavior.</span></span> <span data-ttu-id="99b21-116"><xref:System.Data.DataSet.CaseSensitive%2A> Właściwość jest stosowana do danych w <xref:System.Data.DataSet> i ma wpływ na sortowanie, wyszukiwanie, filtrowanie, wymuszenie ograniczenia i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="99b21-116">The <xref:System.Data.DataSet.CaseSensitive%2A> property applies to the data in the <xref:System.Data.DataSet> and affects sorting, searching, filtering, enforcing constraints, and so on.</span></span>  
  
## <a name="namespace-support"></a><span data-ttu-id="99b21-117">Obsługa Namespace</span><span class="sxs-lookup"><span data-stu-id="99b21-117">Namespace Support</span></span>  
 <span data-ttu-id="99b21-118">W wersjach programu ADO.NET starszych niż 2.0 dwie tabele nie mogą mieć takiej samej nazwie, nawet jeżeli znajdowały się w różnych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="99b21-118">In versions of ADO.NET earlier than 2.0, two tables could not have the same name, even if they were in different namespaces.</span></span> <span data-ttu-id="99b21-119">To ograniczenie zostało usunięte w ADO.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="99b21-119">This limitation was removed in ADO.NET 2.0.</span></span> <span data-ttu-id="99b21-120">A <xref:System.Data.DataSet> może zawierać dwóch tabel, które mają taki sam <xref:System.Data.DataTable.TableName%2A> wartość właściwości, ale o różnych <xref:System.Data.DataTable.Namespace%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="99b21-120">A <xref:System.Data.DataSet> can contain two tables that have the same <xref:System.Data.DataTable.TableName%2A> property value but different <xref:System.Data.DataTable.Namespace%2A> property values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b21-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99b21-121">See Also</span></span>  
 [<span data-ttu-id="99b21-122">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="99b21-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="99b21-123">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="99b21-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
