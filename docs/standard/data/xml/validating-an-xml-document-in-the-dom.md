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

<xref:System.Xml.XmlDocument> Klasa nie sprawdza poprawności kodu XML w Document Object Model (dom) w odniesieniu do języka definicji schematu XML (XSD) lub definicji typu dokumentu (DTD) domyślnie; KOD XML jest weryfikowany tylko jako prawidłowo sformułowany.

Aby sprawdzić poprawność kodu XML w modelu DOM, można sprawdzić poprawność kodu XML w miarę ich ładowania do modelu DOM przez <xref:System.Xml.XmlReader> przekazanie <xref:System.Xml.XmlDocument.Load%2A> walidacji schematu <xref:System.Xml.XmlDocument> do metody klasy lub zweryfikowanie wcześniej niezweryfikowanego dokumentu XML w modelu dom przy <xref:System.Xml.XmlDocument.Validate%2A> użyciu metody <xref:System.Xml.XmlDocument> klasy.

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a>Sprawdzanie poprawności dokumentu XML w trakcie jego ładowania do modelu DOM

<xref:System.Xml.XmlDocument> Klasa sprawdza poprawność danych XML w miarę ich ładowania do modelu dom, gdy Walidacja <xref:System.Xml.XmlReader> jest przenoszona <xref:System.Xml.XmlDocument.Load%2A> do metody <xref:System.Xml.XmlDocument> klasy.

Po pomyślnej weryfikacji ustawienia domyślne schematu są stosowane, wartości tekstowe są konwertowane na wartości niepodzielne w razie potrzeby, a informacje o typie są skojarzone z zweryfikowanymi elementami informacji. W związku z tym wpisane dane XML zastępują poprzednio niewpisane dane XML.

### <a name="creating-an-xml-schema-validating-xmlreader"></a>Tworzenie schematu XML — Walidacja elementu XmlReader

Aby utworzyć sprawdzanie poprawności <xref:System.Xml.XmlReader>schematu XML, wykonaj następujące kroki.

1. Utwórz nowe <xref:System.Xml.XmlReaderSettings> wystąpienie.

2. Dodaj schemat XML do <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości <xref:System.Xml.XmlReaderSettings> wystąpienia.

3. Określ `Schema` jako <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.

4. Opcjonalnie można <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> określić i <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> a, aby obsługiwać błędy walidacji schematu i ostrzeżenia napotkane podczas walidacji.

5. Na koniec przekazanie <xref:System.Xml.XmlReaderSettings> obiektu do <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy wraz z dokumentem XML, tworzenie walidacji <xref:System.Xml.XmlReader>schematu.

### <a name="example"></a>Przykład

W poniższym przykładzie kodu, walidacja <xref:System.Xml.XmlReader> schematu sprawdza poprawność danych XML załadowanych do modelu DOM. Wprowadzono nieprawidłowe modyfikacje w dokumencie XML, a następnie dokument zostanie ponownie zweryfikowany, co spowoduje błędy walidacji schematu. Na koniec jeden z błędów zostanie poprawiony, a następnie część dokumentu XML jest częściowo zweryfikowana.

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Przykład pobiera również `contosoBooks.xsd` plik jako dane wejściowe.

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

Podczas sprawdzania poprawności danych XML, które są ładowane do modelu DOM, należy wziąć pod uwagę następujące kwestie.

- W powyższym przykładzie <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest wywoływana przy każdym napotkaniu nieprawidłowego typu. Jeśli element <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> nie jest ustawiony w walidacji <xref:System.Xml.XmlReader>, <xref:System.Xml.Schema.XmlSchemaValidationException> jest zgłaszany, <xref:System.Xml.XmlDocument.Load%2A> gdy jest wywoływana, jeśli dowolny atrybut lub typ elementu nie jest zgodny z odpowiadającym mu typem określonym w schemacie walidacji.

