---
title: Wykonywanie zapytania do kolekcji DataRowView w elemencie DataView
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
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 02b32157fe88bddfd9a777042f6da87aa48ca551
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="0d64c-102">Wykonywanie zapytania do kolekcji DataRowView w elemencie DataView</span><span class="sxs-lookup"><span data-stu-id="0d64c-102">Querying the DataRowView Collection in a DataView</span></span>
<span data-ttu-id="0d64c-103"><xref:System.Data.DataView> Udostępnia kolekcję wyliczalny <xref:System.Data.DataRowView> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0d64c-103">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="0d64c-104"><xref:System.Data.DataRowView>reprezentuje dostosowany widok <xref:System.Data.DataRow> i przedstawia określoną wersję tego <xref:System.Data.DataRow> w formancie.</span><span class="sxs-lookup"><span data-stu-id="0d64c-104"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="0d64c-105">Tylko jedna wersja <xref:System.Data.DataRow> można wyświetlić za pomocą formantu, takich jak <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0d64c-105">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="0d64c-106">Dostęp można uzyskać <xref:System.Data.DataRow> widoczne przy <xref:System.Data.DataRowView> za pośrednictwem <xref:System.Data.DataRowView.Row%2A> właściwość <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="0d64c-106">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="0d64c-107">Podczas wyświetlania wartości przy użyciu <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> właściwość określa, która wersja wiersza podstawowych <xref:System.Data.DataRow> jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="0d64c-107">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="0d64c-108">Uzyskać informacji na temat uzyskiwania dostępu do wersji innego wiersza przy użyciu <xref:System.Data.DataRow>, zobacz [stany wiersza i wersje wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="0d64c-108">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="0d64c-109">Ponieważ kolekcja <xref:System.Data.DataRowView> obiektów udostępnianych przez <xref:System.Data.DataView> jest wyliczalny, można użyć [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania nad nim.</span><span class="sxs-lookup"><span data-stu-id="0d64c-109">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to query over it.</span></span>  
  
 <span data-ttu-id="0d64c-110">Następujące przykładowe zapytania `Product` tabeli kolorze czerwony produktów i tworzy tabelę na podstawie zapytania.</span><span class="sxs-lookup"><span data-stu-id="0d64c-110">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="0d64c-111">A <xref:System.Data.DataView> jest tworzona na podstawie tabeli i <xref:System.Data.DataView.RowStateFilter%2A> właściwości ustawiono odfiltrować usunięte i zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="0d64c-111">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="0d64c-112"><xref:System.Data.DataView> Jest następnie używany jako źródło w zapytaniu składnika LINQ i <xref:System.Data.DataRowView> obiektów, które zostały zmodyfikowane i usuwane są powiązane z <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="0d64c-112">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="0d64c-113">Poniższy przykład tworzy tabelę produktów z widoku, który jest powiązany z <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="0d64c-113">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0d64c-114"><xref:System.Data.DataView> Zostanie zapytany o kolorze czerwony produktów i uporządkowanych wyników są powiązane z <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="0d64c-114">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="0d64c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d64c-115">See Also</span></span>  
 [<span data-ttu-id="0d64c-116">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0d64c-116">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
