---
title: DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a2653a94992440b747371c5d8a7b9daa66b3e3ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dataviews"></a>DataViews
A <xref:System.Data.DataView> można tworzyć widoki danych przechowywanych w <xref:System.Data.DataTable>, możliwość, która jest często używana w aplikacjach powiązania danych. Przy użyciu **DataView**, można udostępnić dane w tabeli z innego sortowania i dane można filtrować według wierszy stanu lub w oparciu o wyrażenie filtru.  
  
 A **DataView** udostępnia dynamiczny widok danych podstawowych **DataTable**: zawartość, kolejność i członkostwa odzwierciedlenia zmian w miarę ich występowania. To zachowanie różni się od **wybierz** metody **DataTable**, która zwraca <xref:System.Data.DataRow> tablicy z tabeli na podstawie w określonej kolejności filtru i/lub sortowania: thiscontent odzwierciedla zmiany podstawowy w tabeli, ale jego członkostwa i kolejność pozostały niezmienione. Dynamiczne możliwości środowiska **DataView** była idealne dla powiązania danych aplikacji.  
  
 A **DataView** udostępnia dynamiczny widok jednego zestawu danych, tak jak widok bazy danych, do której można zastosować różne sortowanie i kryteria filtrowania. W przeciwieństwie do widoku bazy danych, jednak **DataView** nie może być traktowane jako tabelę i nie umożliwia wyświetlanie połączonych tabel. Również nie można wykluczyć kolumny, które istnieją w tabeli źródłowej i nie można dodać kolumny, takich jak kolumny obliczeniowej, które nie istnieją w tabeli źródłowej.  
  
 Można użyć <xref:System.Data.DataView.DataViewManager%2A> umożliwia zarządzanie ustawieniami widoku wszystkie tabele w **zestawu danych**. **DataViewManager** zapewnia wygodny sposób zarządzania domyślne ustawienia widoku dla każdej tabeli. Podczas tworzenia wiązania formantu więcej niż jednej tabeli **DataSet**, powiązania do **DataViewManager** jest idealnym wyborem.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie widoku danych.](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 Opisuje sposób tworzenia **DataView** dla **DataTable**.  
  
 [Sortowanie i filtrowanie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 Opisuje sposób ustawiania właściwości **DataView** zwracanie podzbiorów danych wiersze spełniające kryteria określony filtr lub zwróć dane określony porządek sortowania.  
  
 [Elementów DataRows i DataRowViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 Zawiera opis sposobu uzyskiwania dostępu do danych udostępnianych przez **DataView**.  
  
 [Znajdowanie wierszy](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 Opisuje sposób wyszukiwania określonego wiersza w **DataView**.  
  
 [ChildViews i relacji](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 Opisuje sposób tworzenia widoków danych z relacji nadrzędny podrzędny przy użyciu **DataView**.  
  
 [Modyfikowanie DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 Opisuje sposób modyfikowania danych podstawowych **DataTable** za pośrednictwem **DataView**, w tym o włączeniu lub wyłączeniu aktualizacji.  
  
 [Obsługa zdarzeń widoku danych.](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 Informacje dotyczące używania **ListChanged** zdarzeń, aby otrzymać powiadomienie po zawartości lub kolejność **DataView** jest aktualizowana.  
  
 [Zarządzanie DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 Informacje dotyczące używania **DataViewManager** do zarządzania **DataView** ustawienia dla każdej tabeli w **zestawu danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Aplikacje sieci Web ASP.NET](http://msdn.microsoft.com/en-us/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 Zawiera przegląd i szczegółowe procedury krok po kroku dotyczące tworzenia aplikacji ASP.NET, formularzy sieci Web i usług sieci Web.  
  
 [Aplikacje systemu Windows](http://msdn.microsoft.com/en-us/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 Zawiera szczegółowe informacje dotyczące pracy z formularzy systemu Windows i aplikacji konsoli.  
  
 [Zbiory danych, DataTables i DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 W tym artykule opisano **DataSet** obiektu i jak go używać do zarządzania danymi aplikacji.  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 W tym artykule opisano **DataTable** obiektu i jak go używać do zarządzania danymi aplikacji, samodzielnie lub w ramach **zestawu danych**.  
  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 W tym artykule opisano ADO.NET architektury i składników oraz sposób ADO.NET umożliwia dostęp do istniejących źródeł danych i zarządzanie danych aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
