---
title: Weryfikowanie dokumentu XML w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0f5ae64eb1017570a56efab59a4bf1a66d5e02b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676353"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Weryfikowanie dokumentu XML w modelu DOM
<xref:System.Xml.XmlDocument> Klasy XML w modelu DOM (Document Object) względem schematu XML definicji język (XSD) schematu lub dokumentu definicja typu (DTD) domyślnie weryfikują dane XML tylko sprawdza się, jest poprawnie sformułowany.  
  
 Aby sprawdzić poprawność kodu XML w modelu DOM, można sprawdzić poprawność kodu XML zgodnie z ich załadowaniu do modelu DOM, przekazując, sprawdzanie poprawności schematu <xref:System.Xml.XmlReader> do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument> klasy lub sprawdzania poprawności wcześniej niezweryfikowanych dokumentu XML w modelu DOM przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Weryfikowanie dokumentu XML w postaci, w jakiej są ładowane do modelu DOM  
 <xref:System.Xml.XmlDocument> Klasy sprawdza poprawność danych XML, ponieważ został załadowany do modelu DOM, podczas sprawdzania poprawności <xref:System.Xml.XmlReader> jest przekazywany do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
 Po pomyślnej weryfikacji wartości domyślne schematu są stosowane wartości tekstowe są konwertowane na niepodzielne wartości zgodnie z potrzebami i informacje o typie jest skojarzone z elementami zweryfikowanych informacji. W rezultacie typizowanych danych XML zastępuje poprzednio bez typu danych XML.  
  
### <a name="creating-an-xml-schema-validating-xmlreader"></a>Tworzenie pliku XML sprawdzanie poprawności schematu elementu XmlReader  
 Aby utworzyć XML schematu weryfikacji <xref:System.Xml.XmlReader>, wykonaj następujące kroki.  
  
1.  Utworzyć nową <xref:System.Xml.XmlReaderSettings> wystąpienia.  
  
2.  Dodawanie schematu XML do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwość <xref:System.Xml.XmlReaderSettings> wystąpienia.  
  
3.  Określ `Schema` jako <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.  
  
4.  Opcjonalnie można określić <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> i <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> do obsługi schematu błędy i ostrzeżenia walidacji podczas sprawdzania poprawności.  
  
5.  Na koniec Przekaż <xref:System.Xml.XmlReaderSettings> obiekt <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy wraz z dokumentu XML, tworzenie, sprawdzanie poprawności schematu <xref:System.Xml.XmlReader>.  
  
