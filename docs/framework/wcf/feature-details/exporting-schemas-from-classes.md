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
ms.openlocfilehash: d356450af8ce6690e2142f3487e153bcde095324
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595521"
---
# <a name="exporting-schemas-from-classes"></a>Eksportowanie schematów z klas
Aby wygenerować schematy języka definicji schematu XML (XSD) z klas, które są używane w modelu kontraktu danych, użyj <xref:System.Runtime.Serialization.XsdDataContractExporter> klasy. W tym temacie opisano proces tworzenia schematów.  
  
## <a name="the-export-process"></a>Proces eksportowania  
 Proces eksportowania schematu rozpoczyna się od jednego lub kilku typów i tworzy <xref:System.Xml.Schema.XmlSchemaSet> , który opisuje projekcję XML tych typów.  
  
 `XmlSchemaSet`Jest częścią .NET Framework modelu obiektów schematu (SOM), który reprezentuje zestaw dokumentów schematu XSD. Aby utworzyć dokumenty XSD z `XmlSchemaSet` , Użyj kolekcji schematów z <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości `XmlSchemaSet` klasy. Następnie serializować każdy <xref:System.Xml.Schema.XmlSchema> obiekt za pomocą <xref:System.Xml.Serialization.XmlSerializer> .  
  
#### <a name="to-export-schemas"></a>Aby wyeksportować schematy  
  
1. Utwórz wystąpienie elementu <xref:System.Runtime.Serialization.XsdDataContractExporter>.  
  
2. Opcjonalny. Przekaż <xref:System.Xml.Schema.XmlSchemaSet> w konstruktorze. W takim przypadku schemat wygenerowany podczas eksportowania schematu jest dodawany do tego <xref:System.Xml.Schema.XmlSchemaSet> wystąpienia zamiast od pustego <xref:System.Xml.Schema.XmlSchemaSet> .  
  
3. Opcjonalny. Wywołaj jedną z <xref:System.Runtime.Serialization.XsdDataContractExporter.CanExport%2A> metod. Metoda określa, czy można eksportować określony typ. Metoda ma takie same przeciążenia jak `Export` Metoda w następnym kroku.  
  
4. Wywołaj jedną z <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metod. Istnieją trzy przeciążenia <xref:System.Type> , a <xref:System.Collections.Generic.List%601> `Type` obiekty lub <xref:System.Collections.Generic.List%601> <xref:System.Reflection.Assembly> obiekty. W ostatnim przypadku eksportowane są wszystkie typy we wszystkich określonych zestawach.  
  
     Wiele wywołań `Export` metody powoduje dodanie wielu elementów do tego samego `XmlSchemaSet` . Typ nie jest generowany w przypadku, `XmlSchemaSet` gdy już istnieje. W związku z tym, wywoływanie `Export` wielu wystąpień w tym samym czasie `XsdDataContractExporter` jest preferowany do utworzenia wielu instancji `XsdDataContractExporter` klasy. Pozwala to uniknąć generowania zduplikowanych typów schematów.  
  
    > [!NOTE]
    > Jeśli wystąpił błąd podczas eksportowania, `XmlSchemaSet` będzie on znajdować się w stanie nieprzewidywalnym.  
  
5. Dostęp do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> właściwości.  
  
## <a name="export-options"></a>Opcje eksportu  
 Można ustawić <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> Właściwość <xref:System.Runtime.Serialization.XsdDataContractExporter> na wystąpienie <xref:System.Runtime.Serialization.ExportOptions> klasy w celu kontrolowania różnych aspektów procesu eksportu. W tym celu można ustawić następujące opcje:  
  
- <xref:System.Runtime.Serialization.ExportOptions.KnownTypes%2A>. Ta kolekcja `Type` reprezentuje znane typy dla eksportowanych typów. (Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](data-contract-known-types.md)). Te znane typy są eksportowane przy każdym `Export` wywołaniu oprócz typów przekazaną do `Export` metody.  
  
- <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A>. <xref:System.Runtime.Serialization.IDataContractSurrogate>Można dostarczyć za pomocą tej właściwości, która dostosowuje proces eksportowania. Aby uzyskać więcej informacji, zobacz [surogaty kontraktu danych](../extending/data-contract-surrogates.md). Domyślnie żaden Surogat nie jest używany.  
  
## <a name="helper-methods"></a>Metody pomocnika  
 Poza podstawową rolą eksportowania schematu, `XsdDataContractExporter` zapewnia kilka przydatnych metod pomocniczych, które dostarczają informacji o typach. Należą do nich następujące elementy:  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetRootElementName%2A>Method. Ta metoda przyjmuje `Type` i zwraca obiekt <xref:System.Xml.XmlQualifiedName> , który reprezentuje nazwę elementu głównego i przestrzeń nazw, które będą używane, jeśli ten typ został Zserializowany jako obiekt główny.  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaTypeName%2A>Method. Ta metoda przyjmuje `Type` i zwraca obiekt <xref:System.Xml.XmlQualifiedName> , który reprezentuje nazwę typu schematu XSD, który będzie używany, jeśli ten typ został wyeksportowany do schematu. <xref:System.Xml.Serialization.IXmlSerializable>W przypadku typów reprezentowanych jako typy anonimowe w schemacie ta metoda zwraca `null` .  
  
- <xref:System.Runtime.Serialization.XsdDataContractExporter.GetSchemaType%2A>Method. Ta metoda działa tylko z <xref:System.Xml.Serialization.IXmlSerializable> typami, które są reprezentowane jako typy anonimowe w schemacie, i zwraca `null` dla wszystkich innych typów. W przypadku typów anonimowych Metoda zwraca, <xref:System.Xml.Schema.XmlSchemaType> która reprezentuje daną `Type` .  
  
 Opcje eksportu mają wpływ na wszystkie te metody.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [importowanie i eksportowanie schematu](schema-import-and-export.md)
- [Importowanie schematu w celu generowania klas](importing-schema-to-generate-classes.md)
