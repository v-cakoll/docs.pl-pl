---
title: Eksportowanie schematów z klas
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, schema import and export
- schemas [WCF], exporting from classes
- schemas [WCF]
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: bb57b962-70c1-45a9-93d5-e721e340a13f
ms.openlocfilehash: 9fa123e5532e4c721af5f3ece4feeea92356d1fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exporting-schemas-from-classes"></a>Eksportowanie schematów z klas
Aby wygenerować schematu XML definition language (XSD) schematów z klas, które są używane w modelu kontraktu danych, użyj <xref:System.Runtime.Serialization.XsdDataContractExporter> klasy. W tym temacie opisano proces tworzenia schematów.  
  
## <a name="the-export-process"></a>Proces eksportowania  
 Proces eksportowania schematu rozpoczyna się od jednego lub więcej typów i tworzy <xref:System.Xml.Schema.XmlSchemaSet> opisujący projekcji XML z tych typów.  
  
 `XmlSchemaSet` Jest częścią [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]tego schematu obiektu Model (model SOM) reprezentujący zestaw dokumentów schematu XSD. Tworzenie dokumentów XSD z `XmlSchemaSet`, użyć kolekcji schematów z <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwość `XmlSchemaSet` klasy. Następnie serializować każdego <xref:System.Xml.Schema.XmlSchema> przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.  
  
#### <a name="to-export-schemas"></a>Aby wyeksportować schematów  
  
1.  Utwórz wystąpienie <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2.  Opcjonalna. Przekaż <xref:System.Xml.Schema.XmlSchemaSet> w konstruktorze. W takim przypadku schematu wygenerowanego podczas eksportu schematu jest dodane do tego <xref:System.Xml.Schema.XmlSchemaSet> wystąpienia zamiast począwszy od pustego <xref:System.Xml.Schema.XmlSchemaSet>.  
  
3.  Opcjonalna. Wywoływanie jednego z <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> metody. Metoda określa, czy można wyeksportować określonego typu. Metoda ma tego samego przeciążeń jako `Export` metody w następnym kroku.  
  
4.  Wywoływanie jednego z <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metody. Istnieją trzy przeciążenia biorąc <xref:System.Type>, <xref:System.Collections.Generic.List%601> z `Type` obiektów, lub <xref:System.Collections.Generic.List%601> z <xref:System.Reflection.Assembly> obiektów. W ostatnim przypadku eksportowane są wszystkie typy w podane zestawy.  
  
     Wiele wywołań `Export` powoduje wielu elementów dodawane do tej samej metody `XmlSchemaSet`. Typ nie jest generowany w `XmlSchemaSet` Jeśli istnieje już istnieje. W związku z tym wywołaniem `Export` wiele razy w tym samym `XsdDataContractExporter` lepiej jest tworzenie wielu wystąpień `XsdDataContractExporter` klasy. Dzięki temu można uniknąć typów duplikat schematu z generowany.  
  
    > [!NOTE]
    >  W przypadku awarii podczas eksportu, `XmlSchemaSet` będzie w nieprzewidywalnym stanie.  
  
5.  Dostęp <xref:System.Xml.Schema.XmlSchemaSet> za pośrednictwem <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> właściwości.  
  
## <a name="export-options"></a>Opcje eksportu  
 Można ustawić <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> właściwość <xref:System.Runtime.Serialization.XsdDataContractExporter> na wystąpienie <xref:System.Runtime.Serialization.ExportOptions> klasę, aby kontrolować różne aspekty procesu eksportowania. W szczególności można ustawić następujące opcje:  
  
-   <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Ta kolekcja `Type` reprezentuje znanych typów dla typów eksportowane. (Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Te znane typy są eksportowane na każdym `Export` Ponadto wywołanie typów przekazywanej do `Export` — metoda.  
  
-   <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. <xref:System.Runtime.Serialization.IDataContractSurrogate> Mogą być dostarczane za pomocą tej właściwości, który będzie dostosowania procesu eksportu. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Domyślnie surogat nie jest używany.  
  
## <a name="helper-methods"></a>Metody pomocnicze  
 Oprócz jego podstawową rolą, jaką eksportowania schematu `XsdDataContractExporter` udostępnia kilka metod przydatne pomocnika, które zawierają informacje o typach. Należą do nich następujące elementy:  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> Metoda. Ta metoda przyjmuje `Type` i zwraca <xref:System.Xml.XmlQualifiedName> reprezentujący nazwę elementu głównego i przestrzeni nazw, które mają być używane, jeśli zostały zserializować tego typu jako główny obiekt.  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> Metoda. Ta metoda przyjmuje `Type` i zwraca <xref:System.Xml.XmlQualifiedName> reprezentujący nazwę typu schematu XSD, który będzie używany w przypadku tego typu zostały wyeksportowane do schematu. Aby uzyskać <xref:System.Xml.Serialization.IXmlSerializable> typy reprezentowane jako typy anonimowe w schemacie, ta metoda zwraca `null`.  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> Metoda. Ta metoda działa tylko w przypadku <xref:System.Xml.Serialization.IXmlSerializable> typy, które są reprezentowane jako typy anonimowe schematu i zwraca `null` dla wszystkich innych typów. Typy anonimowe, ta metoda zwraca <xref:System.Xml.Schema.XmlSchemaType> reprezentujący danego `Type`.  
  
 Opcje eksportu wpływają na wszystkie te metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 [importowanie i eksportowanie schematu](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)  
 [Importowanie schematu w celu generowania klas](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
