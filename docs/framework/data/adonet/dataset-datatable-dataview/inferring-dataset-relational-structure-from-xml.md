---
title: Wnioskowanie struktury zestawu danych relacyjnych z pliku XML
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 6ded5e893ccca973f8be5f070f68d9d8c7e09678
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759686"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a>Wnioskowanie struktury zestawu danych relacyjnych z pliku XML
Relacyjne struktury lub schematu z <xref:System.Data.DataSet> składa się z tabel, kolumn, ograniczenia i relacji. Podczas ładowania <xref:System.Data.DataSet> z pliku XML, można wstępnie schematu lub można go utworzyć, jawnie lub za pośrednictwem wnioskowania o typach z pliku XML, ładowany. Aby uzyskać więcej informacji na temat ładowania schematu i zawartość <xref:System.Data.DataSet> z pliku XML, zobacz [podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) i [podczas ładowania informacji schematu zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
 Jeśli schemat <xref:System.Data.DataSet> jest tworzony z pliku XML, preferowaną metodą jest jawnie określić schemat przy użyciu schematu XML definicji języka (XSD) (zgodnie z opisem w [wyprowadzanie struktury relacyjne zestawu danych z schematu XML (XSD) ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)) lub danych XML zmniejszona (XDR). Jeśli schemat XML lub XDR schemat jest dostępna w pliku XML, schemat <xref:System.Data.DataSet> można wywnioskować na podstawie struktury elementów XML oraz atrybuty.  
  
 W tej sekcji opisano reguły dotyczące <xref:System.Data.DataSet> wnioskowania schematu, zwiększając liczbę pokazywanych elementów XML oraz atrybuty i ich struktury i wynikowa wywnioskować <xref:System.Data.DataSet> schematu.  
  
 Nie wszystkie atrybuty w dokumencie XML powinny uwzględnione w procesie wnioskowania. Atrybuty kwalifikowana Namespace może zawierać metadane, które są ważne dla dokumentu XML, ale nie dla <xref:System.Data.DataSet> schematu. Przy użyciu <xref:System.Data.DataSet.InferXmlSchema%2A>, można określić przestrzeni nazw ma być ignorowane podczas wnioskowania. Aby uzyskać więcej informacji, zobacz [podczas ładowania informacji schematu zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podsumowanie procesu wnioskowania schematu elementu DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/summary-of-the-dataset-schema-inference-process.md)  
 Zawiera podsumowanie wysokiego poziomu zasad dla wnioskowanie schematu <xref:System.Data.DataSet> z pliku XML.  
  
 [Wnioskowanie tabel](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)  
 W tym artykule opisano elementy XML, które są wywnioskować jako tabele w <xref:System.Data.DataSet>.  
  
 [Wnioskowanie kolumn](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-columns.md)  
 Zawiera opis elementów XML oraz atrybuty, które są wywnioskować jako kolumny w tabeli.  
  
 [Wnioskowanie relacji](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-relationships.md)  
 W tym artykule opisano <xref:System.Data.DataRelation> i <xref:System.Data.ForeignKeyConstraint> obiektów utworzonych zagnieżdżonych, wywnioskować tabel.  
  
 [Wnioskowanie tekstu elementu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-element-text.md)  
 Opisuje kolumny, które zostały utworzone dla tekstu w elementów XML i wyjaśniono, gdy tekst w elementach XML jest ignorowany.  
  
 [Ograniczenia wnioskowania](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inference-limitations.md)  
 W tym artykule omówiono ograniczenia wnioskowania schematu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Używanie języka XML w elemencie DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Opisuje sposób <xref:System.Data.DataSet> obiektu współdziała z danych XML.  
  
 [Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Opisuje relacyjne struktury lub schematu z <xref:System.Data.DataSet> utworzonego ze schematu (XSD) języka definicji schematu XML.  
  
 [Omówienie ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 W tym artykule opisano ADO.NET architektury i składników oraz sposób ich używać do dostęp do istniejących źródeł danych i zarządzanie danych aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
