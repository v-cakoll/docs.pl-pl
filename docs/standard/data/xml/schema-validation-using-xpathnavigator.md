---
title: Weryfikacja schematu przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: bfcbf7306e896af54808c49e25f95d0631f5bcc0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710209"
---
# <a name="schema-validation-using-xpathnavigator"></a>Weryfikacja schematu przy użyciu klasy XPathNavigator
Korzystając z klasy <xref:System.Xml.XmlDocument>, można sprawdzić poprawność zawartości XML zawartej w obiekcie <xref:System.Xml.XmlDocument> na dwa sposoby. Pierwszy sposób polega na sprawdzeniu poprawności zawartości XML przy użyciu walidacji obiektu <xref:System.Xml.XmlReader>, a drugi — do użycia metody <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument>. Można również wykonać walidację zawartości XML tylko do odczytu przy użyciu klasy <xref:System.Xml.XPath.XPathDocument>.  
  
## <a name="validating-xml-data"></a>Walidacja danych XML  
 Klasa <xref:System.Xml.XmlDocument> nie sprawdza poprawności dokumentu XML przy użyciu opcji walidacji schematu języka definicji schematu XML (XSD). Sprawdza tylko, czy dokument XML jest poprawnie sformułowany.  
  
 Pierwszy sposób sprawdzania poprawności dokumentu XML polega na sprawdzeniu, czy dokument jest ładowany do obiektu <xref:System.Xml.XmlDocument> przy użyciu walidacji obiektu <xref:System.Xml.XmlReader>. Drugi sposób polega na sprawdzeniu, czy niewpisany wcześniej dokument XML przy użyciu metody <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument>. W obu przypadkach zmiany zweryfikowanego dokumentu XML mogą być ponownie weryfikowane przy użyciu metody <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument>.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Sprawdzanie poprawności dokumentu w trakcie jego ładowania  
 Sprawdzanie poprawności obiektu <xref:System.Xml.XmlReader> jest tworzone przez przekazanie obiektu <xref:System.Xml.XmlReaderSettings> do metody <xref:System.Xml.XmlReader.Create%2A> klasy <xref:System.Xml.XmlReader>, która przyjmuje obiekt <xref:System.Xml.XmlReaderSettings> jako parametr. Obiekt <xref:System.Xml.XmlReaderSettings> przeszedł jako parametr ma właściwość <xref:System.Xml.XmlReaderSettings.ValidationType%2A> ustawioną na `Schema` i schemat XML dla dokumentu XML zawartego w obiekcie <xref:System.Xml.XmlDocument> dodany do jego właściwości <xref:System.Xml.XmlReaderSettings.Schemas%2A>. Obiekt <xref:System.Xml.XmlReader> walidacji jest następnie używany do tworzenia obiektu <xref:System.Xml.XmlDocument>.  
  
 Poniższy przykład sprawdza poprawność pliku `contosoBooks.xml`, gdy jest ładowany do obiektu <xref:System.Xml.XmlDocument> przez utworzenie obiektu <xref:System.Xml.XmlDocument> przy użyciu walidacji obiektu <xref:System.Xml.XmlReader>. Ponieważ dokument XML jest prawidłowy zgodnie ze schematem, nie są generowane żadne błędy walidacji schematu ani Ostrzeżenia.  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 W powyższym przykładzie <xref:System.Xml.Schema.XmlSchemaValidationException> zostanie wygenerowany, gdy zostanie wywołane <xref:System.Xml.XmlDocument.Load%2A>, jeśli którykolwiek typ atrybutu lub elementu nie pasuje do odpowiedniego typu określonego w schemacie walidacji. Jeśli <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest ustawiona na <xref:System.Xml.XmlReader>sprawdzania poprawności, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> będzie wywoływana za każdym razem, gdy zostanie napotkany nieprawidłowy typ.  
  
 <xref:System.Xml.Schema.XmlSchemaException> zostanie wygenerowany, gdy do <xref:System.Xml.XPath.XPathNavigator>zostanie uzyskany dostęp do atrybutu lub elementu z <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>m ustawionym na `invalid`.  
  
 Właściwość <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> może służyć do określenia, czy pojedynczy atrybut lub element jest prawidłowy podczas uzyskiwania dostępu do atrybutów lub elementów z <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
