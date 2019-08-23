---
title: Dodawanie elementu DataTable do elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 2bc0bca55dcdc350537f0826ab3a675747ee5497
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951328"
---
# <a name="adding-a-datatable-to-a-dataset"></a>Dodawanie elementu DataTable do elementu DataSet
ADO.NET umożliwia tworzenie <xref:System.Data.DataTable> obiektów i dodawanie ich do istniejącej <xref:System.Data.DataSet>. Można ustawić informacje o ograniczeniach dla <xref:System.Data.DataTable> elementu przy <xref:System.Data.DataTable.PrimaryKey%2A> użyciu właściwości <xref:System.Data.DataColumn.Unique%2A> i.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataSet>, dodaje nowy <xref:System.Data.DataTable> obiekt do <xref:System.Data.DataSet>, a następnie dodaje trzy <xref:System.Data.DataColumn> obiekty do tabeli. Na koniec kod ustawia jedną kolumnę jako kolumnę klucza podstawowego.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Rozróżnianie wielkości liter  
 Co najmniej dwie tabele lub relacje o tej samej nazwie, ale różne wielkości liter, mogą znajdować <xref:System.Data.DataSet>się w. W takich przypadkach odwołania według nazwy do tabel i relacji uwzględniają wielkość liter. Na przykład, <xref:System.Data.DataSet> Jeśli **zestaw danych** zawiera tabele **Tabela1** i **Tabela1**, należy odwołać się do **Tabela1** według nazwy jako **DataSet. tabele ["Tabela1"]** i **Tabela1** jako **DataSet. Tables ["Tabela1"]** . Próba odwołująca się do jednej z tabel jako **DataSet. tabele ["Tabela1"]** wygenerują wyjątek.  
  
 Zachowanie z rozróżnianiem wielkości liter nie ma zastosowania, jeśli tylko jedna tabela lub relacja ma określoną nazwę. Na przykład, jeśli <xref:System.Data.DataSet> ma tylko **Tabela1**, można odwoływać się do niego przy użyciu **zestawu danych. tabele ["Tabela1"]** .  
  
> [!NOTE]
> <xref:System.Data.DataSet.CaseSensitive%2A> Właściwość<xref:System.Data.DataSet> nie ma wpływu na to zachowanie. Właściwość ma zastosowanie do danych <xref:System.Data.DataSet> w i ma wpływ na sortowanie, wyszukiwanie, filtrowanie, wymuszanie ograniczeń itd. <xref:System.Data.DataSet.CaseSensitive%2A>  
  
## <a name="namespace-support"></a>Obsługa przestrzeni nazw  
 W wersjach programu ADO.NET starszej niż 2,0, dwie tabele nie mogły mieć takiej samej nazwy, nawet jeśli znajdują się w różnych przestrzeniach nazw. To ograniczenie zostało usunięte w ADO.NET 2,0. Może zawierać dwie tabele, które mają taką samą <xref:System.Data.DataTable.TableName%2A> wartość właściwości, ale <xref:System.Data.DataTable.Namespace%2A> różne wartości właściwości. <xref:System.Data.DataSet>  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
