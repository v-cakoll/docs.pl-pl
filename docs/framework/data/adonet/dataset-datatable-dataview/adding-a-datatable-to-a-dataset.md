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
ms.workload: dotnet
ms.openlocfilehash: c5846f93cfa75d7f0e760a24ee65fa838abc1eb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-datatable-to-a-dataset"></a>Dodawanie elementu DataTable z zestawem danych
ADO.NET umożliwia utworzenie <xref:System.Data.DataTable> obiekty i dodaj je do istniejącej <xref:System.Data.DataSet>. Można ustawić informacji ograniczenia dla <xref:System.Data.DataTable> za pomocą <xref:System.Data.DataTable.PrimaryKey%2A> i <xref:System.Data.DataColumn.Unique%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataSet>, dodaje nową <xref:System.Data.DataTable> do obiektu <xref:System.Data.DataSet>, a następnie dodaje trzy <xref:System.Data.DataColumn> obiektów do tabeli. Na koniec kod ustawia jednej kolumny jako kolumny klucza podstawowego.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Uwzględniana wielkość liter  
 Co najmniej dwie tabele lub relacji z tej samej nazwy, ale o innej wielkości znaków, może istnieć w <xref:System.Data.DataSet>. W takich przypadkach odwołania według nazwy tabel i relacji jest uwzględniana wielkość liter. Na przykład jeśli <xref:System.Data.DataSet> **zestawu danych** zawiera tabele **Table1** i **table1**, czy odwołanie **Tabela1** według nazwy jako **dataSet.Tables["Table1"]**, i **table1** jako **dataSet.Tables["table1"]**. Próby odwołania jednej z tabel jako **dataSet.Tables["TABLE1"]** wygenerowanie wyjątku.  
  
 Zachowanie uwzględnianie wielkości liter nie ma zastosowania, jeśli tylko jedna tabela lub relacji o określonej nazwie. Na przykład, jeśli <xref:System.Data.DataSet> ma tylko **Table1**, można odwoływać się za pomocą **dataSet.Tables["TABLE1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataSet.CaseSensitive%2A> Właściwość <xref:System.Data.DataSet> nie ma wpływu na tego zachowania. <xref:System.Data.DataSet.CaseSensitive%2A> Właściwość jest stosowana do danych w <xref:System.Data.DataSet> i ma wpływ na sortowanie, wyszukiwanie, filtrowanie, wymuszenie ograniczenia i tak dalej.  
  
## <a name="namespace-support"></a>Obsługa Namespace  
 W wersjach programu ADO.NET starszych niż 2.0 dwie tabele nie mogą mieć takiej samej nazwie, nawet jeżeli znajdowały się w różnych przestrzeniach nazw. To ograniczenie zostało usunięte w ADO.NET 2.0. A <xref:System.Data.DataSet> może zawierać dwóch tabel, które mają taki sam <xref:System.Data.DataTable.TableName%2A> wartość właściwości, ale o różnych <xref:System.Data.DataTable.Namespace%2A> wartości właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
