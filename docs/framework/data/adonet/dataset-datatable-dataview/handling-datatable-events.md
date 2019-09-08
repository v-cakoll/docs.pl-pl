---
title: Obsługa zdarzeń elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: 3edafa6c6a1bc3da2abc0598f329caf0e2f21e8b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786254"
---
# <a name="handling-datatable-events"></a>Obsługa zdarzeń elementu DataTable
<xref:System.Data.DataTable> Obiekt zawiera serię zdarzeń, które mogą być przetwarzane przez aplikację. W poniższej tabeli opisano `DataTable` zdarzenia.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Występuje po <xref:System.Data.DataTable.EndInit%2A> wywołaniu metody `DataTable` klasy. To zdarzenie jest przeznaczone głównie do obsługi scenariuszy czasu projektowania.|  
|<xref:System.Data.DataTable.ColumnChanged>|Występuje po pomyślnej zmianie wartości w <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Występuje, gdy wartość zostanie przesłana dla elementu `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Występuje po `DataColumn` pomyślnym zmianie <xref:System.Data.DataRow.RowState%2A> wartości lub <xref:System.Data.DataRow> elementu w `DataTable` .|  
|<xref:System.Data.DataTable.RowChanging>|Występuje, gdy `DataColumn` została przesłana zmiana dotycząca wartości `RowState` lub z `DataRow` w `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Występuje po oznaczeniu `DataRow` elementu `DataTable` w elemencie jako `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Występuje przed oznaczeniem `DataRow` `DataTable` elementu w `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Występuje po pomyślnym wyczyszczeniu <xref:System.Data.DataTable.Clear%2A> `DataRow`wywołania metody `DataTable` .|  
|<xref:System.Data.DataTable.TableClearing>|Występuje po wywołaniu `Clear` metody, ale `Clear` przed rozpoczęciem operacji.|  
|<xref:System.Data.DataTable.TableNewRow>|Występuje po utworzeniu nowej `DataRow` przez wywołanie `NewRow` metody `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Występuje, `DataTable` gdy jest `Disposed`. Dziedziczone z <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
> Większość operacji, które dodają lub usuwają wiersze, `ColumnChanged` nie `ColumnChanging` powodują zdarzeń i. `ColumnChanged` `ColumnChanging` `Auto` `DiffGram` `DiffGram`Jednak metoda wykonuje podnoszenie`XmlReadMode` i zdarzenia, chyba że jest ustawiona na lub jest ustawiona na, gdy dokument XML jest odczytywany. `ReadXml`  
  
> [!WARNING]
> Uszkodzenie danych może wystąpić, `DataSet` `RowChanged` Jeśli dane są modyfikowane w przypadku, gdy zdarzenie jest zgłaszane. Wyjątek nie zostanie zgłoszony, jeśli wystąpi takie uszkodzenie danych.  
  
## <a name="additional-related-events"></a>Dodatkowe powiązane zdarzenia  
 <xref:System.Data.DataTable.Constraints%2A> Właściwość<xref:System.Data.ConstraintCollection> przechowuje wystąpienie. <xref:System.Data.ConstraintCollection> Klasa<xref:System.Data.ConstraintCollection.CollectionChanged> ujawnia zdarzenie. To zdarzenie jest wyzwalane, gdy ograniczenie zostanie dodane, zmodyfikowane lub usunięte z `ConstraintCollection`.  
  
 <xref:System.Data.DataTable.Columns%2A> Właściwość<xref:System.Data.DataColumnCollection> przechowuje wystąpienie. `DataColumnCollection` Klasa<xref:System.Data.DataColumnCollection.CollectionChanged> ujawnia zdarzenie. To zdarzenie jest wyzwalane `DataColumn` , gdy element jest dodawany, modyfikowany lub `DataColumnCollection`usuwany z. Modyfikacje, które powodują pożar zdarzenia, obejmują zmiany nazwy, typu, wyrażenia lub liczby porządkowej kolumny.  
  
 <xref:System.Data.DataSet.Tables%2A> Właściwość obiektu<xref:System.Data.DataTableCollection> zawiera wystąpienie. <xref:System.Data.DataSet> Klasa uwidacznia `CollectionChanging` zarówno zdarzenie `CollectionChanged` `DataTableCollection` , jak i. Te zdarzenia `DataTable` są wyzwalane po dodaniu lub usunięciu `DataSet`z.  
  
 Zmiany w `DataRows` usłudze mogą również wyzwalać zdarzenia dla <xref:System.Data.DataView>skojarzonego elementu. `DataView` Klasa uwidacznia`DataColumn` zdarzenie, które jest wyzwalane, gdy wartość ulegnie zmianie lub gdy zmieni się kompozycja lub porządek sortowania widoku. <xref:System.Data.DataView.ListChanged> Klasa uwidacznia zdarzenie, które jest wyzwalane, gdy `DataColumn` zostanie zmieniona skojarzona wartość. <xref:System.Data.DataRowView.PropertyChanged> <xref:System.Data.DataRowView>  
  
## <a name="sequence-of-operations"></a>Sekwencja operacji  
 Oto sekwencja operacji, które wystąpiły po `DataRow` dodaniu, zmodyfikowaniu lub usunięciu:  
  
1. Utwórz proponowany rekord i Zastosuj wszelkie zmiany.  
  
2. Ograniczenia check dla kolumn niebędących wyrażeniami wyrażeń.  
  
3. Zgłoś odpowiednie zdarzenia `RowDeleting`lub. `RowChanging`  
  
4. Ustaw proponowany rekord jako bieżący rekord.  
  
5. Aktualizowanie wszystkich skojarzonych indeksów.  
  
6. Zgłoś `ListChanged` zdarzenia dla skojarzonych `DataView` obiektów i `PropertyChanged` zdarzeń dla skojarzonych `DataRowView` obiektów.  
  
7. Oceń wszystkie kolumny wyrażeń, ale Opóźnij sprawdzanie ograniczeń dotyczących tych kolumn.  
  
8. Wywołaj `ListChanged` zdarzenia dla `DataView` skojarzonych obiektów `PropertyChanged` i zdarzeń dla `DataRowView` skojarzonych obiektów, na które mają wpływ oceny kolumn wyrażeń.  
  
9. `RowChanged` Podnieś `RowDeleted` lub zgłoś odpowiednie zdarzenia.  
  
10. Ograniczenia check dla kolumn wyrażeń.  
  
> [!NOTE]
> Zmiany w kolumnach wyrażeń nigdy nie `DataTable` powodują zdarzeń. Zmiany w kolumnach wyrażeń powodują `DataView` podnoszenie `DataRowView` i zdarzenia. Kolumny wyrażeń mogą mieć zależności dla wielu innych kolumn i mogą być oceniane wiele razy podczas jednej `DataRow` operacji. Każde obliczenie wyrażenia wywołuje zdarzenia, a pojedyncza `DataRow` operacja może spowodować wygenerowanie `PropertyChanged` wielu `ListChanged` i zdarzeń w przypadku, gdy dotyczy kolumn wyrażeń, może także uwzględniać wiele zdarzeń dla tej samej kolumny wyrażenia.  
  
> [!WARNING]
> Nie <xref:System.NullReferenceException> zgłaszaj `RowChanged` w ramach procedury obsługi zdarzeń. Jeśli jest zgłaszany `RowChanged` w ramach zdarzenia `DataTable`, `DataTable` zostanie uszkodzona. <xref:System.NullReferenceException>  
  
### <a name="example"></a>Przykład  
 Poniższy `RowChanged`przykład ilustruje sposób tworzenia obsługi zdarzeń dla zdarzeń `ColumnChanged` `RowDeleting` `RowDeleted` `RowChanging` ,`ColumnChanging`,,,,,, i `TableClearing`. `TableNewRow` `TableCleared` Każdy program obsługi zdarzeń wyświetla dane wyjściowe w oknie konsoli, gdy jest on uruchamiany.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Operowanie danymi w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [Obsługa zdarzeń elementu DataAdapter](../handling-dataadapter-events.md)
- [Obsługa zdarzeń elementu DataSet](handling-dataset-events.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
