---
title: Elementy DataSet, DataTable i DataView
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 9c57f75dd94f3fbda74c13a5d5773825051fe416
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034297"
---
# <a name="datasets-datatables-and-dataviews"></a>Elementy DataSet, DataTable i DataView
ADO.NET <xref:System.Data.DataSet> jest reprezentacją rezydentnego zapewnia spójny model programowania relacyjnych niezależnie od źródła danych zawiera dane. A <xref:System.Data.DataSet> przedstawia kompletny zestaw danych w tym tabel, które zawierają, kolejność i Zachowaj dane, jak również relacje między tabelami.  
  
 Istnieją różne sposoby pracy z <xref:System.Data.DataSet>, które można stosować niezależnie lub razem. Można:  
  
- Programowe tworzenie <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, i <xref:System.Data.Constraint> w ramach <xref:System.Data.DataSet> i wypełnianie tabel danymi.  
  
- Wypełnij <xref:System.Data.DataSet> z tabelami danych z istniejącego relacyjne źródła danych przy użyciu `DataAdapter`.  
  
- Ładowanie i zachować <xref:System.Data.DataSet> zawartości za pomocą języka XML. Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
 Silnie typizowane <xref:System.Data.DataSet> również mogą być transportowane przy użyciu usługi sieci Web XML. Projekt <xref:System.Data.DataSet> to idealny do transportowania danych przy użyciu usług XML sieci Web. Aby uzyskać omówienie usług XML sieci Web, zobacz [Omówienie usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)). Na przykład używania <xref:System.Data.DataSet> z usługi sieci Web XML, zobacz [korzystanie z zestawu danych z usługi sieci Web XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 W tym artykule opisano Składnia służąca do tworzenia wystąpienia obiektu <xref:System.Data.DataSet>.  
  
 [Dodawanie elementu DataTable do elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 W tym artykule opisano sposób tworzenia i dodawanie tabel i kolumn do <xref:System.Data.DataSet>.  
  
 [Dodawanie elementów DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 W tym artykule opisano sposób tworzenia relacji między tabelami w <xref:System.Data.DataSet>.  
  
 [Nawigowanie w elementach DataRelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 Opisuje sposób używania relacje między tabelami w <xref:System.Data.DataSet> do zwrócenia wierszy podrzędnej lub nadrzędnej relacji nadrzędny podrzędny.  
  
 [Scalanie zawartości elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 W tym artykule opisano sposób scalania zawartość jednej <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow> tablicy do innej <xref:System.Data.DataSet>.  
  
 [Kopiowanie zawartości elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 W tym artykule opisano sposób tworzenia kopii <xref:System.Data.DataSet> zawierających schemat, a także określonych danych.  
  
 [Obsługa zdarzeń elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 W tym artykule opisano zdarzeń <xref:System.Data.DataSet> i sposobu ich używania.  
  
 [Typizowane elementy DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 W tym artykule omówiono jakie wpisane <xref:System.Data.DataSet> jest i jak tworzyć i używać go.  
  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 W tym artykule opisano sposób tworzenia <xref:System.Data.DataTable>, zdefiniować schemat i manipulowania danymi.  
  
 [Elementy DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 Opisuje sposób tworzenia i używania <xref:System.Data.DataTableReader>.  
  
 [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 W tym artykule opisano sposób tworzenia i pracy z `DataViews` i pracować z <xref:System.Data.DataView> zdarzenia.  
  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 W tym artykule opisano sposób, w jaki <xref:System.Data.DataSet> wchodzi w interakcję z danymi XML jako źródła danych, w tym ładowanie i przechowywanie zawartości <xref:System.Data.DataSet> jako danych XML.  
  
 [Korzystanie z elementu DataSet w usłudze internetowej XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 W tym artykule opisano sposób tworzenia usługi XML sieci Web, która używa <xref:System.Data.DataSet> transportu danych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Nowości w programie ADO.NET](../../../../../docs/framework/data/adonet/whats-new.md)  
 Dodano funkcje, które są nowością w programie ADO.NET.  
  
 [Omówienie ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Wprowadzenie do projektowania i składników programu ADO.NET.  
  
 [Wypełnianie zestawu danych z elementu DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Zawiera opis sposobu ładowania **DataSet** z danymi ze źródła danych.  
  
 [Aktualizowanie źródeł danych za pomocą elementów DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Opisuje sposób rozwiązywania zmiany z danymi w **DataSet** wstecz do źródła danych.  
  
 [Dodawanie istniejących ograniczeń do zestawu danych](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Zawiera opis sposobu wypełniania **DataSet** o informacje o kluczu podstawowym ze źródła danych.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET](../../../../../docs/framework/data/adonet/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
