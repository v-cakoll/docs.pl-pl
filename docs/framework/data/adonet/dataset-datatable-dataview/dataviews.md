---
title: Elementy DataView
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 8a06accb11631f2dce6b0d39587d7274223c0e68
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786347"
---
# <a name="dataviews"></a>Elementy DataView
A <xref:System.Data.DataView> umożliwia tworzenie różnych widoków danych przechowywanych <xref:System.Data.DataTable>w programie, które są często używane w aplikacjach do wiązania danych. Za pomocą elementu **DataView**można uwidocznić dane w tabeli z różnymi kolejności sortowania i można filtrować dane według stanu wiersza lub w oparciu o wyrażenie filtru.  
  
 **Element DataView** udostępnia dynamiczny widok danych w źródłowej **tabeli DataTable**: zawartość, kolejność i członkostwo odzwierciedlają zmiany w miarę ich występowania. To zachowanie różni się od metody **SELECT** **elementu DataTable**, <xref:System.Data.DataRow> która zwraca tablicę z tabeli na podstawie określonego filtru i/lub porządku sortowania: Ta zawartość odzwierciedla zmiany w tabeli podstawowej, ale jego członkostwo i Porządkowanie pozostaje statyczne. Dynamiczne możliwości obiektu **DataView** sprawiają, że są idealnym rozwiązaniem dla aplikacji do wiązania danych.  
  
 **Element DataView** udostępnia dynamiczny widok pojedynczego zestawu danych, podobnie jak widok bazy danych, do którego można zastosować różne kryteria sortowania i filtrowania. W przeciwieństwie do widoku bazy danych, jednak **element DataView** nie może być traktowany jako tabela i nie może zawierać widoku sprzężonych tabel. Nie można również wykluczyć kolumn istniejących w tabeli źródłowej ani dodawać kolumn, takich jak kolumny obliczeniowe, które nie istnieją w tabeli źródłowej.  
  
 Aby zarządzać ustawieniami widoku <xref:System.Data.DataView.DataViewManager%2A> dla wszystkich tabel w **zestawie danych**, można użyć elementu. Element **DataViewManager** zapewnia wygodny sposób zarządzania domyślnymi ustawieniami widoku dla każdej tabeli. W przypadku wiązania kontrolki z więcej niż jedną tabelą **zestawu danych**powiązanie z elementem **DataViewManager** jest idealnym wyborem.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementu DataView](creating-a-dataview.md)  
 Opisuje sposób tworzenia elementu **DataView** dla **elementu DataTable**.  
  
 [Sortowanie i filtrowanie danych](sorting-and-filtering-data.md)  
 Opisuje sposób ustawiania właściwości elementu **DataView** do zwracania podzbiorów wierszy danych spełniających kryteria filtrowania lub do zwracania danych w określonej kolejności sortowania.  
  
 [Elementy DataRow i DataRowView](datarows-and-datarowviews.md)  
 Opisuje sposób uzyskiwania dostępu do danych uwidocznionych przez **Widok DataView**.  
  
 [Znajdowanie wierszy](finding-rows.md)  
 Opisuje, jak znaleźć konkretny wiersz w **widoku**danych.  
  
 [Elementy ChildView i relacje](childviews-and-relations.md)  
 Opisuje sposób tworzenia widoków danych z relacji nadrzędny-podrzędny przy użyciu elementu **DataView**.  
  
 [Modyfikowanie elementów DataView](modifying-dataviews.md)  
 Opisuje, jak modyfikować dane w źródłowej **DataTable** za pośrednictwem **widoku**danych, w tym Włączanie lub wyłączanie aktualizacji.  
  
 [Obsługa zdarzeń elementu DataView](handling-dataview-events.md)  
 Opisuje sposób korzystania z zdarzenia **ListChanged** w celu otrzymywania powiadomień w przypadku aktualizowania zawartości lub kolejności elementu **DataView** .  
  
 [Zarządzanie elementami DataView](managing-dataviews.md)  
 Opisuje, w jaki sposób używać elementu **DataViewManager** do zarządzania ustawieniami **DataView** dla każdej tabeli w **zestawie danych**.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Aplikacje internetowe ASP.NET](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))  
 Oferuje przeglądy i szczegółowe procedury krok po kroku dotyczące tworzenia aplikacji ASP.NET, formularzy sieci Web i usług sieci Web.  
  
 [Aplikacje systemu Windows](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))  
 Zawiera szczegółowe informacje dotyczące pracy z aplikacjami Windows Forms i konsolą programu.  
  
 [Elementy DataSet, DataTable i DataView](index.md)  
 Opisuje obiekt **DataSet** i jak można go użyć do zarządzania danymi aplikacji.  
  
 [Elementy DataTable](datatables.md)  
 Opisuje obiekt **DataTable** i sposób, w jaki można go użyć do zarządzania danymi aplikacji przez siebie lub jako część **zestawu danych**.  
  
 [ADO.NET](../index.md)  
 Opisuje architekturę i składniki ADO.NET oraz sposób używania ADO.NET do uzyskiwania dostępu do istniejących źródeł danych i zarządzania danymi aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](../ado-net-overview.md)
