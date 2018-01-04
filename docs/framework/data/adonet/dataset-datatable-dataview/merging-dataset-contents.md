---
title: "Scalanie zawartości zestawu danych"
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
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 44d171cab4099436d7daea26def831f149b75b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="merging-dataset-contents"></a>Scalanie zawartości zestawu danych
Można użyć <xref:System.Data.DataSet.Merge%2A> sposób scalania zawartość <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow> tablicy do istniejącej `DataSet`. Kilka czynników, jak i opcje mają wpływ na sposób nowe dane są scalane istniejące `DataSet`.  
  
## <a name="primary-keys"></a>Klucze podstawowe  
 Jeśli klucz podstawowy tabeli odbieranie nowych danych i schematu z scalania, nowe wiersze z danych przychodzących są wspomagane istniejących wierszy, które mają taki sam <xref:System.Data.DataRowVersion.Original> wartości klucza podstawowego, jak przychodzących danych. Jeśli kolumny z przychodzącego schematu pasują do właściwości istniejącego schematu, dane w istniejących wierszy jest modyfikowany. Kolumny, która nie pasuje do istniejącego schematu są ignorowane lub dodane na podstawie <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametru. Nowe wiersze z wartości kluczy podstawowych, które nie pasują jakiekolwiek istniejące wiersze są dołączane do istniejącej tabeli.  
  
 Jeśli przychodzących lub istniejących wierszy mają stan wiersza <xref:System.Data.DataRowState.Added>, ich wartości klucza podstawowego są identyfikowane przy użyciu <xref:System.Data.DataRowVersion.Current> wartość klucza podstawowego `Added` wiersza, ponieważ nie `Original` istnieje wersji wiersza.  
  
 Jeśli przychodzące tabeli i istniejącej tabeli zawierają kolumnę o tej samej nazwie, ale różne typy danych, jest zgłaszany wyjątek i <xref:System.Data.DataSet.MergeFailed> zdarzenie `DataSet` jest wywoływane. Jeśli przychodzące tabeli i istniejącej tabeli zdefiniowano kluczy, ale klucze główne są przeznaczone dla różnych kolumn, jest zgłaszany wyjątek i `MergeFailed` zdarzenie `DataSet` jest wywoływane.  
  
 Jeśli tabela otrzymuje nowych danych z scalania nie ma klucza podstawowego, nowych wierszy z przychodzących danych nie można dopasować do istniejących wierszy w tabeli i zamiast tego są dołączane do istniejącej tabeli.  
  
## <a name="table-names-and-namespaces"></a>Nazwy tabel i przestrzenie nazw  
 <xref:System.Data.DataTable>Opcjonalnie można przypisać obiektów <xref:System.Data.DataTable.Namespace%2A> wartości właściwości. Gdy <xref:System.Data.DataTable.Namespace%2A> przypisywania wartości <xref:System.Data.DataSet> może zawierać wiele <xref:System.Data.DataTable> obiektów z takimi samymi <xref:System.Data.DataTable.TableName%2A> wartość. Podczas operacji scalania zarówno <xref:System.Data.DataTable.TableName%2A> i <xref:System.Data.DataTable.Namespace%2A> są używane do identyfikowania element docelowy scalania. Jeśli nie <xref:System.Data.DataTable.Namespace%2A> przypisano, tylko <xref:System.Data.DataTable.TableName%2A> służy do identyfikowania element docelowy scalania.  
  
> [!NOTE]
>  To zachowanie, zmiany w wersji 2.0 programu .NET Framework. W wersji 1.1 przestrzenie nazw są obsługiwane, ale zostały zignorowane podczas operacji scalania. Z tego powodu <xref:System.Data.DataSet> używającą <xref:System.Data.DataTable.Namespace%2A> wartości właściwości mają różne zachowania, w zależności od instalowanej wersji programu .NET Framework są uruchomione. Załóżmy na przykład, jeśli masz dwa `DataSets` zawierający `DataTables` o takim samym <xref:System.Data.DataTable.TableName%2A> ale o innej wartości właściwości <xref:System.Data.DataTable.Namespace%2A> wartości właściwości. W wersji 1.1 programu .NET Framework różnych <xref:System.Data.DataTable.Namespace%2A> nazwy zostaną pominięte podczas scalania dwa <xref:System.Data.DataSet> obiektów. Jednak począwszy od wersji 2.0, scalanie powoduje, że dwa nowe `DataTables` ma zostać utworzony w celu <xref:System.Data.DataSet>. Oryginalna `DataTables` będą mieć wpływu na scalanie.  
  
## <a name="preservechanges"></a>PreserveChanges  
 Podczas przekazywania `DataSet`, `DataTable`, lub `DataRow` tablicy do `Merge` metody, można uwzględnić parametry opcjonalne, które określają, czy chcesz zachować zmiany w istniejących `DataSet`oraz sposób obsługi nowych elementów schematu znaleziono w danych przychodzących. Pierwsza z tych parametrów po danych przychodzących jest flaga wartości logicznej, <xref:System.Data.LoadOption.PreserveChanges>, który określa, czy chcesz zachować zmiany w istniejących `DataSet`. Jeśli `PreserveChanges` flaga jest ustawiona na `true`, wartości przychodzących nie zastępują istniejące wartości w `Current` wersji wierszy istniejącego wiersza. Jeśli `PreserveChanges` flaga jest ustawiona na `false`, wartości przychodzących zastąpić istniejące wartości w `Current` wersji wierszy istniejącego wiersza. Jeśli `PreserveChanges` flaga nie zostanie określony, jest równa `false` domyślnie. Aby uzyskać więcej informacji dotyczących wersji wierszy, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Gdy `PreserveChanges` jest `true`, dane z istniejącym wierszu są przechowywane w <xref:System.Data.DataRowVersion.Current> wersja wiersza z istniejącym wierszu danych z <xref:System.Data.DataRowVersion.Original> wersji wierszy istniejącego wiersza jest zastępowany przy użyciu danych z `Original` wiersza Wersja wiersza przychodzących. <xref:System.Data.DataRow.RowState%2A> Istniejącego wiersza jest ustawiony na wartość <xref:System.Data.DataRowState.Modified>. Zastosuj następujące wyjątki:  
  
