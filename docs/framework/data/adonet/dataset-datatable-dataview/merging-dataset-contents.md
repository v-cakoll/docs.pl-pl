---
title: Scalanie zawartości elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: 153c96860005046e4cc16d5a965bd569e3519b52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607933"
---
# <a name="merging-dataset-contents"></a>Scalanie zawartości elementu DataSet

Możesz użyć <xref:System.Data.DataSet.Merge%2A> metodę, aby scalić zawartość <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow> tablicę do istniejącego `DataSet`. Kilka czynników, jak i opcje mają wpływ na sposób nowe dane są scalane w istniejącej `DataSet`.

## <a name="primary-keys"></a>Klucze podstawowe

Jeśli tabela odbieranie nowych danych i schemat z scalanie ma klucz podstawowy, nowych wierszy dane przychodzące są dopasowywane do istniejące wiersze, które mają taki sam <xref:System.Data.DataRowVersion.Original> klucz podstawowy wartości zgodnie z programami znajdującymi się na dane przychodzące. Jeśli kolumny z przychodzącego schematu pasują do właściwości istniejącego schematu, danych w istniejących wierszy jest modyfikowany. Kolumny, które nie pasują do istniejącego schematu są ignorowane lub dodawane na podstawie <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametru. Nowe wiersze z wartości klucza podstawowego, które nie pasują jakiekolwiek istniejące wiersze są dołączane do istniejącej tabeli.

Jeśli przychodzących lub istniejące wiersze mają stan wiersza <xref:System.Data.DataRowState.Added>, ich wartości klucza podstawowego są dopasowywane przy użyciu <xref:System.Data.DataRowVersion.Current> wartość klucza podstawowego `Added` wiersza, ponieważ nie `Original` istnieje wersja wiersza.

Jeśli tabeli usługi w przychodzących i istniejącej tabeli zawiera kolumnę o tej samej nazwie, ale różnych typów danych, jest zgłaszany wyjątek i <xref:System.Data.DataSet.MergeFailed> zdarzenia `DataSet` jest wywoływane. Jeśli tabeli usługi w przychodzących i istniejącej tabeli zdefiniowano kluczy, ale klucze podstawowe są dla różnych kolumn, zwracany jest wyjątek i `MergeFailed` zdarzenia `DataSet` jest wywoływane.

Jeśli tabela otrzymuje nowych danych z scalania nie ma klucza podstawowego, nowych wierszy z przychodzących danych nie można dopasować do istniejące wiersze w tabeli i zamiast tego są dołączane do istniejącej tabeli.

## <a name="table-names-and-namespaces"></a>Nazwy tabel i przestrzenie nazw

<xref:System.Data.DataTable> Opcjonalnie można przypisać obiektów <xref:System.Data.DataTable.Namespace%2A> wartości właściwości. Gdy <xref:System.Data.DataTable.Namespace%2A> wartości są przypisywane, <xref:System.Data.DataSet> może zawierać więcej niż jednego <xref:System.Data.DataTable> obiekty o takiej samej <xref:System.Data.DataTable.TableName%2A> wartość. Podczas operacji scalanie zarówno <xref:System.Data.DataTable.TableName%2A> i <xref:System.Data.DataTable.Namespace%2A> są używane do identyfikowania element docelowy scalania. Jeśli nie <xref:System.Data.DataTable.Namespace%2A> został przypisany, tylko <xref:System.Data.DataTable.TableName%2A> służy do identyfikowania element docelowy scalania.

> [!NOTE]
> To zachowanie, zmiany w wersji 2.0 programu .NET Framework. W wersji 1.1 przestrzenie nazw były obsługiwane, ale zostały zignorowane podczas wykonywania operacji scalania. Z tego powodu <xref:System.Data.DataSet> , który używa <xref:System.Data.DataTable.Namespace%2A> wartości właściwości mają różne zachowania, w zależności od instalowanej wersji programu .NET Framework są uruchomione. Załóżmy, że masz dwa `DataSets` zawierający `DataTables` o takiej samej <xref:System.Data.DataTable.TableName%2A> ale o innej wartości właściwości <xref:System.Data.DataTable.Namespace%2A> wartości właściwości. W wersji 1.1 programu .NET Framework, poszczególne <xref:System.Data.DataTable.Namespace%2A> nazwy zostaną zignorowane podczas scalania dwóch <xref:System.Data.DataSet> obiektów. Jednak począwszy od wersji 2.0, scalanie powoduje, że dwa nowe `DataTables` zostały utworzone w docelowej <xref:System.Data.DataSet>. Oryginalny `DataTables` będą mieć wpływu na scalania.

## <a name="preservechanges"></a>PreserveChanges

Podczas przekazywania `DataSet`, `DataTable`, lub `DataRow` tablicy do `Merge` metody może zawierać parametrów opcjonalnych, które określają, czy chcesz zachować zmiany w istniejącym `DataSet`i sposób obsługi nowych elementów schematu, znaleziono w danych przychodzących. Pierwsza z tych parametrów po dane przychodzące są flagę logiczną <xref:System.Data.LoadOption.PreserveChanges>, która określa, czy chcesz zachować zmiany w istniejącym `DataSet`. Jeśli `PreserveChanges` flaga jest ustawiona na `true`, wartości przychodzących nie zastępuj istniejących wartości `Current` wiersza wersji istniejącego wiersza. Jeśli `PreserveChanges` flaga jest ustawiona na `false`, wartości przychodzących zastępuj istniejących wartości w `Current` wiersza wersji istniejącego wiersza. Jeśli `PreserveChanges` flaga nie zostanie określona, jest równa `false` domyślnie. Aby uzyskać więcej informacji na temat wersji wierszy, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).

