---
title: "Obsługa zdarzeń DataTable"
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
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c67fe25e405b81b3e48aa861dc4d6af837835226
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="handling-datatable-events"></a>Obsługa zdarzeń DataTable
<xref:System.Data.DataTable> Obiekt zapewnia szereg zdarzeń, które mogą być przetwarzane przez aplikację. W poniższej tabeli opisano `DataTable` zdarzenia.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Występuje po <xref:System.Data.DataTable.EndInit%2A> metoda `DataTable` jest wywoływana. To zdarzenie jest przeznaczony głównie w celu obsługi scenariuszy, w czasie projektowania.|  
|<xref:System.Data.DataTable.ColumnChanged>|Występuje po pomyślnie zmieniono wartość w <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Występuje, gdy wartość została przesłana do `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Występuje po `DataColumn` wartość lub <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRow> w `DataTable` został pomyślnie zmieniony.|  
|<xref:System.Data.DataTable.RowChanging>|Występuje, gdy zmiana została przesłana do `DataColumn` wartość lub `RowState` z `DataRow` w `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Występuje po `DataRow` w `DataTable` została oznaczona jako `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Występuje przed `DataRow` w `DataTable` jest oznaczony jako `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Występuje po wywołaniu <xref:System.Data.DataTable.Clear%2A> metody `DataTable` została wyczyszczona co `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Występuje po `Clear` metodę wywoływaną, ale przed wysłaniem `Clear` rozpocznie się wykonywanie operacji.|  
|<xref:System.Data.DataTable.TableNewRow>|Występuje po nowy `DataRow` jest utworzona przez wywołanie do `NewRow` metody `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Występuje, gdy `DataTable` jest `Disposed`. Dziedziczone z <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
>  Nie wywołuj większości operacje dodawania i usuwania wierszy `ColumnChanged` i `ColumnChanging` zdarzenia. Jednak `ReadXml` wywoływanie metody `ColumnChanged` i `ColumnChanging` zdarzeń, chyba że `XmlReadMode` ustawiono `DiffGram` lub `Auto` podczas odczytu dokumentu XML jest `DiffGram`.  
  
> [!WARNING]
>  Może spowodować uszkodzenie danych, jeśli dane są modyfikowane w `DataSet` z którego `RowChanged` zdarzenia. Wyjątek nie zostanie wygenerowany, jeśli takie uszkodzenie danych.  
  
## <a name="additional-related-events"></a>Dodatkowe zdarzenia pokrewne  
 <xref:System.Data.DataTable.Constraints%2A> Blokad właściwości <xref:System.Data.ConstraintCollection> wystąpienia. <xref:System.Data.ConstraintCollection> Klasy ujawnia <xref:System.Data.ConstraintCollection.CollectionChanged> zdarzeń. To zdarzenie jest generowane podczas dodane, zmodyfikowane lub usunięte z ograniczeniem `ConstraintCollection`.  
  
 <xref:System.Data.DataTable.Columns%2A> Blokad właściwości <xref:System.Data.DataColumnCollection> wystąpienia. `DataColumnCollection` Klasy ujawnia <xref:System.Data.DataColumnCollection.CollectionChanged> zdarzeń. To zdarzenie uruchamiane w przypadku `DataColumn` dodane, zmodyfikowane lub usunięte z `DataColumnCollection`. Zmiany, które powodują wyzwolenie zdarzenia obejmują zmiany nazwy, typu, wyrażenie lub porządkowym kolumny.  
  
 <xref:System.Data.DataSet.Tables%2A> Właściwość <xref:System.Data.DataSet> przechowuje <xref:System.Data.DataTableCollection> wystąpienia. `DataTableCollection` Klasa udostępnia zarówno `CollectionChanged` i `CollectionChanging` zdarzeń. Wyzwalać te zdarzenia, kiedy `DataTable` zostanie dodany do lub usunięty z `DataSet`.  
  
 Zmienia się na `DataRows` może także wyzwolić skojarzonego zdarzenia <xref:System.Data.DataView>. `DataView` Klasy ujawnia <xref:System.Data.DataView.ListChanged> zdarzenie, które są uruchamiane w przypadku `DataColumn` zmiany wartości lub zmiany kompozycji i kolejność sortowania widoku. <xref:System.Data.DataRowView> Klasy ujawnia <xref:System.Data.DataRowView.PropertyChanged> zdarzenie, które są generowane, gdy skojarzony `DataColumn` wartość zmienia się.  
  
## <a name="sequence-of-operations"></a>Sekwencja operacji  
 Poniżej przedstawiono kolejność operacji, które występują po `DataRow` dodane, zmodyfikowane lub usunięte:  
  
1.  Utwórz rekord proponowanych i zastosować zmiany.  
  
2.  Sprawdź ograniczenia dla kolumny z systemem innym niż wyrażeń.  
  
3.  Zgłoś `RowChanging` lub `RowDeleting` zdarzeń zgodnie z wymaganiami.  
  
4.  Ustaw proponowanych rekordu dla bieżącego rekordu.  
  
5.  Zaktualizuj wszystkie indeksy.  
  
6.  Zgłoś `ListChanged` skojarzonego zdarzenia `DataView` obiektów i `PropertyChanged` skojarzonego zdarzenia `DataRowView` obiektów.  
  
7.  Należy ocenić wszystkie wyrażenia kolumny, ale opóźnienie sprawdzanie ograniczeń na tych kolumnach.  
  
8.  Zgłoś `ListChanged` skojarzonego zdarzenia `DataView` obiektów i `PropertyChanged` skojarzonego zdarzenia `DataRowView` obiektów dotyczy oceny kolumny wyrażenia.  
  
9. Zgłoś `RowChanged` lub `RowDeleted` zdarzeń zgodnie z wymaganiami.  
  
10. Sprawdź ograniczenia dla kolumny wyrażenia.  
  
> [!NOTE]
>  Zmiany w wyrażeniu kolumny nigdy nie podnieść `DataTable` zdarzenia. Zmiany w wyrażeniu kolumny tylko podnieść `DataView` i `DataRowView` zdarzenia. Wyrażenie kolumny może być zależny od wielu innych kolumn i może przyjąć wiele razy podczas pojedynczy `DataRow` operacji. Każdej oceny wyrażenie wywołuje zdarzenia i jeden `DataRow` operacji może wiązać się z wielu `ListChanged` i `PropertyChanged` zdarzenia, gdy wyrażenie kolumny jest narażony, może obejmować wiele zdarzeń dla tej samej kolumny wyrażenia.  
  
> [!WARNING]
>  Nie zgłaszają <xref:System.NullReferenceException> w ramach `RowChanged` programu obsługi zdarzeń. Jeśli <xref:System.NullReferenceException> jest zgłaszany w `RowChanged` zdarzenie `DataTable`, a następnie `DataTable` zostanie uszkodzony.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano tworzenie obsługi zdarzeń `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, i `TableClearing` zdarzenia. Każdy program obsługi zdarzeń wyświetla dane wyjściowe w oknie konsoli, gdy jest on uruchamiany.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie danymi w DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Obsługa zdarzeń element DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [Obsługa zdarzeń zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