-   Jeśli istniejący wiersz ma `RowState` z `Deleted`, to `RowState` pozostaje `Deleted` i nie jest ustawiony na `Modified`. W takim przypadku dane z przychodzącego wiersza, nadal będą przechowywane w `Original` wersja wiersza istniejącego wiersza zastępowanie `Original` wersji wierszy istniejącego wiersza (chyba że przychodzące wiersz ma `RowState` z `Added`).  
  
-   Jeśli wiersz ma `RowState` z `Added`, dane z `Original` wersji wierszy istniejącego wiersza nie zostaną zastąpione danymi z przychodzącego wiersza, ponieważ wiersz nie ma `Original` wersji wiersza.  
  
 Gdy `PreserveChanges` jest `false`, zarówno `Current` i `Original` wersji wierszy w istniejącym wierszu zostaną zastąpione danymi z przychodzącego wiersza i `RowState` istniejącego wiersza jest ustawiony na wartość `RowState` przychodzące wiersza. Zastosuj następujące wyjątki:  
  
-   Jeśli wiersz przychodzące ma `RowState` z `Unchanged` i istniejący wiersz ma `RowState` z `Modified`, `Deleted`, lub `Added`, `RowState` istniejącego wiersza jest ustawiony na wartość `Modified`.  
  
-   Jeśli wiersz przychodzące ma `RowState` z `Added`, a istniejący wiersz ma `RowState` z `Unchanged`, `Modified`, lub `Deleted`, `RowState` istniejącego wiersza jest ustawiony na wartość `Modified`. Ponadto dane z `Original` wersji wierszy istniejącego wiersza nie jest zastępowany dane z przychodzącego wiersza, ponieważ wiersz nie ma `Original` wersji wiersza.  
  
## <a name="missingschemaaction"></a>MissingSchemaAction  
 Można użyć opcjonalnego <xref:System.Data.MissingSchemaAction> parametr `Merge` metodę, aby określić sposób `Merge` obsłuży elementy schematu przychodzących danych, które nie są częścią istniejącej `DataSet`.  
  
 W poniższej tabeli opisano opcje `MissingSchemaAction`.  
  
|Opcja MissingSchemaAction|Opis|  
|--------------------------------|-----------------|  
|<xref:System.Data.MissingSchemaAction.Add>|Dodawanie nowych informacji o schemacie `DataSet` i wypełnić nowe kolumny przy użyciu wartości przychodzących. Domyślnie włączone.|  
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Dodawanie nowego schematu i informacje o kluczu podstawowym do `DataSet` i wypełnić nowe kolumny przy użyciu wartości przychodzących.|  
|<xref:System.Data.MissingSchemaAction.Error>|Zgłoś wyjątek, jeśli okaże się informacje o schemacie niezgodne.|  
|<xref:System.Data.MissingSchemaAction.Ignore>|Ignoruj nowych informacji o schemacie.|  
  
## <a name="constraints"></a>Ograniczenia  
 Z `Merge` metody ograniczenia nie są sprawdzane, dopóki wszystkie nowe dane zostały dodane do istniejącej `DataSet`. Po dodaniu danych na bieżące wartości wymuszone są ograniczenia `DataSet`. Należy się upewnić, że kod obsługuje wszystkie wyjątki, które może zostać zgłoszone z powodu naruszenia ograniczenia.  
  
 Rozważmy przykład w przypadku, gdy istniejący wiersz w `DataSet` jest `Unchanged` wiersza z wartości klucza podstawowego 1. Podczas operacji scalania z `Modified` wiersz z `Original` wartość klucza podstawowego 2 i `Current` wartość klucza podstawowego równą 1, istniejący wiersz i wiersz nie są uznawane za zgodnych, ponieważ `Original` wartości klucza podstawowego różnią się. Jednak po ukończeniu scalania i ograniczenia są zaznaczone, zostanie wygenerowany wyjątek ponieważ `Current` wartości kluczy podstawowych narusza ograniczenie unique dla kolumny klucza podstawowego.  
  
> [!NOTE]
>  Jeśli wiersze zostaną wstawione do tabeli bazy danych zawierające automatyczne zwiększanie kolumny, takich jak kolumny tożsamości, zwracane przez wstawienie wartości kolumny tożsamości mogą nie pasuje do wartości w `DataSet`, powodując zwrócone wiersze, które mają być dołączane zamiast scalone. Aby uzyskać więcej informacji, zobacz [pobierania tożsamości lub wartości automatycznie numerowane](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
 Poniższy przykład kodu scala dwie `DataSet` obiektów ze schematami differents do jednej `DataSet` z połączonych schematów dwóch przychodzących `DataSet` obiektów.  
  
 [!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]  
  
 Poniższy przykładowy kod ma istniejące `DataSet` aktualizacje i przekazuje te aktualizacje `DataAdapter` do przetworzenia w źródle danych. Wyniki są następnie scalane w oryginalnym `DataSet`. Po odrzuceniu zmian, które spowodowały błąd, są zatwierdzone z zmiany scalone `AcceptChanges`.  
  
 [!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]  
  
 [!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
 [!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [Elementy DataAdapter i DataReaders](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Pobieranie tożsamości lub wartości automatycznych numerów](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