Gdy `PreserveChanges` jest `true`, danych z istniejącego wiersza jest zachowywany w <xref:System.Data.DataRowVersion.Current> wiersz wersję istniejący wiersz, podczas dane z <xref:System.Data.DataRowVersion.Original> istniejący wiersz w wersji wiersza jest zastępowany przy użyciu danych z `Original` wiersza Wersja wiersza przychodzących. <xref:System.Data.DataRow.RowState%2A> Istniejący wiersz został ustawiony na <xref:System.Data.DataRowState.Modified>. Stosuje się następujące wyjątki:

- Jeśli istniejący wiersz ma `RowState` z `Deleted`ten `RowState` pozostaje `Deleted` i nie jest ustawiony na `Modified`. W tym przypadku danych z przychodzącego wiersza, nadal będą przechowywane w `Original` istniejący wiersz w wersji wiersza zastępowanie `Original` istniejący wiersz w wersji wiersza (chyba że przychodzących wiersz zawiera `RowState` z `Added`).

- Jeśli wiersz zawiera `RowState` z `Added`, dane z `Original` istniejący wiersz w wersji wiersza nie zostaną zastąpione przy użyciu danych z przychodzącego wiersza, ponieważ wiersz nie ma `Original` wiersza wersji.

Gdy `PreserveChanges` jest `false`, zarówno `Current` i `Original` wersje wiersza w istniejącym wierszu zostaną zastąpione danymi z przychodzącego wiersza i `RowState` istniejący wiersz został ustawiony na `RowState` przychodzących wiersza. Stosuje się następujące wyjątki:

- Jeśli wiersz zawiera `RowState` z `Unchanged` i istniejący wiersz ma `RowState` z `Modified`, `Deleted`, lub `Added`, `RowState` istniejący wiersz został ustawiony na `Modified`.

- Jeśli wiersz zawiera `RowState` z `Added`, a istniejący wiersz ma `RowState` z `Unchanged`, `Modified`, lub `Deleted`, `RowState` istniejący wiersz został ustawiony na `Modified`. Ponadto dane z `Original` istniejący wiersz w wersji wiersza nie jest zastępowany przy użyciu danych z przychodzącego wiersza, ponieważ wiersz nie ma `Original` wiersza wersji.

## <a name="missingschemaaction"></a>MissingSchemaAction

Możesz użyć opcjonalnego <xref:System.Data.MissingSchemaAction> parametru `Merge` metodę, aby określić sposób `Merge` będzie obsługiwać elementy schematu danych przychodzących, które nie są częścią istniejącej `DataSet`.

W poniższej tabeli opisano opcje `MissingSchemaAction`.

|Opcja MissingSchemaAction|Opis|
|--------------------------------|-----------------|
|<xref:System.Data.MissingSchemaAction.Add>|Dodanie nowych informacji o schemacie do `DataSet` i wypełnić nowe kolumny przy użyciu wartości przychodzących. Domyślnie włączone.|
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Dodawanie nowego schematu i informacje o kluczu podstawowym do `DataSet` i wypełnić nowe kolumny przy użyciu wartości przychodzących.|
|<xref:System.Data.MissingSchemaAction.Error>|Zgłoś wyjątek, jeśli okaże się, informacje o schemacie niezgodne.|
|<xref:System.Data.MissingSchemaAction.Ignore>|Ignoruj nowych informacji o schemacie.|

## <a name="constraints"></a>Ograniczenia

Za pomocą `Merge` metody ograniczenia nie są sprawdzane, dopóki wszystkie nowe dane zostały dodane do istniejących `DataSet`. Po dodaniu danych ograniczenia są wymuszane na bieżące wartości `DataSet`. Należy się upewnić, że kod obsługuje wszystkie wyjątki, które mogą być generowane z powodu naruszenia ograniczenia.

Należy rozważyć przypadek, w przypadku, gdy istniejący wiersz w `DataSet` jest `Unchanged` wiersz mający wartość klucza podstawowego 1. Podczas operacji scalania z `Modified` wiersz z `Original` wartość klucza podstawowego 2 i `Current` wartość klucza podstawowego, 1, istniejący wiersz i wiersz nie są uważane za dopasowanie, ponieważ `Original` wartości klucza podstawowego różnią się. Jednak po ukończeniu scalania i ograniczenia są sprawdzane, zostanie zgłoszony wyjątek ponieważ `Current` wartości klucza podstawowego narusza unikatowe ograniczenie dla kolumny klucza podstawowego.

> [!NOTE]
> Gdy wiersze zostały wstawione do tabeli bazy danych zawierająca automatycznego przyrostu o wartości kolumny, takie jak kolumny tożsamości, wartości kolumny tożsamości, które są zwracane przez Wstaw mogą być niezgodne wartości w `DataSet`, powodując zwrócone wiersze, które mają być dołączane zamiast scalone. Aby uzyskać więcej informacji, zobacz [pobieranie tożsamości lub wartości automatycznych numerów](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).

Poniższy przykład kodu scala dwa `DataSet` obiektów z różnymi schematami w jednej `DataSet` za pomocą połączonego schematów dwóch przychodzących `DataSet` obiektów.

[!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]

Poniższy przykładowy kod pobiera istniejący `DataSet` aktualizacje i przekazuje te aktualizacje `DataAdapter` mają być przetwarzane w źródle danych. Wyniki są następnie scalane w oryginalnym `DataSet`. Po odrzuceniu zmian, które spowodowały błąd, scalone zmiany są zatwierdzone z `AcceptChanges`.

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)
- [Elementy DataAdapter i DataReaders](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Pobieranie tożsamości lub wartości automatycznych numerów](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
