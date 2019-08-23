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
ms.openlocfilehash: 2ea3bdea9c65b326953d16d7824114763ff4d017
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939409"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Weryfikowanie dokumentu XML w modelu DOM
<xref:System.Xml.XmlDocument> Klasa nie sprawdza poprawności kodu XML w Document Object Model (dom) w odniesieniu do języka definicji schematu XML (XSD) lub definicji typu dokumentu (DTD) domyślnie; plik XML jest weryfikowany tylko tak, aby był poprawnie sformułowany.  
  
 Aby sprawdzić poprawność kodu XML w modelu dom, można sprawdzić poprawność kodu XML w miarę ich ładowania do modelu Dom przez <xref:System.Xml.XmlReader> przekazanie <xref:System.Xml.XmlDocument.Load%2A> walidacji schematu <xref:System.Xml.XmlDocument> do metody klasy lub zweryfikowanie poprzednio niezweryfikowanego dokumentu XML w modelu dom przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> Metoda klasy.<xref:System.Xml.XmlDocument>  
  
## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Sprawdzanie poprawności dokumentu XML w trakcie jego ładowania do modelu DOM  
 Klasa sprawdza poprawność danych XML w miarę ich ładowania do modelu dom, gdy Walidacja <xref:System.Xml.XmlReader> jest przenoszona <xref:System.Xml.XmlDocument.Load%2A> <xref:System.Xml.XmlDocument> do metody klasy. <xref:System.Xml.XmlDocument>  
  
 Po pomyślnej weryfikacji ustawienia domyślne schematu są stosowane, wartości tekstowe są konwertowane na wartości niepodzielne w razie potrzeby, a informacje o typie są skojarzone z zweryfikowanymi elementami informacji. W związku z tym wpisane dane XML zastępują poprzednio niewpisane dane XML.  
  
### <a name="creating-an-xml-schema-validating-xmlreader"></a>Tworzenie schematu XML — Walidacja elementu XmlReader  
 Aby utworzyć sprawdzanie poprawności <xref:System.Xml.XmlReader>schematu XML, wykonaj następujące kroki.  
  
1. Utwórz nowe <xref:System.Xml.XmlReaderSettings> wystąpienie.  
  
2. Dodaj schemat XML do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości <xref:System.Xml.XmlReaderSettings> wystąpienia.  
  
3. `Schema` Określ<xref:System.Xml.XmlReaderSettings.ValidationType%2A>jako.  
  
4. Opcjonalnie można <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> określić i <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> a, aby obsługiwać błędy walidacji schematu i ostrzeżenia napotkane podczas walidacji.  
  
