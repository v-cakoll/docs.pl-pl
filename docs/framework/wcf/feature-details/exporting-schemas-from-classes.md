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
ms.openlocfilehash: dcbccbea279796fdaec1227b7575cf39e47f9e4f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336879"
---
# <a name="exporting-schemas-from-classes"></a>Eksportowanie schematów z klas
Aby wygenerować schematów języka (XSD) definicji schematu XML z klas, które są używane w modelu kontraktu danych, należy użyć <xref:System.Runtime.Serialization.XsdDataContractExporter> klasy. W tym temacie opisano proces tworzenia schematów.  
  
## <a name="the-export-process"></a>Proces eksportowania  
 Proces eksportowania schematu rozpoczyna się od jednego lub więcej typów i tworzy <xref:System.Xml.Schema.XmlSchemaSet> opisujący projekcji XML z tych typów.  
  
 `XmlSchemaSet` Jest częścią [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]firmy schematu Object Model (model SOM) reprezentujący zestaw dokumentów schematu XSD. Tworzenie dokumentów XSD z `XmlSchemaSet`, korzystać z kolekcji schematów na podstawie <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwość `XmlSchemaSet` klasy. Następnie każdy serializacji <xref:System.Xml.Schema.XmlSchema> przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.  
  
#### <a name="to-export-schemas"></a>Aby wyeksportować schematów  
  
1. Utwórz wystąpienie obiektu <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2. Opcjonalna. Przekaż <xref:System.Xml.Schema.XmlSchemaSet> w konstruktorze. W tym przypadku schematu wygenerowanego podczas eksportu schematu jest dodawany do tego <xref:System.Xml.Schema.XmlSchemaSet> wystąpienie zamiast począwszy od pustego <xref:System.Xml.Schema.XmlSchemaSet>.  
  
3. Opcjonalna. Wywołanie jednej z <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> metody. Metoda określa, czy można wyeksportować określonego typu. Metoda ma tego samego przeciążenia jako `Export` metody w następnym kroku.  
  
4. Wywołanie jednej z <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metody. Istnieją trzy przeciążenia biorąc <xref:System.Type>, <xref:System.Collections.Generic.List%601> z `Type` obiektów, lub <xref:System.Collections.Generic.List%601> z <xref:System.Reflection.Assembly> obiektów. W ostatnim przypadku eksportowane są wszystkie typy w podane zestawy.  
  
     Wiele wywołań `Export` metoda nie powoduje wiele elementów, które są dodawane do tej samej `XmlSchemaSet`. Typ nie jest generowany w `XmlSchemaSet` Jeśli istnieje już istnieje. Dlatego wywołanie `Export` wiele razy w tym samym `XsdDataContractExporter` jest tworzenie wielu wystąpień `XsdDataContractExporter` klasy. Umożliwia to uniknięcie typy zduplikowanych schematów generowania.  
  
    > [!NOTE]
    >  Jeśli wystąpi awaria podczas eksportu `XmlSchemaSet` będą znajdować się w nieprzewidywalnym stanie.  
  
5. Dostęp do <xref:System.Xml.Schema.XmlSchemaSet> za pośrednictwem <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> właściwości.  
  
## <a name="export-options"></a>Opcje eksportu  
 Możesz ustawić <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> właściwość <xref:System.Runtime.Serialization.XsdDataContractExporter> do wystąpienia <xref:System.Runtime.Serialization.ExportOptions> klasy, aby kontrolować różne aspekty procesu eksportu. W szczególności można ustawić następujące opcje:  
  
-   <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Ta kolekcja `Type` reprezentuje znanych typów dla typów eksportowanych. (Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).) Te znane typy są eksportowane na każdy `Export` wywołanie dodatkowo typy przekazane do `Export` metody.  
  
-   <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. <xref:System.Runtime.Serialization.IDataContractSurrogate> Mogą być dostarczane za pośrednictwem tej właściwości, które umożliwia dostosowywanie procesu eksportu. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Domyślnie jest używany nie zastępczy.  
  
## <a name="helper-methods"></a>Metody pomocnicze  
 Oprócz jego podstawową rolą Eksportowanie schematu `XsdDataContractExporter` udostępnia kilka metod pomocniczych użyteczne, które dostarczają informacji na temat typów. Należą do nich następujące elementy:  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A> Metoda. Ta metoda przyjmuje `Type` i zwraca <xref:System.Xml.XmlQualifiedName> reprezentujący nazwę elementu głównego i przestrzeni nazw, która będzie używana w przypadku tego typu zostały zaszeregowane w głównym obiekcie.  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A> Metoda. Ta metoda przyjmuje `Type` i zwraca <xref:System.Xml.XmlQualifiedName> reprezentujący nazwę typu schematu XSD, która będzie używana w przypadku tego typu zostały wyeksportowane do schematu. Aby uzyskać <xref:System.Xml.Serialization.IXmlSerializable> typów reprezentowane jako typów anonimowych w schemacie, Metoda ta zwraca `null`.  
  
-   <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A> Metoda. Ta metoda działa tylko w przypadku <xref:System.Xml.Serialization.IXmlSerializable> typy, które są reprezentowane jako typów anonimowych w schemacie, a następnie zwraca `null` dla wszystkich innych typów. Typy anonimowe, Metoda ta zwraca <xref:System.Xml.Schema.XmlSchemaType> reprezentujący danego `Type`.  
  
 Opcje eksportu mają wpływ na wszystkie te metody.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [Importowanie i eksportowanie schematu](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Importowanie schematu w celu generowania klas](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
