---
title: Praca ze schematami XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83fddd00f44b184fa066f6c47b90b01fac7ef7bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959118"
---
# <a name="working-with-xml-schemas"></a>Praca ze schematami XML
Aby zdefiniować strukturę dokumentu XML, a także jej relacje elementu, typów danych oraz ograniczenia zawartości, należy użyć definicji typu dokumentu (DTD) lub schematu języka (XSD) definicji schematu XML. Mimo że dokument XML jest uważany za poprawnie sformułowane, jeśli dana jednostka spełnia wszystkie wymagania syntaktycznych zdefiniowane przez konsorcjum World Wide Web Consortium (W3C) języka XML (Extensible Markup) 1.0 zalecenia, nie wydaje się prawidłowe, chyba że jest poprawnie sformułowany i jest zgodna z ograniczeń zdefiniowanych przez jego DTD lub schematu. W związku z tym mimo że wszystkie ważne dokumenty XML są poprawnie sformułowany, nie wszystkie poprawnie sformułowany dokumentów XML są prawidłowe.  
  
 Aby uzyskać więcej informacji na temat XML, zobacz [zalecenia 1.0 W3C XML](https://www.w3.org/TR/REC-xml/). Aby uzyskać więcej informacji na temat schematu XML, zobacz [W3C XML schematu część 1: Zalecenie struktur](https://www.w3.org/TR/xmlschema-1/) i [W3C XML schematu część 2: Typy danych zalecenie](https://www.w3.org/TR/xmlschema-2/) zalecenia.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 W tym artykule omówiono w modelu obiektów schematu (SOM) <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, który zawiera zestaw klas, która umożliwia odczytywanie schematu języka (XSD) definicji schematu z pliku lub programowo utworzyć schemat w pamięci.  
  
 [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 W tym artykule omówiono <xref:System.Xml.Schema.XmlSchemaSet> klasy, to znaczy, pamięci podręcznej, gdzie schematy XSD mogą być przechowywane i zweryfikowane.  
  
 [Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 W tym artykule omówiono <xref:System.Xml.Schema.XmlSchemaValidator> klasę, która zapewnia efektywny, wydajny mechanizm weryfikacji danych XML względem schematów XSD w sposób, na podstawie wypychania.  
  
 [Wnioskowanie schematu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 W tym artykule omówiono sposób używania <xref:System.Xml.Schema.XmlSchemaInference> klasy na potrzeby wnioskowania dotyczącego schematu XSD ze struktury dokumentu XML.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Weryfikowanie dokumentu XML w modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 W tym artykule omówiono sposób sprawdzania poprawności kodu XML w modelu DOM (Document Object). Sprawdzanie poprawności kodu XML, zgodnie z ich załadowaniu do modelu DOM lub Sprawdź poprawność wcześniej niezweryfikowanych dokumentu XML w modelu DOM.  
  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 W tym artykule omówiono sposób sprawdzania poprawności XML jest przejście i edytowane przy użyciu <xref:System.Xml.XPath.XPathNavigator> klasy.