### <a name="example"></a>Przykład  
 W przykładzie kodu, który następuje po sprawdzanie poprawności schematu <xref:System.Xml.XmlReader> sprawdza poprawność danych XML załadowane do modelu DOM. Nieprawidłowe zmiany zostaną wprowadzone do dokumentu XML i dokumentu jest następnie sprawdzony ponownie, powodując błędy sprawdzania poprawności schematu. Na koniec jeden z błędów jest usuwana, a następnie częściowo zweryfikowane części dokumentu XML.  
  
 [!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
 [!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Rozważ następujące opcje podczas sprawdzania poprawności danych XML, zgodnie z ich załadowaniu do modelu DOM.  
  
-   W powyższym przykładzie <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest wywoływany przy każdym napotkaniu nieprawidłowego typu. Jeśli <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> nie jest ustawiony na temat weryfikacji <xref:System.Xml.XmlReader>, <xref:System.Xml.Schema.XmlSchemaValidationException> jest generowany, gdy <xref:System.Xml.XmlDocument.Load%2A> jest wywoływana, jeśli dowolny typ atrybutu lub elementu nie jest zgodny z odpowiedniego typu, określona w schemacie sprawdzania poprawności.  
  
-   Podczas ładowania dokumentu XML do <xref:System.Xml.XmlDocument> obiektu za pomocą skojarzonego schematu, który definiuje wartości domyślne <xref:System.Xml.XmlDocument> traktuje te ustawienia domyślne tak, jakby były one wyświetlane w dokumencie XML. Oznacza to, że <xref:System.Xml.XmlReader.IsEmptyElement%2A> właściwość zawsze zwraca `false` element, który został przyjmujące wartości domyślne ze schematu. Nawet jeśli w dokumencie XML został on zapisany jako pusty element.  
  
## <a name="validating-an-xml-document-in-the-dom"></a>Weryfikowanie dokumentu XML w modelu DOM  
 <xref:System.Xml.XmlDocument.Validate%2A> Metody <xref:System.Xml.XmlDocument> klasy sprawdza poprawność danych XML załadowane w modelu DOM względem schematów w <xref:System.Xml.XmlDocument> obiektu <xref:System.Xml.XmlDocument.Schemas%2A> właściwości. Po pomyślnej weryfikacji wartości domyślne schematu są stosowane wartości tekstowe są konwertowane na niepodzielne wartości zgodnie z potrzebami i informacje o typie jest skojarzone z elementami zweryfikowanych informacji. W rezultacie typizowanych danych XML zastępuje poprzednio bez typu danych XML.  
  
 W poniższym przykładzie jest podobny do przykładu w "Sprawdzanie poprawności dokumentu jako go jest załadowana do modelu DOM języka XML" powyżej. W tym przykładzie dokumentu XML nie zostanie zweryfikowana podczas ładowania do modelu DOM, ale zamiast sprawdzania poprawności po ich załadowaniu do modelu DOM przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XmlDocument.Validate%2A> Metoda sprawdza dokumentu XML względem schematów XML zawartych w <xref:System.Xml.XmlDocument.Schemas%2A> właściwość <xref:System.Xml.XmlDocument>. Nieprawidłowy następnie modyfikacje wprowadza do dokumentu XML i dokumentu jest następnie sprawdzony ponownie, powodując błędy sprawdzania poprawności schematu. Na koniec jeden z błędów jest usuwana, a następnie częściowo zweryfikowane części dokumentu XML.  
  
 [!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]  
  
 Pobiera przykład jako dane wejściowe `contosoBooks.xml` i `contosoBooks.xsd` plików, o której mowa w "Sprawdzanie poprawności dokumentu jako go jest załadowana do modelu DOM języka XML" powyżej.  
  
## <a name="handling-validation-errors-and-warnings"></a>Obsługa błędy i ostrzeżenia walidacji  
 Błędy sprawdzania poprawności schematu XML są zgłaszane, gdy sprawdzanie poprawności danych XML załadowane w modelu DOM. Użytkownik jest powiadamiany o wszystkie błędy sprawdzania poprawności schematu, znaleziono podczas sprawdzania poprawności danych XML, gdy jest ładowany lub Sprawdzanie poprawności wcześniej niezweryfikowanych dokumentu XML.  
  
 Błędy sprawdzania poprawności są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler>. Jeśli <xref:System.Xml.Schema.ValidationEventHandler> został przypisany do <xref:System.Xml.XmlReaderSettings> wystąpienia lub przekazany do <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy, <xref:System.Xml.Schema.ValidationEventHandler> będzie obsługiwać błędy sprawdzania poprawności; w przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidationException> jest wywoływane, gdy Weryfikacja schematu Napotkano błąd.  
  
> [!NOTE]
>  Dane XML są ładowane do modelu DOM, pomimo błędy sprawdzania poprawności schematu, chyba że Twoje <xref:System.Xml.Schema.ValidationEventHandler> zgłasza wyjątek, aby zatrzymać proces.  
>   
>  Ostrzeżenia sprawdzania poprawności schematu nie są wyświetlane, chyba że <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> określono flagę <xref:System.Xml.XmlReaderSettings> obiektu.  
  
 Aby uzyskać przykłady ilustrujące <xref:System.Xml.Schema.ValidationEventHandler>, zobacz "Sprawdzanie poprawności dokumentu jako go jest załadowana do modelu DOM języka XML" i "Sprawdzanie poprawności dokumentu w modelu DOM języka XML" powyżej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XmlReader>  
- <xref:System.Xml.Schema.ValidationEventHandler>  
- <xref:System.Xml.XmlReaderSettings>  
- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
- [Praca ze schematami XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
