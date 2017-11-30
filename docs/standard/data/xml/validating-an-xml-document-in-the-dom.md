---
title: "Sprawdzanie poprawności dokumentu XML w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 51ca7b5d18e4b664fcc5a56f7de004c42cb95c9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="validating-an-xml-document-in-the-dom"></a>Sprawdzanie poprawności dokumentu XML w modelu DOM
<xref:System.Xml.XmlDocument> Klasy nie można zweryfikować XML w modelu DOM (Document Object) względem schematu XML definition language (XSD) schemat lub dokument definicji typu (DTD) domyślnie; XML tylko zweryfikowaniu jest poprawnie sformułowany.  
  
 Aby sprawdzić poprawność kodu XML w modelu DOM, można sprawdzić poprawność pliku XML jako jest załadowane do modelu DOM, przekazując sprawdzanie poprawności schematu <xref:System.Xml.XmlReader> do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument> klasy lub sprawdzania poprawności wcześniej niezweryfikowanych dokumentu XML w modelu DOM przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Sprawdzanie poprawności dokument XML, ponieważ została załadowana do modelu DOM  
 <xref:System.Xml.XmlDocument> Klasy sprawdza poprawność danych XML, ponieważ jest on ładowany do modelu DOM, podczas sprawdzania poprawności <xref:System.Xml.XmlReader> jest przekazywana do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
 Po sprawdzeniu poprawności schematu wartości domyślne są stosowane wartości tekstowe są konwertowane na atomic wartości zgodnie z potrzebami i informacje o typie jest skojarzony z elementami zweryfikowanych informacji. W związku z tym typu danych XML zastępuje wcześniej bez typu danych XML.  
  
### <a name="creating-an-xml-schema-validating-xmlreader"></a>Tworzenie XML XmlReader sprawdzanie poprawności schematu  
 Aby utworzyć XML schematu weryfikacji <xref:System.Xml.XmlReader>, wykonaj następujące kroki.  
  
1.  Utworzyć nową <xref:System.Xml.XmlReaderSettings> wystąpienia.  
  
2.  Schemat XML, aby dodać <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> wystąpienia.  
  
3.  Określ `Schema` jako <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.  
  
4.  Opcjonalnie można określić <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> i <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> do obsługi błędów sprawdzania poprawności schematu i ostrzeżenia podczas sprawdzania poprawności.  
  
5.  Na koniec przekazać <xref:System.Xml.XmlReaderSettings> do obiektu <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy wraz z dokumentu w formacie XML, tworzenie, sprawdzanie poprawności schematu <xref:System.Xml.XmlReader>.  
  
