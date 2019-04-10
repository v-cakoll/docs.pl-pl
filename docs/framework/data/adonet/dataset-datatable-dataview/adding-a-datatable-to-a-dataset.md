---
title: Dodawanie elementu DataTable do elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 392855e3db2ea10c90784a6f9003805b79db74a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230580"
---
# <a name="adding-a-datatable-to-a-dataset"></a>Dodawanie elementu DataTable do elementu DataSet
ADO.NET pozwala na tworzenie <xref:System.Data.DataTable> obiektów i dodać je do istniejącej <xref:System.Data.DataSet>. Można ustawić informacje o ograniczeniach dla <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTable.PrimaryKey%2A> i <xref:System.Data.DataColumn.Unique%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataSet>, dodaje nowy <xref:System.Data.DataTable> obiekt <xref:System.Data.DataSet>, a następnie dodaje trzy <xref:System.Data.DataColumn> obiektów do tabeli. Na koniec kod ustawia jedną kolumnę jako kolumna klucza podstawowego.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Rozróżnianie wielkości liter  
 Co najmniej dwóch tabel lub relacji o takiej samej nazwie, ale inną wielkością liter, może znajdować się w <xref:System.Data.DataSet>. W takich przypadkach odwołania według nazwy do tabel i relacji jest uwzględniana wielkość liter. Na przykład jeśli <xref:System.Data.DataSet> **zestawu danych** zawiera tabele **Tabela1** i **Tabela1**, czy odwołanie **Tabela1** według nazwy, jako **dataSet.Tables["Table1"]**, i **Tabela1** jako **dataSet.Tables["table1"]**. Podjęto próbę odwoływać się do jednej z tabel jako **dataSet.Tables["TABLE1"]** wygeneruje wyjątek.  
  
 Zachowanie uwzględnianie wielkości liter nie ma zastosowania, jeśli tylko jedna tabela lub relacji o określonej nazwie. Na przykład, jeśli <xref:System.Data.DataSet> ma tylko **Tabela1**, możesz odwoływać się za pomocą **dataSet.Tables["TABLE1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataSet.CaseSensitive%2A> Właściwość <xref:System.Data.DataSet> nie wpływa na to zachowanie. <xref:System.Data.DataSet.CaseSensitive%2A> Właściwość ma zastosowanie do danych w <xref:System.Data.DataSet> i wpływa na sortowanie, wyszukiwanie, filtrowanie, wymuszania ograniczeń i tak dalej.  
  
## <a name="namespace-support"></a>Obsługa Namespace  
 W wersjach programu ADO.NET starszych niż 2.0 dwie tabele nie może mieć takiej samej nazwie, nawet jeśli były one w różnych obszarach nazw. To ograniczenie zostało usunięte ADO.NET w wersji 2.0. A <xref:System.Data.DataSet> może zawierać dwóch tabel, które mają taki sam <xref:System.Data.DataTable.TableName%2A> wartości właściwości, ale o różnych <xref:System.Data.DataTable.Namespace%2A> wartości właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
