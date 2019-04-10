---
title: Obsługa zdarzeń elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: 414be4a5bdbd1fe5d65475efcd5e72606b73685f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312829"
---
# <a name="handling-datatable-events"></a>Obsługa zdarzeń elementu DataTable
<xref:System.Data.DataTable> Obiekt zawiera szereg zdarzeń, które mogą być przetwarzane przez aplikację. W poniższej tabeli opisano `DataTable` zdarzenia.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Występuje po <xref:System.Data.DataTable.EndInit%2A> metoda `DataTable` jest wywoływana. To zdarzenie jest przeznaczony głównie do obsługi scenariuszy w czasie projektowania.|  
|<xref:System.Data.DataTable.ColumnChanged>|Występuje po wartości po pomyślnej zmianie w <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Występuje, gdy wartość została przesłana do `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Występuje po `DataColumn` wartość lub <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRow> w `DataTable` zostało pomyślnie zmienione.|  
|<xref:System.Data.DataTable.RowChanging>|Występuje, gdy zmiana została przesłana do `DataColumn` wartość lub `RowState` z `DataRow` w `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Występuje po `DataRow` w `DataTable` została oznaczona jako `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Występuje przed `DataRow` w `DataTable` jest oznaczony jako `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Występuje po wywołaniu <xref:System.Data.DataTable.Clear%2A> metody `DataTable` został pomyślnie wyczyszczony co `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Występuje po `Clear` metoda jest wywoływana, lecz przed `Clear` rozpoczęciu operacji.|  
|<xref:System.Data.DataTable.TableNewRow>|Występuje po nową `DataRow` jest tworzony przez wywołanie `NewRow` metody `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Występuje, gdy `DataTable` jest `Disposed`. Odziedziczone po <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
>  Większość operacji, dodać lub usunąć wiersze, które nie wywołuj `ColumnChanged` i `ColumnChanging` zdarzenia. Jednak `ReadXml` wywoływanie metody `ColumnChanged` i `ColumnChanging` zdarzeń, chyba że `XmlReadMode` jest ustawiona na `DiffGram` lub została ustawiona na `Auto` po dokumentu XML odczytywanych `DiffGram`.  
  
> [!WARNING]
>  Może spowodować uszkodzenie danych, jeśli data zostanie zmodyfikowany w `DataSet` z którego `RowChanged` zdarzenie jest wywoływane. Żaden wyjątek nie zostanie wygenerowany, jeśli wystąpi takie uszkodzenie danych.  
  
## <a name="additional-related-events"></a>Dodatkowe zdarzenia pokrewne  
 <xref:System.Data.DataTable.Constraints%2A> Przechowuje właściwości <xref:System.Data.ConstraintCollection> wystąpienia. <xref:System.Data.ConstraintCollection> Klasy ujawnia <xref:System.Data.ConstraintCollection.CollectionChanged> zdarzeń. To zdarzenie jest uruchamiana, gdy dodane, zmodyfikowane lub usunięte z ograniczenie `ConstraintCollection`.  
  
 <xref:System.Data.DataTable.Columns%2A> Przechowuje właściwości <xref:System.Data.DataColumnCollection> wystąpienia. `DataColumnCollection` Klasy ujawnia <xref:System.Data.DataColumnCollection.CollectionChanged> zdarzeń. To zdarzenie jest uruchamiany, gdy `DataColumn` dodane, zmodyfikowane lub usunięte z `DataColumnCollection`. Modyfikacje, które powodują wyzwolenie zdarzenia obejmują zmiany nazwy, typu, wyrażenie lub porządkowym kolumny.  
  
 <xref:System.Data.DataSet.Tables%2A> Właściwość <xref:System.Data.DataSet> przechowuje <xref:System.Data.DataTableCollection> wystąpienia. `DataTableCollection` Klasa udostępnia zarówno `CollectionChanged` i `CollectionChanging` zdarzeń. Wyzwolenie tych zdarzeń, gdy `DataTable` jest dodane lub usunięte z `DataSet`.  
  
 Zmienia się na `DataRows` można również wyzwalać zdarzenia dla skojarzonego <xref:System.Data.DataView>. `DataView` Klasy ujawnia <xref:System.Data.DataView.ListChanged> zdarzeń, który jest uruchamiany, gdy `DataColumn` zmiany wartości lub podczas zmiany kompozycji i kolejność sortowania widoku. <xref:System.Data.DataRowView> Klasy ujawnia <xref:System.Data.DataRowView.PropertyChanged> zdarzenia, które są generowane, gdy skojarzony `DataColumn` wartość zmienia się.  
  
## <a name="sequence-of-operations"></a>Sekwencja operacji  
 Oto sekwencja operacji, które występują podczas `DataRow` dodane, zmodyfikowane lub usunięte:  
  
1. Utwórz rekord proponowanych i zastosować zmiany.  
  
2. Sprawdź ograniczenia w kolumnach-expression.  
  
3. Wywoływanie `RowChanging` lub `RowDeleting` zdarzeń, jeśli ma to zastosowanie.  
  
4. Ustaw proponowany rekord bieżącego rekordu.  
  
5. Zaktualizuj wszystkie indeksy.  
  
6. Wywoływanie `ListChanged` skojarzone zdarzenia dla `DataView` obiektów i `PropertyChanged` skojarzone zdarzenia dla `DataRowView` obiektów.  
  
7. Należy ocenić wszystkie kolumny wyrażenia, ale opóźnienie sprawdzanie żadnych ograniczeń na tych kolumnach.  
  
8. Wywoływanie `ListChanged` skojarzone zdarzenia dla `DataView` obiektów i `PropertyChanged` skojarzone zdarzenia dla `DataRowView` obiektów wpływ ocen kolumnę wyrażenia.  
  
9. Wywoływanie `RowChanged` lub `RowDeleted` zdarzeń, jeśli ma to zastosowanie.  
  
10. Sprawdź ograniczenia dotyczące wyrażeń kolumn.  
  
> [!NOTE]
>  Zmiany kolumn wyrażeń nigdy nie zgłaszać `DataTable` zdarzenia. Zmiany kolumn wyrażeń tylko zgłosić `DataView` i `DataRowView` zdarzenia. Kolumny wyrażeń może być zależny od wielu innych kolumn i mogą być obliczane wielokrotnie podczas jednego `DataRow` operacji. Każdej oceny wyrażenia wywołuje zdarzenia i jeden `DataRow` operacji można podnieść wielu `ListChanged` i `PropertyChanged` zdarzenia w przypadku kolumn wyrażeń one dotyczą, prawdopodobnie w tym wiele zdarzeń dla tej samej kolumny w wyrażeniu.  
  
> [!WARNING]
>  Nie zgłaszają wyjątków <xref:System.NullReferenceException> w ramach `RowChanged` programu obsługi zdarzeń. Jeśli <xref:System.NullReferenceException> zostanie zgłoszony w obrębie `RowChanged` zdarzenia `DataTable`, a następnie `DataTable` zostanie uszkodzony.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia procedury obsługi zdarzeń dla `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, i `TableClearing` zdarzenia. Każdy program obsługi zdarzeń wyświetla dane wyjściowe w oknie konsoli po jego wyzwoleniu.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Operowanie na danych w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [Obsługa zdarzeń elementu DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)
- [Obsługa zdarzeń elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
