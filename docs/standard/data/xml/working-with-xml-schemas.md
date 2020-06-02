---
title: Praca ze schematami XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: f239d67d959c1f7a0bfebfaaaa49de9cf9c9a111
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281690"
---
# <a name="working-with-xml-schemas"></a>Praca ze schematami XML
Aby zdefiniować strukturę dokumentu XML, a także relacje elementów, typy danych i ograniczenia zawartości, należy użyć definicji typu dokumentu (DTD) lub schematu języka definicji schematu XML (XSD). Mimo że dokument XML jest uznawany za prawidłowo sformułowany, jeśli spełnia wszystkie wymagania składniowe zdefiniowane przez organizacja World Wide Web Consortium (W3C) XML (XML) 1,0 zalecenie, nie jest uważane za ważne, chyba że jest poprawnie sformułowany i jest zgodny z ograniczeniami zdefiniowanymi przez jego DTD lub schemat. W związku z tym, mimo że wszystkie prawidłowe dokumenty XML są poprawnie sformułowane, nie wszystkie poprawnie sformułowane dokumenty XML są prawidłowe.  
  
 Aby uzyskać więcej informacji na temat formatu XML, zobacz [zalecenia dotyczące W3C xml 1,0](https://www.w3.org/TR/REC-xml/). Aby uzyskać więcej informacji na temat schematu XML, zobacz [część 1 W3C XML schematu: rekomendacja struktury](https://www.w3.org/TR/xmlschema-1/) i [plik W3C XML schematu część 2: typy danych zalecenie](https://www.w3.org/TR/xmlschema-2/) zalecenia.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Model SOM (XML Schema Object Model)](xml-schema-object-model-som.md)  
 W tym artykule omówiono model obiektów schematu (SOM) w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw, który zawiera zestaw klas, które umożliwiają odczytywanie schematu języka definicji schematu (XSD) z pliku lub programowo Tworzenie schematu w pamięci.  
  
 [Klasa XmlSchemaSet na potrzeby kompilacji schematu](xmlschemaset-for-schema-compilation.md)  
 Omawia <xref:System.Xml.Schema.XmlSchemaSet> klasę, która jest pamięcią podręczną, w której można przechowywać i sprawdzać schematy XSD.  
  
 [Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator](xmlschemavalidator-push-based-validation.md)  
 Omawia <xref:System.Xml.Schema.XmlSchemaValidator> klasę, która zapewnia wydajny mechanizm o wysokiej wydajności do sprawdzania poprawności danych XML względem schematów XSD w sposób oparty na wypychaniu.  
  
 [Wnioskowanie schematu XML](inferring-an-xml-schema.md)  
 W tym artykule omówiono sposób użycia <xref:System.Xml.Schema.XmlSchemaInference> klasy do wywnioskowania schematu XSD ze struktury dokumentu XML.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Xml.Schema.XmlSchemaSet>&#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124;<xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Weryfikowanie dokumentu XML w modelu DOM](validating-an-xml-document-in-the-dom.md)  
 W tym artykule omówiono sposób sprawdzania poprawności kodu XML w Document Object Model (DOM). Możesz sprawdzić poprawność kodu XML w miarę jego ładowania do modelu DOM lub sprawdzić poprawność niezweryfikowanego dokumentu XML w modelu DOM.  
  
 [Weryfikacja schematu przy użyciu klasy XPathNavigator](schema-validation-using-xpathnavigator.md)  
 W tym artykule omówiono sposób sprawdzania poprawności kodu XML, który jest przeszukiwany i edytowany przy użyciu <xref:System.Xml.XPath.XPathNavigator> klasy.
