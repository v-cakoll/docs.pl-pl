---
title: Weryfikowanie dokumentu XML w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: 93686ddf1afff76926e77acdbf5aa58e93d6cb77
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710040"
---
# <a name="validating-an-xml-document-in-the-dom"></a>Weryfikowanie dokumentu XML w modelu DOM

Klasa<xref:System.Xml.XmlDocument> nie sprawdza poprawności kodu XML w Document Object Model (DOM) w odniesieniu do języka definicji schematu XML (XSD) lub definicji typu dokumentu (DTD) domyślnie; KOD XML jest weryfikowany tylko jako prawidłowo sformułowany.

Aby sprawdzić poprawność kodu XML w modelu DOM, można sprawdzić poprawność kodu XML w miarę jego ładowania do modelu DOM przez przekazanie <xref:System.Xml.XmlReader> sprawdzania poprawności schematu do metody <xref:System.Xml.XmlDocument.Load%2A> klasy <xref:System.Xml.XmlDocument> lub Walidacja wcześniej niezweryfikowanego dokumentu XML w modelu DOM przy użyciu metody <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument>.

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Sprawdzanie poprawności dokumentu XML w trakcie jego ładowania do modelu DOM

Klasa <xref:System.Xml.XmlDocument> sprawdza poprawność danych XML, ponieważ jest załadowana do modelu DOM, gdy Walidacja <xref:System.Xml.XmlReader> jest przenoszona do metody <xref:System.Xml.XmlDocument.Load%2A> klasy <xref:System.Xml.XmlDocument>.

Po pomyślnej weryfikacji ustawienia domyślne schematu są stosowane, wartości tekstowe są konwertowane na wartości niepodzielne w razie potrzeby, a informacje o typie są skojarzone z zweryfikowanymi elementami informacji. W związku z tym wpisane dane XML zastępują poprzednio niewpisane dane XML.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>Tworzenie schematu XML — Walidacja elementu XmlReader

Aby utworzyć schemat XML z walidacją <xref:System.Xml.XmlReader>, wykonaj następujące kroki.

1. Utwórz nowe wystąpienie <xref:System.Xml.XmlReaderSettings>.

2. Dodaj schemat XML do właściwości <xref:System.Xml.XmlReaderSettings.Schemas%2A> wystąpienia <xref:System.Xml.XmlReaderSettings>.

3. Określ `Schema` jako <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.

4. Opcjonalnie można określić <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> i <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> do obsługi błędów walidacji schematu i ostrzeżeń napotkanych podczas walidacji.

5. Na koniec przekaż obiekt <xref:System.Xml.XmlReaderSettings> do metody <xref:System.Xml.XmlReader.Create%2A> klasy <xref:System.Xml.XmlReader> wraz z dokumentem XML, tworząc <xref:System.Xml.XmlReader>sprawdzania poprawności schematu.

### <a name="example"></a>Przykład

W poniższym przykładzie kodu, sprawdzanie poprawności schematu <xref:System.Xml.XmlReader> sprawdza poprawność danych XML załadowanych do modelu DOM. Wprowadzono nieprawidłowe modyfikacje w dokumencie XML, a następnie dokument zostanie ponownie zweryfikowany, co spowoduje błędy walidacji schematu. Na koniec jeden z błędów zostanie poprawiony, a następnie część dokumentu XML jest częściowo zweryfikowana.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Przykład pobiera również plik `contosoBooks.xsd` jako dane wejściowe.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

Podczas sprawdzania poprawności danych XML, które są ładowane do modelu DOM, należy wziąć pod uwagę następujące kwestie.

- W powyższym przykładzie <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest wywoływana za każdym razem, gdy zostanie napotkany nieprawidłowy typ. Jeśli <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> nie jest ustawiona w <xref:System.Xml.XmlReader>walidacji, zostanie zgłoszony <xref:System.Xml.Schema.XmlSchemaValidationException>, <xref:System.Xml.XmlDocument.Load%2A> gdy atrybut lub typ elementu nie jest zgodny z odpowiadającym mu typem określonym w schemacie walidacji.