5. Na koniec przekazanie <xref:System.Xml.XmlReaderSettings> obiektu do <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader>metody klasy wraz z dokumentem XML, tworzenie walidacji schematu. <xref:System.Xml.XmlReader.Create%2A>  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie kodu, walidacja <xref:System.Xml.XmlReader> schematu sprawdza poprawność danych XML załadowanych do modelu DOM. Wprowadzono nieprawidłowe modyfikacje w dokumencie XML, a następnie dokument zostanie ponownie zweryfikowany, co spowoduje błędy walidacji schematu. Na koniec jeden z błędów zostanie poprawiony, a następnie część dokumentu XML jest częściowo zweryfikowana.  
  
 [!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
 [!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera `contosoBooks.xsd` również plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 Podczas sprawdzania poprawności danych XML, które są ładowane do modelu DOM, należy wziąć pod uwagę następujące kwestie.  
  
- W powyższym przykładzie <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest wywoływana przy każdym napotkaniu nieprawidłowego typu. Jeśli element <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> nie jest ustawiony w walidacji <xref:System.Xml.XmlReader>, <xref:System.Xml.Schema.XmlSchemaValidationException> jest zgłaszany, <xref:System.Xml.XmlDocument.Load%2A> gdy jest wywoływana, jeśli dowolny atrybut lub typ elementu nie jest zgodny z odpowiadającym mu typem określonym w schemacie walidacji.  
  
- Gdy dokument XML jest ładowany do <xref:System.Xml.XmlDocument> obiektu ze skojarzonym schematem, który definiuje wartości domyślne <xref:System.Xml.XmlDocument> , traktuje te wartości domyślne tak, jakby pojawiły się w dokumencie XML. Oznacza to, że <xref:System.Xml.XmlReader.IsEmptyElement%2A> Właściwość zawsze zwraca `false` dla elementu, który został domyślnie zwrócony ze schematu. Nawet jeśli w dokumencie XML, został on zapisany jako pusty element.  
  
## <a name="validating-an-xml-document-in-the-dom"></a>Weryfikowanie dokumentu XML w modelu DOM  
 Metoda klasy sprawdza poprawność danych XML załadowanych w modelu dom <xref:System.Xml.XmlDocument> względem <xref:System.Xml.XmlDocument.Schemas%2A> schematów we właściwości obiektu. <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Validate%2A> Po pomyślnej weryfikacji ustawienia domyślne schematu są stosowane, wartości tekstowe są konwertowane na wartości niepodzielne w razie potrzeby, a informacje o typie są skojarzone z zweryfikowanymi elementami informacji. W związku z tym wpisane dane XML zastępują poprzednio niewpisane dane XML.  
  
 Poniższy przykład jest podobny do przykładu w "Walidacja dokumentu XML, gdy jest ładowany do modelu DOM" powyżej. W tym przykładzie dokument XML nie jest weryfikowany, ponieważ jest ładowany do modelu dom, ale nie jest sprawdzany po załadowaniu do modelu dom przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. Metoda sprawdza poprawność dokumentu XML względem schematów XML zawartych <xref:System.Xml.XmlDocument.Schemas%2A> we właściwości <xref:System.Xml.XmlDocument>. <xref:System.Xml.XmlDocument.Validate%2A> W dokumencie XML wprowadzono nieprawidłowe modyfikacje, a następnie dokument zostanie ponownie zweryfikowany, co spowoduje błędy walidacji schematu. Na koniec jeden z błędów zostanie poprawiony, a następnie część dokumentu XML jest częściowo zweryfikowana.  
  
 [!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
 [!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]  
  
 Przykład przyjmuje jako dane wejściowe `contosoBooks.xml` i `contosoBooks.xsd` pliki, do których odwołuje się "Walidacja dokumentu XML, gdy jest ładowany do modelu dom" powyżej.  
  
## <a name="handling-validation-errors-and-warnings"></a>Obsługa błędów i ostrzeżeń walidacji  
 Błędy walidacji schematu XML są raportowane podczas walidacji danych XML załadowanych w modelu DOM. Otrzymasz powiadomienie o wszystkich błędach walidacji schematu podczas walidacji danych XML w trakcie ich ładowania lub podczas weryfikowania poprzednio niezweryfikowanego dokumentu XML.  
  
 Błędy sprawdzania poprawności są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler>. Jeśli obiekt <xref:System.Xml.Schema.ValidationEventHandler> został przypisany <xref:System.Xml.XmlReaderSettings> do wystąpienia lub przeszedł <xref:System.Xml.XmlDocument> do <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.Schema.XmlSchemaValidationException> klasy, <xref:System.Xml.Schema.ValidationEventHandler> będzie obsługiwać błędy walidacji schematu; w przeciwnym razie jest zgłaszany podczas walidacji schematu Wystąpił błąd.  
  
> [!NOTE]
> Dane XML są ładowane do modelu dom pomimo błędów walidacji schematu, chyba <xref:System.Xml.Schema.ValidationEventHandler> że wywołuje wyjątek, aby zatrzymać proces.  
>   
>  <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> Ostrzeżenia<xref:System.Xml.XmlReaderSettings> dotyczące walidacji schematu nie są zgłaszane, chyba że flaga zostanie określona dla obiektu.  
  
 Przykłady ilustrujące <xref:System.Xml.Schema.ValidationEventHandler>, zobacz "Walidacja dokumentu XML w trakcie jego ładowania do modelu dom" i "Walidacja dokumentu XML w modelu dom" powyżej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Praca ze schematami XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
