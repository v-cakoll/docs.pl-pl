---
title: Scalanie zawartości elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: abc9183666602a7ef369e690e3ae499f8c7b8b11
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784396"
---
# <a name="merging-dataset-contents"></a>Scalanie zawartości elementu DataSet

<xref:System.Data.DataSet.Merge%2A> Możesz użyć `DataSet`metody <xref:System.Data.DataSet>, aby scalić zawartość tablicy, <xref:System.Data.DataTable>lub <xref:System.Data.DataRow> do istniejącej. Kilka czynników i opcji mają wpływ na sposób scalania nowych danych w istniejący `DataSet`.

## <a name="primary-keys"></a>Klucze podstawowe

Jeśli tabela otrzymująca nowe dane i schemat z scalania ma klucz podstawowy, nowe wiersze z danych przychodzących są dopasowywane do istniejących wierszy, które mają te same <xref:System.Data.DataRowVersion.Original> wartości klucza podstawowego co te w danych przychodzących. Jeśli kolumny ze schematu przychodzącego są zgodne z istniejącymi schematami, dane w istniejących wierszach są modyfikowane. Kolumny, które nie pasują do istniejącego schematu, są ignorowane lub dodawane na podstawie <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametru. Nowe wiersze z wartościami klucza podstawowego, które nie są zgodne z żadnymi istniejącymi wierszami, są dołączane do istniejącej tabeli.

Jeśli przychodzące lub istniejące <xref:System.Data.DataRowState.Added>wiersze mają stan wiersza, ich wartości klucza podstawowego są dopasowywane <xref:System.Data.DataRowVersion.Current> przy użyciu wartości klucza `Added` podstawowego wiersza, ponieważ nie `Original` istnieje wersja wiersza.

Jeśli tabela przychodząca i istniejąca tabela zawierają kolumnę o tej samej nazwie, ale różne typy danych, zgłaszany jest wyjątek, <xref:System.Data.DataSet.MergeFailed> a zdarzenie `DataSet` jest wywoływane. Jeśli tabela przychodząca i istniejąca tabela mają zdefiniowane klucze, ale klucze podstawowe są dla różnych kolumn, zgłaszany jest wyjątek, a `MergeFailed` zdarzenie `DataSet` jest wywoływane.

Jeśli tabela otrzymująca nowe dane z scalania nie ma klucza podstawowego, nie można dopasować nowych wierszy z danych przychodzących do istniejących wierszy w tabeli i są one dołączane do istniejącej tabeli.

## <a name="table-names-and-namespaces"></a>Nazwy tabel i przestrzenie nazw

<xref:System.Data.DataTable>do <xref:System.Data.DataTable.Namespace%2A> obiektów można opcjonalnie przypisać wartość właściwości. Gdy <xref:System.Data.DataTable.Namespace%2A> wartości są przypisane <xref:System.Data.DataSet> , może zawierać wiele <xref:System.Data.DataTable> obiektów o tej samej <xref:System.Data.DataTable.TableName%2A> wartości. Podczas operacji scalania zarówno <xref:System.Data.DataTable.TableName%2A> i <xref:System.Data.DataTable.Namespace%2A> są używane do identyfikowania celu scalania. Jeśli nie <xref:System.Data.DataTable.Namespace%2A> została przypisana, <xref:System.Data.DataTable.TableName%2A> tylko służy do identyfikowania celu scalania.

> [!NOTE]
> To zachowanie zostało zmienione w wersji 2,0 .NET Framework. W wersji 1,1, przestrzenie nazw były obsługiwane, ale zostały zignorowane podczas operacji scalania. Z tego powodu, <xref:System.Data.DataSet> który używa <xref:System.Data.DataTable.Namespace%2A> wartości właściwości, będzie mieć różne zachowania, w zależności od używanej wersji .NET Framework. Załóżmy na przykład, że masz `DataSets` dwie zawierające `DataTables` te same <xref:System.Data.DataTable.TableName%2A> wartości właściwości, ale różne <xref:System.Data.DataTable.Namespace%2A> wartości właściwości. W wersji 1,1 .NET Framework różne <xref:System.Data.DataTable.Namespace%2A> nazwy zostaną zignorowane podczas scalania dwóch <xref:System.Data.DataSet> obiektów. Jednak począwszy od wersji 2,0, scalenia powoduje utworzenie dwóch `DataTables` nowych obiektów w celu. <xref:System.Data.DataSet> Scalanie `DataTables` nie wpłynie na oryginalne.

## <a name="preservechanges"></a>PreserveChanges

`DataSet`Gdy przekazujesz tablicę `DataTable`, `DataRow` `DataSet`, lub do metody, możesz dołączyć parametry opcjonalne, które określają, czy zachować zmiany w istniejącym i jak obsługiwać nowe elementy schematu `Merge` w danych przychodzących. Pierwszy z tych parametrów po danych przychodzących jest flagą logiczną, <xref:System.Data.LoadOption.PreserveChanges>która określa, czy zachować zmiany w istniejącym. `DataSet` Jeśli flaga jest ustawiona na `true`, wartości przychodzące nie `Current` zastępują istniejących wartości w wierszu wersji istniejącego wiersza. `PreserveChanges` Jeśli flaga jest ustawiona na `false`, wartości przychodzące zastępuje istniejące wartości w `Current` wierszu wersji istniejącego wiersza. `PreserveChanges` Jeśli flaga nie jest określona, jest domyślnie ustawiona na `false` wartość. `PreserveChanges` Aby uzyskać więcej informacji o wersjach wierszy, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).