> Gdy dokument XML jest ładowany do obiektu <xref:System.Xml.XmlDocument> ze skojarzonym schematem, który definiuje wartości domyślne, obiekt <xref:System.Xml.XmlDocument> traktuje te wartości domyślne tak, jakby pojawiły się w dokumencie XML. Oznacza to, że właściwość <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> zawsze zwraca `false` dla elementu, który został domyślnie wykonany ze schematu, nawet jeśli w dokumencie XML został zapisany jako pusty element.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Walidacja dokumentu przy użyciu metody weryfikacji  
 Metoda <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument> sprawdza poprawność dokumentu XML zawartego w obiekcie <xref:System.Xml.XmlDocument> względem schematów określonych we właściwości <xref:System.Xml.XmlDocument.Schemas%2A> obiektu <xref:System.Xml.XmlDocument> i wykonuje rozszerzenie sprawdzonych. Wynikiem jest poprzednio nieokreślony dokument XML w obiekcie <xref:System.Xml.XmlDocument> zastąpiony dokumentem o określonym typie.  
  
 Obiekt <xref:System.Xml.XmlDocument> zgłasza błędy walidacji schematu i ostrzeżenia przy użyciu delegata <xref:System.Xml.Schema.ValidationEventHandler> przekazaną jako parametr do metody <xref:System.Xml.XmlDocument.Validate%2A>.  
  
 Poniższy przykład sprawdza poprawność pliku `contosoBooks.xml` zawartego w obiekcie <xref:System.Xml.XmlDocument> względem schematu `contosoBooks.xsd` zawartego we właściwości <xref:System.Xml.XmlDocument.Schemas%2A> obiektu <xref:System.Xml.XmlDocument>.  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Weryfikowanie modyfikacji  
 Po wprowadzeniu modyfikacji do dokumentu XML można sprawdzić poprawność modyfikacji schematu dla dokumentu XML przy użyciu metody <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument>.  
  
 Poniższy przykład sprawdza poprawność pliku `contosoBooks.xml`, gdy jest ładowany do obiektu <xref:System.Xml.XmlDocument> przez utworzenie obiektu <xref:System.Xml.XmlDocument> przy użyciu walidacji obiektu <xref:System.Xml.XmlReader>. Dokument XML zostanie zweryfikowany pomyślnie, ponieważ jest załadowany bez generowania błędów walidacji schematu lub ostrzeżeń. W przykładzie są wprowadzane dwie modyfikacje dokumentu XML, które są nieprawidłowe zgodnie ze schematem `contosoBooks.xsd`. Pierwsza modyfikacja powoduje wstawienie nieprawidłowego elementu podrzędnego w wyniku błędu walidacji schematu, a druga zmiana ustawia wartość węzła określonego przez wartość, która jest nieprawidłowa w zależności od typu węzła, w wyniku wyjątku.  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 W powyższym przykładzie dwa modyfikacje są wprowadzane do dokumentu XML zawartego w obiekcie <xref:System.Xml.XmlDocument>. Po załadowaniu dokumentu XML wszelkie napotkane błędy walidacji schematu byłyby obsługiwane przez metodę obsługi zdarzeń walidacji i zapisywane w konsoli.  
  
 W tym przykładzie błędy walidacji zostały wprowadzone po załadowaniu dokumentu XML i zostały znalezione przy użyciu metody <xref:System.Xml.XmlDocument.Validate%2A> klasy <xref:System.Xml.XmlDocument>.  
  
 Modyfikacje wprowadzone przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> klasy <xref:System.Xml.XPath.XPathNavigator> spowodowały <xref:System.InvalidCastException>, ponieważ nowa wartość była nieprawidłowa przy uwzględnieniu typu schematu węzła.  
  
 Aby uzyskać więcej informacji na temat modyfikowania wartości przy użyciu metody <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, zobacz temat [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
### <a name="read-only-validation"></a>Walidacja tylko do odczytu  
 Klasa <xref:System.Xml.XPath.XPathDocument> jest reprezentacją w pamięci dokumentu XML tylko do odczytu. Zarówno Klasa <xref:System.Xml.XPath.XPathDocument>, jak i Klasa <xref:System.Xml.XmlDocument> tworzą <xref:System.Xml.XPath.XPathNavigator> obiekty do nawigowania i edytowania dokumentów XML. Ponieważ Klasa <xref:System.Xml.XPath.XPathDocument> jest klasą tylko do odczytu, obiekt <xref:System.Xml.XPath.XPathNavigator> zwrócony z <xref:System.Xml.XPath.XPathDocument> obiektów nie może edytować dokumentu XML zawartego w obiekcie <xref:System.Xml.XPath.XPathDocument>.  
  
 W przypadku weryfikacji można utworzyć obiekt <xref:System.Xml.XPath.XPathDocument> tak samo jak w przypadku tworzenia obiektu <xref:System.Xml.XmlDocument> przy użyciu walidacji obiektu <xref:System.Xml.XmlReader>, jak opisano wcześniej w tym temacie. Obiekt <xref:System.Xml.XPath.XPathDocument> sprawdza poprawność dokumentu XML w trakcie jego ładowania, ale ponieważ nie można edytować danych XML w obiekcie <xref:System.Xml.XPath.XPathDocument>, nie można ponownie sprawdzić poprawności dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat obiektów <xref:System.Xml.XPath.XPathNavigator> tylko do odczytu i edytowalnych, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
