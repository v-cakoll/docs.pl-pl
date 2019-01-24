---
title: Wnioskowanie relacyjnej struktury zestawu danych z pliku XML
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: f5cbbcd148f13a630398e870124803d482f63698
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587651"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Wnioskowanie relacyjnej struktury zestawu danych z pliku XML
Relacyjnej struktury lub schematu z <xref:System.Data.DataSet> składa się z tabel, kolumn, ograniczeń i relacji. Podczas ładowania <xref:System.Data.DataSet> z pliku XML mogą być wstępnie zdefiniowane schematu lub mogą być tworzone, jawnie lub za pośrednictwem wnioskowania z pliku XML, trwa ładowanie. Aby uzyskać więcej informacji na temat ładowania schematu i zawartość <xref:System.Data.DataSet> z pliku XML, zobacz [Ładowanie elementu DataSet z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) i [podczas ładowania informacji schematu zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
 Jeśli schemat <xref:System.Data.DataSet> jest tworzony z pliku XML preferowaną metodą jest jawnie określić schematu za pomocą dowolnego języka definicji schematu XML (XSD) (zgodnie z opisem w [elementu pochodnego dla zestawu danych relacyjnej struktury z schematu XML (XSD) ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) lub zmniejszone danych XML (XDR). Jeśli Brak schematu XML lub XDR schematu jest dostępny w formacie XML, schemat <xref:System.Data.DataSet> można wywnioskować na podstawie struktury elementów XML oraz atrybuty.  
  
 W tej sekcji opisano reguły dotyczące <xref:System.Data.DataSet> wnioskowania schematu, pokazując elementów XML i atrybutów i ich struktury i wynikowa wywnioskować <xref:System.Data.DataSet> schematu.  
  
 Nie wszystkie atrybuty w dokumencie XML, powinny być uwzględnione w procesie wnioskowania. Atrybuty kwalifikowana Namespace może zawierać metadane, które są ważne dla dokumentu XML, ale nie dla <xref:System.Data.DataSet> schematu. Za pomocą <xref:System.Data.DataSet.InferXmlSchema%2A>, można określić przestrzenie nazw mają być ignorowane podczas procesu wnioskowania. Aby uzyskać więcej informacji, zobacz [podczas ładowania informacji schematu zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podsumowanie procesu wnioskowania schematu elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 Zawiera podsumowanie wysokiego poziomu zasad wnioskowania schematu <xref:System.Data.DataSet> z pliku XML.  
  
 [Wnioskowanie tabel](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 W tym artykule opisano elementy XML, które są wnioskowane jako tabele w <xref:System.Data.DataSet>.  
  
 [Wnioskowanie kolumn](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 W tym artykule opisano elementy XML i atrybutów, które są wnioskowane jako kolumny w tabeli.  
  
 [Wnioskowanie relacji](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 W tym artykule opisano <xref:System.Data.DataRelation> i <xref:System.Data.ForeignKeyConstraint> obiekty utworzone dla zagnieżdżonych, wywnioskować tabel.  
  
 [Wnioskowanie tekstu elementu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 Zawiera opis kolumn, które zostały utworzone dla tekstu w elementach XML i wyjaśnia, kiedy tekst w elementach XML jest ignorowany.  
  
 [Ograniczenia wnioskowania](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 W tym artykule omówiono ograniczenia wnioskowania schematu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 W tym artykule opisano sposób, w jaki <xref:System.Data.DataSet> obiektu wchodzi w interakcję z danymi XML.  
  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 W tym artykule opisano relacyjnej struktury lub schematu z <xref:System.Data.DataSet> , jest tworzona na podstawie schematu języka (XSD) definicji schematu XML.  
  
 [Omówienie ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 W tym artykule opisano ADO.NET architektura i składniki i sposób ich użycia, dostęp do istniejących źródeł danych i zarządzanie danymi aplikacji.  
  
## <a name="see-also"></a>Zobacz także
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
