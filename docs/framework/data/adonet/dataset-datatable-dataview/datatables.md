---
title: Elementy DataTable
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: 365eafc938f3db511fd6714bec02cea2bd27ea25
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204964"
---
# <a name="datatables"></a>Elementy DataTable
Składa <xref:System.Data.DataSet> się z kolekcji tabel, relacji i ograniczeń. W ADO.NET <xref:System.Data.DataTable> obiekty są używane do reprezentowania tabel w **zestawie danych**. Element **DataTable** reprezentuje jedną tabelę danych relacyjnych w pamięci; dane są lokalne dla. Aplikacja oparta na sieci, w której znajduje się, ale może zostać wypełniona ze źródła danych, takiego jak Microsoft SQL Server przy użyciu elementu **DataAdapter** Aby uzyskać więcej informacji, zobacz wypełnianie [zestawu danych z elementu DataAdapter](../populating-a-dataset-from-a-dataadapter.md).  
  
 Klasa **DataTable** jest składową przestrzeni nazw **System. Data** w bibliotece klas .NET Framework. Można utworzyć i używać **DataTable** niezależnie lub jako elementu członkowskiego **zestawu danych**, a obiekty **DataTable** mogą być również używane w połączeniu z innymi obiektami <xref:System.Data.DataView>.NET Framework, w tym. Dostęp do kolekcji tabel w **zestawie danych** można uzyskać za pomocą właściwości **Tables** obiektu **DataSet** .  
  
 Schemat lub struktura tabeli jest reprezentowana przez kolumny i ograniczenia. Schemat **tabeli DataTable** można zdefiniować przy użyciu <xref:System.Data.DataColumn> <xref:System.Data.ForeignKeyConstraint> obiektów Objects oraz <xref:System.Data.UniqueConstraint> obiektów. Kolumny w tabeli mogą być mapowane na kolumny w źródle danych, zawierają wartości obliczeniowe z wyrażeń, automatycznie zwiększają ich wartości lub zawierają wartości klucza podstawowego.  
  
 Poza schematem element **DataTable** musi także zawierać wiersze, które zawierają i porządkują dane. <xref:System.Data.DataRow> Klasa reprezentuje rzeczywiste dane zawarte w tabeli. Aby pobrać, oszacować i manipulować danymi w tabeli, należy użyć obiektu **DataRow** oraz jego właściwości i metod. Gdy uzyskujesz dostęp do danych i zmieniasz je w wierszu, obiekt **DataRow** zachowuje zarówno bieżący, jak i oryginalny stan.  
  
 Można utworzyć relacje nadrzędny-podrzędny między tabelami przy użyciu co najmniej jednej powiązanej kolumny w tabelach. Utwórz relację między obiektami **DataTable** przy użyciu <xref:System.Data.DataRelation>. Obiektów można następnie użyć do zwrócenia powiązanych podrzędnych lub nadrzędnych wierszy określonego wiersza. Aby uzyskać więcej informacji, zobacz [Dodawanie relacji](adding-datarelations.md)danych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie elementów DataTable](creating-a-datatable.md)  
 Wyjaśnia, jak utworzyć element **DataTable** i dodać go do **zestawu danych**.  
  
 [Definicja schematu elementu DataTable](datatable-schema-definition.md)  
 Zawiera informacje na temat tworzenia i używania obiektów i ograniczeń **kolumn** danych.  
  
 [Operowanie danymi w elemencie DataTable](manipulating-data-in-a-datatable.md)  
 Wyjaśnia, jak dodawać, modyfikować i usuwać dane w tabeli. Wyjaśnia, jak używać zdarzeń **DataTable** do sprawdzania zmian danych w tabeli.  
  
 [Obsługa zdarzeń elementu DataTable](handling-datatable-events.md)  
 Zawiera informacje o zdarzeniach dostępnych do użycia z elementem **DataTable**, w tym zdarzenia, gdy wartości kolumn są modyfikowane, a wiersze są dodawane lub usuwane.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ADO.NET](../index.md)  
 Opisuje architekturę i składniki ADO.NET oraz sposób ich używania do uzyskiwania dostępu do istniejących źródeł danych i zarządzania danymi aplikacji.  
  
 [Elementy DataSet, DataTable i DataView](index.md)  
 Zawiera informacje dotyczące **zestawu danych** ADO.NET, w tym sposób tworzenia relacji między tabelami.  
  
 <xref:System.Data.Constraint>  
 Zawiera informacje referencyjne dotyczące obiektu **ograniczenia** .  
  
 <xref:System.Data.DataColumn>  
 Zawiera informacje referencyjne na temat obiektu DataColumn.  
  
 <xref:System.Data.DataSet>  
 Zawiera informacje referencyjne o obiekcie **DataSet** .  
  
 <xref:System.Data.DataTable>  
 Zawiera informacje referencyjne dotyczące obiektu **DataTable** .  
  
 [Omówienie biblioteki klas](../../../../standard/class-library-overview.md)  
 Zawiera przegląd biblioteki klas .NET Framework, w tym przestrzeń nazw **systemu** , a także jej przestrzeń nazw drugiego poziomu, **System. Data**.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