- Gdy dokument XML jest ładowany do <xref:System.Xml.XmlDocument> obiektu ze skojarzonym schematem, który definiuje wartości domyślne, <xref:System.Xml.XmlDocument> traktuje te wartości domyślne tak, jakby pojawiły się w dokumencie XML. Oznacza to, że <xref:System.Xml.XmlReader.IsEmptyElement%2A> Właściwość zawsze zwraca `false` dla elementu, który został domyślnie zwrócony ze schematu. Nawet jeśli w dokumencie XML, został on zapisany jako pusty element.

## <a name="validating-an-xml-document-in-the-dom"></a>Weryfikowanie dokumentu XML w modelu DOM

<xref:System.Xml.XmlDocument.Validate%2A> Metoda <xref:System.Xml.XmlDocument> klasy sprawdza poprawność danych XML załadowanych w modelu dom względem schematów we <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> właściwości obiektu. Po pomyślnej weryfikacji ustawienia domyślne schematu są stosowane, wartości tekstowe są konwertowane na wartości niepodzielne w razie potrzeby, a informacje o typie są skojarzone z zweryfikowanymi elementami informacji. W związku z tym wpisane dane XML zastępują poprzednio niewpisane dane XML.

Poniższy przykład jest podobny do przykładu w "Walidacja dokumentu XML, gdy jest ładowany do modelu DOM" powyżej. W tym przykładzie dokument XML nie jest weryfikowany, ponieważ jest ładowany do modelu DOM, ale nie jest sprawdzany po załadowaniu do modelu DOM przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. <xref:System.Xml.XmlDocument.Validate%2A> Metoda sprawdza poprawność dokumentu XML względem schematów XML zawartych we <xref:System.Xml.XmlDocument.Schemas%2A> właściwości <xref:System.Xml.XmlDocument>. W dokumencie XML wprowadzono nieprawidłowe modyfikacje, a następnie dokument zostanie ponownie zweryfikowany, co spowoduje błędy walidacji schematu. Na koniec jeden z błędów zostanie poprawiony, a następnie część dokumentu XML jest częściowo zweryfikowana.

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

Przykład przyjmuje jako dane wejściowe `contosoBooks.xml` i `contosoBooks.xsd` pliki, do których odwołuje się "Walidacja dokumentu XML, gdy jest ładowany do modelu dom" powyżej.

## <a name="handling-validation-errors-and-warnings"></a>Obsługa błędów i ostrzeżeń walidacji

Błędy walidacji schematu XML są raportowane podczas walidacji danych XML załadowanych w modelu DOM. Otrzymasz powiadomienie o wszystkich błędach walidacji schematu podczas walidacji danych XML w trakcie ich ładowania lub podczas weryfikowania poprzednio niezweryfikowanego dokumentu XML.

Błędy sprawdzania poprawności są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler>. Jeśli element <xref:System.Xml.Schema.ValidationEventHandler> został przypisany <xref:System.Xml.XmlReaderSettings> do wystąpienia lub <xref:System.Xml.XmlDocument.Validate%2A> przeszedł do metody <xref:System.Xml.XmlDocument> klasy, <xref:System.Xml.Schema.ValidationEventHandler> będzie obsługiwać błędy walidacji schematu; w przeciwnym <xref:System.Xml.Schema.XmlSchemaValidationException> razie jest zgłaszany w przypadku napotkania błędu walidacji schematu.

> [!NOTE]
> Dane XML są ładowane do modelu DOM pomimo błędów walidacji schematu, chyba <xref:System.Xml.Schema.ValidationEventHandler> że wywołuje wyjątek, aby zatrzymać proces.
>
> Ostrzeżenia dotyczące walidacji schematu nie są zgłaszane <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> , chyba że flaga zostanie <xref:System.Xml.XmlReaderSettings> określona dla obiektu.

 Przykłady ilustrujące <xref:System.Xml.Schema.ValidationEventHandler>, zobacz "Walidacja dokumentu XML w trakcie jego ładowania do modelu dom" i "Walidacja dokumentu XML w modelu dom" powyżej.

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Praca ze schematami XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
