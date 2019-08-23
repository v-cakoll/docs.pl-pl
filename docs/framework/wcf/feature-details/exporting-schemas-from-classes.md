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
ms.openlocfilehash: 3db3cc1c529ab40bf775c06a5128e4dabf3c8a56
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963654"
---
# <a name="exporting-schemas-from-classes"></a>Eksportowanie schematów z klas
Aby wygenerować schematy języka definicji schematu XML (XSD) z klas, które są używane w modelu kontraktu danych, użyj <xref:System.Runtime.Serialization.XsdDataContractExporter> klasy. W tym temacie opisano proces tworzenia schematów.  
  
## <a name="the-export-process"></a>Proces eksportowania  
 Proces eksportowania schematu rozpoczyna się od jednego lub kilku typów i tworzy <xref:System.Xml.Schema.XmlSchemaSet> , który opisuje projekcję XML tych typów.  
  
 `XmlSchemaSet` Jest częścią .NET Framework modelu obiektów schematu (SOM), który reprezentuje zestaw dokumentów schematu XSD. Aby utworzyć dokumenty XSD z `XmlSchemaSet`, Użyj kolekcji schematów <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> z właściwości `XmlSchemaSet` klasy. Następnie serializować każdy <xref:System.Xml.Schema.XmlSchema> obiekt <xref:System.Xml.Serialization.XmlSerializer>za pomocą.  
  
#### <a name="to-export-schemas"></a>Aby wyeksportować schematy  
  
1. Utwórz wystąpienie <xref:System.Runtime.Serialization.XsdDataContractExporter>obiektu.  
  
2. Opcjonalna. <xref:System.Xml.Schema.XmlSchemaSet> Przekaż w konstruktorze. W takim przypadku schemat wygenerowany podczas eksportowania schematu jest dodawany do tego <xref:System.Xml.Schema.XmlSchemaSet> wystąpienia zamiast od pustego. <xref:System.Xml.Schema.XmlSchemaSet>  
  
3. Opcjonalny. Wywołaj jedną z <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> metod. Metoda określa, czy można eksportować określony typ. Metoda ma takie same przeciążenia jak `Export` Metoda w następnym kroku.  
  
4. Wywołaj jedną z <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metod. Istnieją trzy <xref:System.Type>przeciążenia, <xref:System.Collections.Generic.List%601> a <xref:System.Collections.Generic.List%601>obiektylub `Type` obiekty<xref:System.Reflection.Assembly> . W ostatnim przypadku eksportowane są wszystkie typy we wszystkich określonych zestawach.  
  
     Wiele wywołań `Export` metody powoduje dodanie wielu elementów do tego samego `XmlSchemaSet`. Typ nie jest generowany w przypadku, `XmlSchemaSet` gdy już istnieje. W związku z `Export` tym, wywoływanie wielu `XsdDataContractExporter` wystąpień w tym samym czasie jest preferowany do `XsdDataContractExporter` utworzenia wielu instancji klasy. Pozwala to uniknąć generowania zduplikowanych typów schematów.  
  
    > [!NOTE]
    > Jeśli wystąpił błąd podczas eksportowania, `XmlSchemaSet` będzie on znajdować się w stanie nieprzewidywalnym.  
  
5. <xref:System.Xml.Schema.XmlSchemaSet> Dostęp<xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> do właściwości.  
  
## <a name="export-options"></a>Opcje eksportu  
 Można ustawić <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> Właściwość <xref:System.Runtime.Serialization.XsdDataContractExporter> nawystąpienieklasywcelukontrolowaniaróżnychaspektówprocesueksportu.<xref:System.Runtime.Serialization.ExportOptions> W tym celu można ustawić następujące opcje:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Ta kolekcja `Type` reprezentuje znane typy dla eksportowanych typów. (Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)). Te znane typy są eksportowane przy każdym `Export` wywołaniu oprócz typów przekazaną `Export` do metody.  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. <xref:System.Runtime.Serialization.IDataContractSurrogate> Można dostarczyć za pomocą tej właściwości, która dostosowuje proces eksportowania. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Domyślnie żaden Surogat nie jest używany.  
  
## <a name="helper-methods"></a>Metody pomocnika  
 Poza podstawową rolą eksportowania schematu, `XsdDataContractExporter` zapewnia kilka przydatnych metod pomocniczych, które dostarczają informacji o typach. Należą do nich następujące elementy:  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A>Method. Ta metoda przyjmuje `Type` i <xref:System.Xml.XmlQualifiedName> zwraca obiekt, który reprezentuje nazwę elementu głównego i przestrzeń nazw, które będą używane, jeśli ten typ został Zserializowany jako obiekt główny.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A>Method. Ta metoda przyjmuje `Type` i zwraca obiekt <xref:System.Xml.XmlQualifiedName> , który reprezentuje nazwę typu schematu XSD, który będzie używany, jeśli ten typ został wyeksportowany do schematu. W <xref:System.Xml.Serialization.IXmlSerializable> przypadku typów reprezentowanych jako typy anonimowe w schemacie `null`ta metoda zwraca.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A>Method. Ta metoda działa tylko z <xref:System.Xml.Serialization.IXmlSerializable> typami, które są reprezentowane jako typy anonimowe w schemacie, `null` i zwraca dla wszystkich innych typów. W przypadku typów anonimowych Metoda zwraca <xref:System.Xml.Schema.XmlSchemaType> , która reprezentuje daną. `Type`  
  
 Opcje eksportu mają wpływ na wszystkie te metody.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [importowanie i eksportowanie schematu](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Importowanie schematu w celu generowania klas](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
