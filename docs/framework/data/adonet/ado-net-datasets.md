---
title: Zestawy danych ADO.NET
ms.date: 03/30/2017
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
ms.openlocfilehash: 50e8e8f5e4b3ee2f5a41cb9dad11b5e701135d9e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190941"
---
# <a name="adonet-datasets"></a>Zestawy danych ADO.NET
<xref:System.Data.DataSet> Obiekt ma decydujące znaczenie dla obsługi odłączony, rozproszone scenariusze danych za pomocą [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. **DataSet** jest rezydentnego reprezentację danych, które zapewnia spójny model programowania relacyjnych niezależnie od tego źródła danych. Mogą być używane z wieloma i różnymi źródłami danych z danymi XML lub do zarządzania danymi lokalne dla aplikacji. **DataSet** przedstawia kompletny zestaw danych, w tym powiązane tabele, ograniczenia i relacje między tabelami. Poniższa ilustracja przedstawia **DataSet** modelu obiektów.  
  
 ![ADO.Net graphic](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Model obiektów DataSet  
  
 Metody i obiektów w **DataSet** są spójne z identyfikatorami w modelu relacyjnej bazy danych.  
  
 **DataSet** można utrwalić i ponownie załaduj jego zawartość w formacie XML, a jego schematu jako języka (XSD) definicji schematu XML. Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **DataSet** zawiera zbiór zero lub więcej tabel, reprezentowane przez <xref:System.Data.DataTable> obiektów. <xref:System.Data.DataTableCollection> Zawiera wszystkie **DataTable** obiekty w **zestawu danych**.  
  
 A **DataTable** jest zdefiniowany w <xref:System.Data> przestrzeni nazw, a wartość reprezentuje pojedynczej tabeli dane rezydentny. Zawiera on kolekcję kolumn, reprezentowane przez <xref:System.Data.DataColumnCollection>i ograniczenia, reprezentowane przez <xref:System.Data.ConstraintCollection>, które razem definiują schematu tabeli. A **DataTable** także zawiera zestaw wierszy, reprezentowane przez <xref:System.Data.DataRowCollection>, który zawiera dane w tabeli. Wraz z jego bieżącym stanie <xref:System.Data.DataRow> zachowuje zarówno jego bieżąca i oryginalna wersja do identyfikowania zmian wartości przechowywane w wierszu.  
  
## <a name="the-dataview-class"></a>DataView — klasa  
 A <xref:System.Data.DataView> umożliwia tworzenie różnych widoków danych przechowywanych w <xref:System.Data.DataTable>, możliwości, jest często używany w aplikacjach powiązanie danych. Za pomocą <xref:System.Data.DataView>, może uwidaczniać dane w tabeli z zamówieniami sortowania i dane można filtrować według wierszy, stanu lub w zależności od wyrażenia filtru. Aby uzyskać więcej informacji, zobacz [DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>The DataRelationCollection  
 A **DataSet** zawiera relacje w jego <xref:System.Data.DataRelationCollection> obiektu. Relacja, reprezentowane przez <xref:System.Data.DataRelation> obiektu, kojarzy wierszy w jednym **DataTable** z wierszami w innym **DataTable**. Relacja jest analogiczne do ścieżki dołączania, które mogą istnieć między kolumnami klucza podstawowe i obce w relacyjnej bazie danych. A **DataRelation** identyfikuje pasujących kolumn w dwóch tabelach **zestawu danych**.  
  
 Relacje Włącz nawigację z jednej tabeli do drugiej **zestawu danych**. Istotne elementy **DataRelation** nazwę relacji, nazwy tabel powiązanych i powiązanych kolumn w każdej tabeli. Relacje mogą być wbudowane w więcej niż jedną kolumnę na tabelę, określając szereg <xref:System.Data.DataColumn> obiektów jako kolumny klucza. Podczas dodawania relacji <xref:System.Data.DataRelationCollection>, możesz opcjonalnie dodać **UniqueKeyConstraint** i **ForeignKeyConstraint** wymuszania ograniczeń integralności, gdy zmiany zostaną wprowadzone do kolumny powiązanej wartości.  
  
 Aby uzyskać więcej informacji, zobacz [Dodawanie elementów DataRelation](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Możesz wpisać **DataSet** ze strumienia XML lub dokumentu. Można użyć strumień XML lub dokument Dostarcz je do **zestawu danych** danych, informacje o schemacie lub obu. Informacje dostarczone z strumień XML lub dokumentu może być łączone z istniejące dane lub informacje o schemacie już istnieje w **zestawu danych**. Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>ExtendedProperties  
 **DataSet**, **DataTable**, i **DataColumn** wszystkie mają **ExtendedProperties** właściwości. **Właściwości rozszerzone** jest **PropertyCollection** umieszczane informacje niestandardowe, takie jak instrukcji SELECT, który został użyty do wygenerowania zestawu wyników lub czasu wygenerowania danych. **ExtendedProperties** kolekcji jest trwały informacji o schemacie dla **zestawu danych**.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapewnia zintegrowane języka zapytań możliwości dla odłączonych — dane przechowywane w zestawie danych. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] używa standardu [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] składni i dostarcza sprawdzanie składni w czasie kompilacji, wpisując statycznych i obsługę funkcji IntelliSense podczas korzystania z programu Visual Studio IDE.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
