---
title: Wykonywanie zapytania do kolekcji DataRowView w widoku danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 17fab6e4c178eee6b5135045fb953267db810898
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794454"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>Wykonywanie zapytania do kolekcji DataRowView w widoku danych
Uwidacznia wyliczalną kolekcję <xref:System.Data.DataRowView>obiektów. <xref:System.Data.DataView> <xref:System.Data.DataRowView>reprezentuje dostosowany widok <xref:System.Data.DataRow> a i wyświetla określoną wersję <xref:System.Data.DataRow> programu w kontrolce. Tylko jedna wersja programu <xref:System.Data.DataRow> może być wyświetlana za pomocą kontrolki, takiej <xref:System.Windows.Forms.DataGridView>jak. Można uzyskać dostęp do <xref:System.Data.DataRow> programu, który jest udostępniany <xref:System.Data.DataRowView> przez <xref:System.Data.DataRowView.Row%2A> Właściwość <xref:System.Data.DataRowView>. Podczas wyświetlania wartości przy użyciu <xref:System.Data.DataRowView> <xref:System.Data.DataView.RowStateFilter%2A> , właściwość określa, która wersja <xref:System.Data.DataRow> wiersza jest uwidoczniona. Aby uzyskać informacje o uzyskiwaniu dostępu do różnych <xref:System.Data.DataRow>wersji wierszy przy użyciu, zobacz [Stany wiersza i wersje wierszy](./dataset-datatable-dataview/row-states-and-row-versions.md). Ponieważ kolekcja <xref:System.Data.DataRowView> obiektów uwidocznionych <xref:System.Data.DataView> przez program jest wyliczalna, można użyć LINQ to DataSet, aby wykonać zapytanie.  
  
 Poniższy przykład wysyła zapytanie `Product` do tabeli w poszukiwaniu czerwonych produktów i tworzy tabelę z tej kwerendy. Jest tworzony na podstawie tabeli <xref:System.Data.DataView.RowStateFilter%2A> , a właściwość jest ustawiona do filtrowania dla usuniętych i zmodyfikowanych wierszy. <xref:System.Data.DataView> Jest on używany jako źródło w zapytaniu LINQ, <xref:System.Data.DataRowView> a obiekty, które zostały zmodyfikowane i <xref:System.Windows.Forms.DataGridView> usunięte są powiązane z kontrolką. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 Poniższy przykład tworzy tabelę produktów z widoku, który jest powiązany z <xref:System.Windows.Forms.DataGridView> kontrolką. Zapytanie jest wykonywane w przypadku produktów czerwonych, a uporządkowane wyniki są powiązane <xref:System.Windows.Forms.DataGridView> z kontrolką. <xref:System.Data.DataView>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych i LINQ to DataSet](data-binding-and-linq-to-dataset.md)
