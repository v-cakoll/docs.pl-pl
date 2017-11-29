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
ms.openlocfilehash: b17a489552e7b2bcb6044fce99e5f526b8293a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>Wykonywanie zapytania do kolekcji DataRowView w elemencie DataView
<xref:System.Data.DataView> Udostępnia kolekcję wyliczalny <xref:System.Data.DataRowView> obiektów. <xref:System.Data.DataRowView>reprezentuje dostosowany widok <xref:System.Data.DataRow> i przedstawia określoną wersję tego <xref:System.Data.DataRow> w formancie. Tylko jedna wersja <xref:System.Data.DataRow> można wyświetlić za pomocą formantu, takich jak <xref:System.Windows.Forms.DataGridView>. Dostęp można uzyskać <xref:System.Data.DataRow> widoczne przy <xref:System.Data.DataRowView> za pośrednictwem <xref:System.Data.DataRowView.Row%2A> właściwość <xref:System.Data.DataRowView>. Podczas wyświetlania wartości przy użyciu <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> właściwość określa, która wersja wiersza podstawowych <xref:System.Data.DataRow> jest widoczna. Uzyskać informacji na temat uzyskiwania dostępu do wersji innego wiersza przy użyciu <xref:System.Data.DataRow>, zobacz [stany wiersza i wersje wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md). Ponieważ kolekcja <xref:System.Data.DataRowView> obiektów udostępnianych przez <xref:System.Data.DataView> jest wyliczalny, można użyć [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania nad nim.  
  
 Następujące przykładowe zapytania `Product` tabeli kolorze czerwony produktów i tworzy tabelę na podstawie zapytania. A <xref:System.Data.DataView> jest tworzona na podstawie tabeli i <xref:System.Data.DataView.RowStateFilter%2A> właściwości ustawiono odfiltrować usunięte i zmodyfikowanych wierszy. <xref:System.Data.DataView> Jest następnie używany jako źródło w zapytaniu składnika LINQ i <xref:System.Data.DataRowView> obiektów, które zostały zmodyfikowane i usuwane są powiązane z <xref:System.Windows.Forms.DataGridView> formantu.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Poniższy przykład tworzy tabelę produktów z widoku, który jest powiązany z <xref:System.Windows.Forms.DataGridView> formantu. <xref:System.Data.DataView> Zostanie zapytany o kolorze czerwony produktów i uporządkowanych wyników są powiązane z <xref:System.Windows.Forms.DataGridView> formantu.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych i LINQ do DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