### <a name="example"></a>Przykład  
 W przykładzie poniżej, sprawdzanie poprawności schematu <xref:System.Xml.XmlReader> sprawdza poprawność danych XML załadowane do modelu DOM. Nieprawidłowe modyfikacje są dokonywane w dokumencie XML i dokumentu jest następnie sprawdzony ponownie, powodując błędy sprawdzania poprawności schematu. Na koniec jeden z błędów jest usuwana, a następnie częściowo zweryfikowane części dokumentu XML.  
  
 [!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
 [!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład również przyjmuje `contosoBooks.xsd` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Należy rozważyć podczas sprawdzania poprawności danych XML, ponieważ jest on ładowany do modelu DOM.  
  
-   W powyższym przykładzie <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest wywoływana, gdy napotkano nieprawidłowy typ. Jeśli <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> nie jest ustawiona na weryfikacji <xref:System.Xml.XmlReader>, <xref:System.Xml.Schema.XmlSchemaValidationException> jest generowany, gdy <xref:System.Xml.XmlDocument.Load%2A> nosi nazwę dowolnego typu elementu lub atrybutu jest niezgodny z danego typu określonego w sprawdzania poprawności schematu.  
  
-   Gdy dokument XML jest ładowany do <xref:System.Xml.XmlDocument> obiektu o skojarzony schemat, który definiuje wartości domyślne <xref:System.Xml.XmlDocument> traktuje te wartości domyślne, jak gdyby znajdowały się one w dokumencie XML. Oznacza to, że <xref:System.Xml.XmlReader.IsEmptyElement%2A> właściwość zawsze zwraca `false` elementu była ustawiana domyślnie na podstawie schematu. Nawet jeśli w dokumencie XML został zapisany jako pustego elementu.  
  
## <a name="validating-an-xml-document-in-the-dom"></a>Sprawdzanie poprawności dokumentu XML w modelu DOM  
 <xref:System.Xml.XmlDocument.Validate%2A> Metody <xref:System.Xml.XmlDocument> klasa sprawdza poprawność danych XML załadowany w modelu DOM względem schematów w <xref:System.Xml.XmlDocument> obiektu <xref:System.Xml.XmlDocument.Schemas%2A> właściwości. Po sprawdzeniu poprawności schematu wartości domyślne są stosowane wartości tekstowe są konwertowane na atomic wartości zgodnie z potrzebami i informacje o typie jest skojarzony z elementami zweryfikowanych informacji. W związku z tym typu danych XML zastępuje wcześniej bez typu danych XML.  
  
 W poniższym przykładzie jest podobny do przykładu w "Sprawdzanie poprawności XML dokumentu jako jego jest załadowane do modelu DOM" powyżej. W tym przykładzie dokumentu XML nie jest weryfikowany jako jest ładowany do modelu DOM, ale raczej sprawdzania poprawności po załadowaniu do modelu DOM przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XmlDocument.Validate%2A> Metoda sprawdza względem schematów XML zawarte w dokumencie XML <xref:System.Xml.XmlDocument.Schemas%2A> właściwość <xref:System.Xml.XmlDocument>. Nieprawidłowy się następnie zmiany w dokumencie XML, a dokument jest następnie sprawdzony ponownie, powodując błędy sprawdzania poprawności schematu. Na koniec jeden z błędów jest usuwana, a następnie częściowo zweryfikowane części dokumentu XML.  
  
 [!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]  
  
 Ma przykład jako dane wejściowe `contosoBooks.xml` i `contosoBooks.xsd` plików określonych w "Sprawdzanie poprawności XML dokumentu jako jego jest załadowane do modelu DOM" powyżej.  
  
## <a name="handling-validation-errors-and-warnings"></a>Obsługa błędów sprawdzania poprawności i ostrzeżenia  
 Błędy sprawdzania poprawności schematu XML są zgłaszane po załadowaniu sprawdzanie poprawności danych XML w modelu DOM. Użytkownik jest powiadamiany o wszystkich błędy sprawdzania poprawności schematu znaleziono podczas sprawdzania poprawności danych XML, gdy jest ładowany lub sprawdzania poprawności wcześniej niezweryfikowanych dokumentu XML.  
  
 Błędy sprawdzania poprawności są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler>. Jeśli <xref:System.Xml.Schema.ValidationEventHandler> została przypisana do <xref:System.Xml.XmlReaderSettings> wystąpienia, lub przekazany do <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy <xref:System.Xml.Schema.ValidationEventHandler> obsłuży błędy sprawdzania poprawności schematu; w przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidationException> jest wywoływane, gdy Weryfikacja schematu Napotkano błąd.  
  
> [!NOTE]
>  Danych XML jest załadowane do modelu DOM pomimo błędy sprawdzania poprawności schematu, chyba że Twoje <xref:System.Xml.Schema.ValidationEventHandler> zgłasza wyjątek, aby zatrzymać proces.  
>   
>  Ostrzeżenia sprawdzania poprawności schematu nie są wyświetlane, chyba że <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> określono flagę <xref:System.Xml.XmlReaderSettings> obiektu.  
  
 Aby uzyskać przykłady ilustrujące <xref:System.Xml.Schema.ValidationEventHandler>, zobacz "Sprawdzanie poprawności XML dokumentu jako jego jest załadowane do modelu DOM" i "Sprawdzanie poprawności XML dokumentu w modelu DOM" powyżej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.ValidationEventHandler>  
 <xref:System.Xml.XmlReaderSettings>  
 [Przetwarzania danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [Praca z schematy XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