Gdy `PreserveChanges` tak `true`jest, dane z istniejącego <xref:System.Data.DataRowVersion.Current> wiersza są zachowywane w wersji wiersza <xref:System.Data.DataRowVersion.Original> istniejącego wiersza, podczas gdy dane z wiersza wersji istniejącego wiersza są zastępowane danymi z `Original` wiersza wersja wiersza przychodzącego. Istniejący wiersz jest ustawiony na <xref:System.Data.DataRowState.Modified>. <xref:System.Data.DataRow.RowState%2A> Obowiązują następujące wyjątki:

- Jeśli istniejący wiersz `RowState` ma wartość `Deleted`, `RowState` pozostaje `Deleted` i nie jest ustawiony na `Modified`. W takim przypadku dane `Original` z przychodzącego wiersza będą nadal przechowywane w wersji wiersza istniejącego wiersza, `Original` zastępując wersję wiersza istniejącego wiersza (chyba że `Added`przychodzący wiersz ma wartość `RowState` ).

- Jeśli przychodzący wiersz zawiera `RowState` z `Added` `Original` , dane z wersji wiersza istniejącego wiersza nie zostaną zastąpione danymi z wiersza przychodzącego, `Original` ponieważ w wierszu przychodzącym nie ma wersji wiersza.

Gdy `PreserveChanges` ma `Original` `Current` `RowState` `RowState` wartość, zarówno wersje wierszy, jak i w istniejącym wierszu są zastępowane danymi z wiersza przychodzącego, a istniejący wiersz jest ustawiony na wiersz przychodzący. `false` Obowiązują następujące wyjątki:

- Jeśli przychodzący wiersz ma `RowState` `Unchanged` a i `Modified`istniejący wiersz ma `RowState` , `Deleted`, lub `Added`, w `RowState` istniejącym wierszu ma ustawioną wartość `Modified`.

- Jeśli wiersz przychodzący ma `RowState` wartość `Added`, a `Unchanged`istniejący wiersz ma `RowState` , `Modified`, lub `Deleted`, w `RowState` istniejącym wierszu jest ustawiony na `Modified`. Ponadto dane z `Original` wersji wiersza istniejącego wiersza nie są zastępowane danymi z wiersza przychodzącego, ponieważ w wierszu przychodzącym nie `Original` ma wersji wiersza.

## <a name="missingschemaaction"></a>MissingSchemaAction

Można użyć opcjonalnego <xref:System.Data.MissingSchemaAction> parametru metody, `Merge` aby określić, jak `Merge` program będzie obsługiwać elementy schematu w danych przychodzących, które nie są częścią istniejącej `DataSet`.

W poniższej tabeli opisano opcje dla programu `MissingSchemaAction`.

|MissingSchemaAction — opcja|Opis|
|--------------------------------|-----------------|
|<xref:System.Data.MissingSchemaAction.Add>|Dodaj nowe informacje o schemacie do `DataSet` i Wypełnij nowe kolumny wartościami przychodzącymi. Domyślnie włączone.|
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Dodaj nowy schemat i informacje o kluczu podstawowym do `DataSet` i Wypełnij nowe kolumny wartościami przychodzącymi.|
|<xref:System.Data.MissingSchemaAction.Error>|Zgłoś wyjątek, Jeśli napotkano niezgodne informacje o schemacie.|
|<xref:System.Data.MissingSchemaAction.Ignore>|Ignoruj nowe informacje o schemacie.|

## <a name="constraints"></a>Ograniczenia

Przy użyciu `DataSet`metody ograniczenia nie są sprawdzane, dopóki wszystkie nowe dane nie zostaną dodane do istniejącej. `Merge` Po dodaniu danych ograniczenia są wymuszane na bieżących wartościach w `DataSet`. Musisz się upewnić, że kod obsługuje wszystkie wyjątki, które mogą być zgłaszane z powodu naruszeń ograniczenia.

Rozważ przypadek, w którym istniejący wiersz w a `DataSet` `Unchanged` jest wiersz z wartością klucza podstawowego 1. Podczas `Modified` operacji scalania z wierszem przychodzącym `Original` z `Current` wartością klucza podstawowego 2 i wartością klucza podstawowego 1, istniejący wiersz i wiersz `Original` przychodzący nie są uważane za zgodne, ponieważ wartości klucza podstawowego różniącego. Jednak po zakończeniu scalania i sprawdzeniu ograniczeń zostanie zgłoszony wyjątek, ponieważ `Current` wartości klucza podstawowego naruszają unikatowe ograniczenie dla kolumny klucza podstawowego.

> [!NOTE]
> Gdy wiersze są wstawiane do tabeli bazy danych zawierającej kolumnę z autoprzyrostem, taką jak kolumna tożsamości, wartość kolumny tożsamości zwracana przez wstawianie może być niezgodna z wartością w `DataSet`, powodując dołączenie zwracanych wierszy zamiast scalonych. Aby uzyskać więcej informacji, zobacz [pobieranie tożsamości lub wartości AutoNumber](../retrieving-identity-or-autonumber-values.md).

Poniższy przykład kodu Scala dwa `DataSet` obiekty z różnymi schematami w jeden `DataSet` z połączonymi schematami dwóch obiektów przychodzących `DataSet` .

[!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]

Poniższy przykład kodu przyjmuje istniejące `DataSet` aktualizacje i przekazuje te aktualizacje do programu `DataAdapter` w celu ich przetworzenia w źródle danych. Następnie wyniki zostaną scalone z oryginałem `DataSet`. Po odrzuceniu zmian, które spowodowały błąd, scalone zmiany są zatwierdzane za `AcceptChanges`pomocą.

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](index.md)
- [Stany wiersza i wersje wiersza](row-states-and-row-versions.md)
- [Elementy DataAdapter i DataReaders](../dataadapters-and-datareaders.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../retrieving-and-modifying-data.md)
- [Pobieranie tożsamości lub wartości automatycznych numerów](../retrieving-identity-or-autonumber-values.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
