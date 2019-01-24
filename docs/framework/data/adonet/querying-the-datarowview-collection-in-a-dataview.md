---
title: Wykonywanie zapytań do kolekcji DataRowView w widoku danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 1890ab2fcc7e1427d9c74f6c981e232802b0eb1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643744"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>Wykonywanie zapytań do kolekcji DataRowView w widoku danych
<xref:System.Data.DataView> Udostępnia wyliczalny zbiór <xref:System.Data.DataRowView> obiektów. <xref:System.Data.DataRowView> reprezentuje dostosowany widok przedstawiający <xref:System.Data.DataRow> i wyświetla określoną wersję, <xref:System.Data.DataRow> w formancie. Tylko jedna wersja <xref:System.Data.DataRow> mogą być wyświetlane za pomocą kontrolki, takie jak <xref:System.Windows.Forms.DataGridView>. Możesz uzyskać dostęp <xref:System.Data.DataRow> , jest uwidaczniany przez <xref:System.Data.DataRowView> za pośrednictwem <xref:System.Data.DataRowView.Row%2A> właściwość <xref:System.Data.DataRowView>. Podczas wyświetlania wartości przy użyciu <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> właściwość określa, którą wersję wiersza elementu bazowego <xref:System.Data.DataRow> jest widoczna. Uzyskać informacji na temat uzyskiwania dostępu do wersji innego wiersza przy użyciu <xref:System.Data.DataRow>, zobacz [stany wiersza i wersje wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md). Ponieważ kolekcja <xref:System.Data.DataRowView> udostępnianych przez obiekty <xref:System.Data.DataView> jest wyliczalny, możesz użyć [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania nad nim.  
  
 Następujące przykładowe kwerendy `Product` tabeli produktów red kolorowe i tworzy tabelę na podstawie tego zapytania. A <xref:System.Data.DataView> jest tworzona na podstawie tabeli i <xref:System.Data.DataView.RowStateFilter%2A> właściwość jest ustawiona na filtrowanie według usunięte i zmodyfikowane wiersze. <xref:System.Data.DataView> Jest następnie używany jako źródło w zapytaniu programu LINQ i <xref:System.Data.DataRowView> obiektów, które zostały zmodyfikowane i usuwane są powiązane z <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Poniższy przykład tworzy tabelę produktów z widoku, który jest powiązany z <xref:System.Windows.Forms.DataGridView> kontroli. <xref:System.Data.DataView> Zostaje przesłane zapytanie produktów red kolorowe i uporządkowanych wyników są powiązane z <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Zobacz także
- [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
