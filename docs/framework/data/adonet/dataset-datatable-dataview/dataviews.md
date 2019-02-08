---
title: DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: bcf370e30c50bf5d992279c7abe02bfc6262ea40
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55825878"
---
# <a name="dataviews"></a>DataView
A <xref:System.Data.DataView> umożliwia tworzenie różnych widoków danych przechowywanych w <xref:System.Data.DataTable>, możliwości, jest często używany w aplikacjach powiązanie danych. Za pomocą **DataView**, może uwidaczniać dane w tabeli z zamówieniami sortowania i dane można filtrować według wierszy, stanu lub w zależności od wyrażenia filtru.  
  
 A **DataView** udostępnia dynamiczny widok danych w źródłowym **DataTable**: zawartość, kolejność i członkostwa odzwierciedlenia zmian w miarę ich występowania. To zachowanie różni się od **wybierz** metody **DataTable**, co powoduje zwrócenie <xref:System.Data.DataRow> tablica z tabeli opartym na określonej kolejności filtrowania lub sortowania: Ta zawartość zawiera zmiany podstawowy w tabeli, ale członkostwo i kolejność pozostaną statyczne. Dynamiczne możliwości **DataView** jest idealnym rozwiązaniem dla wiązania danych aplikacji.  
  
 A **DataView** udostępnia dynamiczny widok jednego zestawu danych, podobnie jak widok bazy danych, do którego można zastosować różne sortowanie i kryteria filtrowania. W przeciwieństwie do widoku bazy danych, jednak **DataView** nie może być traktowany jako tabelę i nie można udostępnić widok Tabele sprzężone. Również nie można wykluczyć kolumny, które istnieją w tabeli źródłowej i nie można dołączyć kolumn, takich jak kolumny obliczeniowej, które nie istnieją w tabeli źródłowej.  
  
 Możesz użyć <xref:System.Data.DataView.DataViewManager%2A> do zarządzania ustawieniami widoku dla wszystkich tabel w **zestawu danych**. **DataViewManager** zapewnia wygodny sposób zarządzać domyślne ustawienia widoku dla każdej tabeli. Podczas tworzenia wiązania kontrolki do więcej niż jedną tabelę **DataSet**, wiązania do **DataViewManager** jest idealnym wyborem.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementu DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 W tym artykule opisano sposób tworzenia **DataView** dla **DataTable**.  
  
 [Sortowanie i filtrowanie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 W tym artykule opisano sposób ustawiania właściwości **DataView** zwracanie podzbiorów danych wiersze spełniające kryteria filtru określonego lub zwrócić dane w określony porządek sortowania.  
  
 [Elementy DataRow i DataRowView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 Opisuje, jak uzyskać dostęp do danych udostępnianych przez **DataView**.  
  
 [Znajdowanie wierszy](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 Opisuje sposób wyszukiwania określonego wiersza w **DataView**.  
  
 [Elementy ChildView i relacje](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 W tym artykule opisano sposób tworzenia widoków danych z relacji nadrzędny podrzędny za pomocą **DataView**.  
  
 [Modyfikowanie elementów DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 Opisuje sposób modyfikowania danych w źródłowym **DataTable** za pośrednictwem **DataView**, w tym na włączenie lub wyłączenie aktualizacji.  
  
 [Obsługa zdarzeń elementu DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 Opisuje sposób używania **ListChanged** zdarzeń, aby otrzymać powiadomienie po zawartości lub kolejność **DataView** jest aktualizowana.  
  
 [Zarządzanie elementami DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 Opisuje sposób używania **DataViewManager** zarządzanie **DataView** ustawienia dla każdej tabeli w **zestawu danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Aplikacje internetowe ASP.NET](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))  
 Zawiera omówienie i szczegółowe procedury krok po kroku do tworzenia aplikacji platformy ASP.NET, formularze sieci Web i usług sieci Web.  
  
 [Aplikacje Windows](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))  
 Zawiera szczegółowe informacje na temat pracy z usługą Windows Forms i aplikacji konsoli.  
  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 W tym artykule opisano **DataSet** obiektu i jak go używać do zarządzania danymi w aplikacji.  
  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 W tym artykule opisano **DataTable** obiektu i jak go używać do zarządzania danymi aplikacji, samodzielnie lub jako część **zestawu danych**.  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 W tym artykule opisano ADO.NET architektura i składniki i jak za pomocą ADO.NET dostęp do istniejących źródeł danych i zarządzania danymi w aplikacji.  
  
## <a name="see-also"></a>Zobacz także
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