- Gdy dokument XML jest ładowany do obiektu <xref:System.Xml.XmlDocument> ze skojarzonym schematem, który definiuje wartości domyślne, <xref:System.Xml.XmlDocument> traktuje te wartości domyślne tak, jakby pojawiły się w dokumencie XML. Oznacza to, że właściwość <xref:System.Xml.XmlReader.IsEmptyElement%2A> zawsze zwraca `false` dla elementu, który został domyślnie zwrócony ze schematu. Nawet jeśli w dokumencie XML, został on zapisany jako pusty element.

## <a name="validating-an-xml-document-in-the-dom"></a>Weryfikowanie dokumentu XML w modelu DOM

Metoda <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument> sprawdza poprawność danych XML załadowanych w modelu DOM względem schematów we właściwości <xref:System.Xml.XmlDocument.Schemas%2A> obiektu <xref:System.Xml.XmlDocument>. Po pomyślnej weryfikacji ustawienia domyślne schematu są stosowane, wartości tekstowe są konwertowane na wartości niepodzielne w razie potrzeby, a informacje o typie są skojarzone z zweryfikowanymi elementami informacji. W związku z tym wpisane dane XML zastępują poprzednio niewpisane dane XML.

Poniższy przykład jest podobny do przykładu w "Walidacja dokumentu XML, gdy jest ładowany do modelu DOM" powyżej. W tym przykładzie dokument XML nie jest weryfikowany, ponieważ jest ładowany do modelu DOM, ale nie jest sprawdzany po załadowaniu do modelu DOM przy użyciu metody <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument>. Metoda <xref:System.Xml.XmlDocument.Validate%2A> sprawdza poprawność dokumentu XML względem schematów XML zawartych we właściwości <xref:System.Xml.XmlDocument.Schemas%2A> <xref:System.Xml.XmlDocument>. W dokumencie XML wprowadzono nieprawidłowe modyfikacje, a następnie dokument zostanie ponownie zweryfikowany, co spowoduje błędy walidacji schematu. Na koniec jeden z błędów zostanie poprawiony, a następnie część dokumentu XML jest częściowo zweryfikowana.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

Przykład przyjmuje jako dane wejściowe `contosoBooks.xml` i `contosoBooks.xsd` plików, do których odnosi się "Walidacja dokumentu XML, gdy jest ładowany do modelu DOM" powyżej.

## <a name="handling-validation-errors-and-warnings"></a>Obsługa błędów i ostrzeżeń walidacji

Błędy walidacji schematu XML są raportowane podczas walidacji danych XML załadowanych w modelu DOM. Otrzymasz powiadomienie o wszystkich błędach walidacji schematu podczas walidacji danych XML w trakcie ich ładowania lub podczas weryfikowania poprzednio niezweryfikowanego dokumentu XML.

Błędy sprawdzania poprawności są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler>. Jeśli <xref:System.Xml.Schema.ValidationEventHandler> zostało przypisane do wystąpienia <xref:System.Xml.XmlReaderSettings> lub przekazane do metody <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument>, <xref:System.Xml.Schema.ValidationEventHandler> będzie obsługiwać błędy walidacji schematu; w przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidationException> jest zgłaszane w przypadku napotkania błędu walidacji schematu.

> [!NOTE]
> Dane XML są ładowane do modelu DOM pomimo błędów walidacji schematu, chyba że <xref:System.Xml.Schema.ValidationEventHandler> zgłasza wyjątek, aby zatrzymać proces.
>
> Ostrzeżenia dotyczące walidacji schematu nie są zgłaszane, jeśli flaga <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> nie została określona do <xref:System.Xml.XmlReaderSettings> obiektu.

 Przykłady ilustrujące <xref:System.Xml.Schema.ValidationEventHandler>można znaleźć w sekcji "Walidacja dokumentu XML w trakcie jego ładowania do modelu DOM" i "Walidacja dokumentu XML w modelu DOM" powyżej.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Praca ze schematami XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
