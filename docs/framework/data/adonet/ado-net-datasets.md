---
title: Zestawy danych
description: Dowiedz się więcej o zestawie danych, reprezentacji danych rezydentnej w pamięci, która zapewnia spójny relacyjny model programowania niezależnie od źródła danych w ADO.NET.
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: 2fc5963937f7bf15dc192c6dc0a980d544a23194
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287132"
---
# <a name="adonet-datasets"></a>Zestawy danych ADO.NET
<xref:System.Data.DataSet>Obiekt jest centralną obsługą rozłączonych, rozproszonych scenariuszy danych za pomocą ADO.NET. **Zestaw danych** to reprezentacja danych będąca rezydentem pamięci, która zapewnia spójny relacyjny model programowania niezależnie od źródła danych. Może być używany z wieloma i różnymi źródłami danych, z danymi XML lub do zarządzania danymi lokalnymi w aplikacji. **Zestaw** danych reprezentuje kompletny zestaw danych, w tym powiązane tabele, ograniczenia i relacje między tabelami. Na poniższej ilustracji przedstawiono model obiektów **DataSet** .  
  
 ![Grafika ADO.Net](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Model obiektów DataSet  
  
 Metody i obiekty w **zestawie danych** są spójne z tymi w modelu relacyjnej bazy danych.  
  
 **Zestaw danych** może również utrwalać i ładować jego zawartość jako XML oraz schemat jako schemat języka definicji schematu XML (XSD). Aby uzyskać więcej informacji, zobacz [Używanie języka XML w zestawie danych](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>Tabela DataTableCollection  
 **Zestaw danych** ADO.NET zawiera kolekcję zawierającą zero lub więcej tabel reprezentowanych przez <xref:System.Data.DataTable> obiekty. <xref:System.Data.DataTableCollection>Zawiera wszystkie obiekty **DataTable** w **zestawie danych**.  
  
 Element **DataTable** jest zdefiniowany w <xref:System.Data> przestrzeni nazw i reprezentuje pojedynczą tabelę danych znajdujących się w pamięci. Zawiera kolekcję kolumn reprezentowane przez <xref:System.Data.DataColumnCollection> , i ograniczenia reprezentowane przez <xref:System.Data.ConstraintCollection> , które razem definiują schemat tabeli. **Tabela DataTable** zawiera również kolekcję wierszy reprezentowanych przez obiekt <xref:System.Data.DataRowCollection> , który zawiera dane w tabeli. Wraz z bieżącym stanem <xref:System.Data.DataRow> zachowuje zarówno bieżącą, jak i oryginalną wersję, aby identyfikować zmiany wartości przechowywanych w wierszu.  
  
## <a name="the-dataview-class"></a>Element DataView — Klasa  
 A <xref:System.Data.DataView> umożliwia tworzenie różnych widoków danych przechowywanych w programie <xref:System.Data.DataTable> , które są często używane w aplikacjach do wiązania danych. Korzystając z <xref:System.Data.DataView> , można uwidocznić dane w tabeli z różnymi kolejności sortowania i można filtrować dane według stanu wiersza lub w oparciu o wyrażenie filtru. Aby uzyskać więcej informacji, zobacz temat [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 **Zestaw danych** zawiera relacje w <xref:System.Data.DataRelationCollection> obiekcie. Relacja reprezentowana przez <xref:System.Data.DataRelation> obiekt kojarzy wiersze w jednej **tabeli DataTable** z wierszami w innej **tabeli DataTable**. Relacja jest analogiczna do ścieżki sprzężenia, która może istnieć między podstawowymi a kolumnami klucza obcego w relacyjnej bazie danych. **Relacja** danych identyfikuje pasujące kolumny w dwóch tabelach **zestawu danych**.  
  
 Relacje umożliwiają nawigację z jednej tabeli do innej w **zestawie danych**. Zasadniczymi elementami **relacji** datarelationship są Nazwa relacji, Nazwa powiązanych tabel i powiązane kolumny w każdej tabeli. Relacje można kompilować z więcej niż jedną kolumną na tabelę, określając tablicę <xref:System.Data.DataColumn> obiektów jako kolumny klucza. Po dodaniu relacji do elementu <xref:System.Data.DataRelationCollection> można opcjonalnie dodać **UniqueKeyConstraint** i **element ForeignKeyConstraint** , aby wymusić ograniczenia integralności w przypadku wprowadzenia zmian w powiązanych wartościach kolumn.  
  
 Aby uzyskać więcej informacji, zobacz [Dodawanie relacji](./dataset-datatable-dataview/adding-datarelations.md)danych.  
  
## <a name="xml"></a>XML  
 **Zestaw danych** można wypełniać ze strumienia XML lub dokumentu. Możesz użyć strumienia XML lub dokumentu, aby dostarczyć do **zestawu** danych dane, informacje o schemacie lub oba te elementy. Informacje dostarczone ze strumienia lub dokumentu XML mogą być łączone z istniejącymi danymi lub informacjami o schemacie już obecnymi w **zestawie danych**. Aby uzyskać więcej informacji, zobacz [Używanie języka XML w zestawie danych](./dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>Właściwości ExtendedProperties  
 Wszystkie **zestawy danych**, **DataTable**i **DataColumn** mają właściwość **Właściwości ExtendedProperties** . **Właściwości ExtendedProperties** jest **właściwością** , w której można umieścić informacje niestandardowe, takie jak instrukcja SELECT, która została użyta do wygenerowania zestawu wyników lub godzina wygenerowania danych. Kolekcja **Właściwości ExtendedProperties** jest utrwalona z informacjami o schemacie dla **zestawu danych**.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 LINQ to DataSet udostępnia funkcje obsługi zapytań zintegrowanych z językiem dla odłączonych danych przechowywanych w zestawie danych. LINQ to DataSet używa standardowej składni LINQ i zapewnia sprawdzanie składni w czasie kompilacji, statyczne wpisywanie i obsługę technologii IntelliSense podczas korzystania ze środowiska IDE programu Visual Studio.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](ado-net-overview.md)
- [Elementy DataSet, DataTable i DataView](./dataset-datatable-dataview/index.md)
- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
