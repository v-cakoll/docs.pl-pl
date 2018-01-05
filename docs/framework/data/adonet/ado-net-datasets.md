---
title: Zestawy danych ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82b641bb-6001-4512-bf1a-2830acdd92ab
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b117b8b75cd4b90f3689fa535b0afbac0ca00fdc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="adonet-datasets"></a>Zestawy danych ADO.NET
<xref:System.Data.DataSet> Obiektu jest podstawą do obsługi odłączony, rozproszonych scenariuszy danych z [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. **DataSet** jest rezydentny reprezentację danych, który zapewnia spójne relacyjne model programowania niezależnie od tego źródła danych. Mogą być używane w wielu i różnych źródeł danych z danych XML lub zarządzać dane lokalne aplikacji. **DataSet** reprezentuje kompletny zestaw danych, w tym powiązane tabele, ograniczenia i relacje między tabelami. Na poniższej ilustracji pokazano **DataSet** obiektu modelu.  
  
 ![Grafika ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Model obiektów DataSet  
  
 Metody i obiektów w **DataSet** są spójne z identyfikatorami w modelu relacyjnej bazy danych.  
  
 **DataSet** można utrwalić i załaduj ponownie jego zawartość w formacie XML, a jego schematu XML schema definition języka (XSD) Schema. Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="the-datatablecollection"></a>DataTableCollection  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] **DataSet** zawiera kolekcję zero lub więcej tabel reprezentowany przez <xref:System.Data.DataTable> obiektów. <xref:System.Data.DataTableCollection> Zawiera wszystkie **DataTable** obiekty w **zestawu danych**.  
  
 A **DataTable** jest zdefiniowany w <xref:System.Data> przestrzeni nazw i reprezentuje pojedynczej tabeli rezydentny danych. Zawiera kolekcję kolumn reprezentowanych przez <xref:System.Data.DataColumnCollection>i ograniczenia reprezentowany przez <xref:System.Data.ConstraintCollection>, które definiują schematu tabeli. A **DataTable** także zawiera zestaw wierszy reprezentowanych przez <xref:System.Data.DataRowCollection>, który zawiera dane w tabeli. Wraz z jego bieżącym stanie <xref:System.Data.DataRow> zachowuje obie jego bieżące i oryginalne wersje identyfikuje zmiany wartości przechowywane w wierszu.  
  
## <a name="the-dataview-class"></a>DataView — klasa  
 A <xref:System.Data.DataView> można tworzyć widoki danych przechowywanych w <xref:System.Data.DataTable>, możliwość, która jest często używana w aplikacjach powiązania danych. Przy użyciu <xref:System.Data.DataView>, można udostępnić dane w tabeli z innego sortowania i dane można filtrować według wierszy stanu lub w oparciu o wyrażenie filtru. Aby uzyskać więcej informacji, zobacz [DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
## <a name="the-datarelationcollection"></a>DataRelationCollection  
 A **DataSet** zawiera relacje w jego <xref:System.Data.DataRelationCollection> obiektu. Relacja reprezentowany przez <xref:System.Data.DataRelation> obiektu, stowarzyszonych wiersze w jednej **DataTable** z wierszami w innym **DataTable**. Relacja jest odpowiednikiem ścieżki sprzężenia, które mogą istnieć między kolumnami klucza podstawowe i obce w relacyjnej bazie danych. A **DataRelation** identyfikuje pasujące kolumny w dwóch tabelach **zestawu danych**.  
  
 Relacje umożliwiają nawigowanie z jednej tabeli do drugiej **zestawu danych**. Istotne elementy **DataRelation** to nazwa relacji, nazwy tabel powiązanych i powiązane kolumny w każdej tabeli. Relacje mogą być wbudowane w więcej niż jedną kolumnę na tabelę, określając tablicę <xref:System.Data.DataColumn> obiektów jako kolumny klucza. Po dodaniu relację <xref:System.Data.DataRelationCollection>, można opcjonalnie dodawać **UniqueKeyConstraint** i **ForeignKeyConstraint** wymuszania ograniczeń integralności, podczas wprowadzania zmian do powiązane kolumny wartości.  
  
 Aby uzyskać więcej informacji, zobacz [Dodawanie DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).  
  
## <a name="xml"></a>XML  
 Możesz wpisać **DataSet** ze strumienia XML lub dokumentu. Strumień XML lub dokument można użyć do dostarczenia **zestawu danych** danych, informacje o schemacie lub obu. Informacje podane w strumieniu XML lub dokument można połączyć z istniejących danych i informacji o schemacie znajduje się już w **zestawu danych**. Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="extendedproperties"></a>właściwości rozszerzone  
 **DataSet**, **DataTable**, i **DataColumn** mieć **właściwości rozszerzone** właściwości. **Właściwości rozszerzone** jest **propertycollection klasy** umieszczane informacje niestandardowe, takie jak instrukcji SELECT, które zostało użyte do wygenerowania zestawu wyników lub czasu wygenerowania danych. **Właściwości ExtendedProperties** kolekcji jest trwały z informacji o schemacie dla **zestawu danych**.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]zapewnia zintegrowane języka podczas badania możliwości odłączonego danych przechowywanych w zestawie danych. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]używa standardu [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] składni i zapewnia sprawdzanie składni kompilacji, wpisując statyczne i obsługę funkcji IntelliSense, gdy używasz [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ do DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
