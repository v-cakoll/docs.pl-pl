---
title: Weryfikacja schematu przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0199efb172466305af22c4ade7c47115a5cefd8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939620"
---
# <a name="schema-validation-using-xpathnavigator"></a>Weryfikacja schematu przy użyciu klasy XPathNavigator
Korzystając z <xref:System.Xml.XmlDocument> klasy, można sprawdzić poprawność zawartości XML zawartej <xref:System.Xml.XmlDocument> w obiekcie na dwa sposoby. Pierwszym sposobem jest zweryfikowanie zawartości XML przy użyciu obiektu sprawdzającego <xref:System.Xml.XmlReader> poprawność, a drugi — <xref:System.Xml.XmlDocument.Validate%2A> użycie metody <xref:System.Xml.XmlDocument> klasy. Można również wykonać walidację zawartości XML tylko do odczytu przy użyciu <xref:System.Xml.XPath.XPathDocument> klasy.  
  
## <a name="validating-xml-data"></a>Walidacja danych XML  
 <xref:System.Xml.XmlDocument> Klasa nie sprawdza poprawności dokumentu XML przy użyciu opcji walidacji schematu języka definicji schematu XML (XSD). Sprawdza tylko, czy dokument XML jest poprawnie sformułowany.  
  
 Pierwszy sposób sprawdzania poprawności dokumentu XML polega na sprawdzeniu, czy dokument jest ładowany do <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu. Drugi sposób polega na sprawdzeniu, czy niewpisany wcześniej dokument XML przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. W obu przypadkach zmiany zweryfikowanego dokumentu XML mogą być ponownie weryfikowane przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Sprawdzanie poprawności dokumentu w trakcie jego ładowania  
 Obiekt <xref:System.Xml.XmlReader> walidacji jest tworzony przez <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReaderSettings> przekazanie obiektu <xref:System.Xml.XmlReader> do metody klasy, która przyjmuje <xref:System.Xml.XmlReaderSettings> obiekt jako parametr. `Schema` <xref:System.Xml.XmlReaderSettings.ValidationType%2A> <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.XmlDocument> Obiekt przeszedł jako parametr ma ustawioną właściwość i schemat XML dla dokumentu XML zawartego w obiekcie dodanym do jego właściwości. <xref:System.Xml.XmlReaderSettings> Obiekt walidacji <xref:System.Xml.XmlReader> jest następnie używany do <xref:System.Xml.XmlDocument> tworzenia obiektu.  
  
 Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku w trakcie jego ładowania <xref:System.Xml.XmlDocument> do obiektu przez utworzenie <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu. Ponieważ dokument XML jest prawidłowy zgodnie ze schematem, nie są generowane żadne błędy walidacji schematu ani Ostrzeżenia.  
  
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
  
 Przykład pobiera `contosoBooks.xsd` również jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 W powyższym przykładzie <xref:System.Xml.Schema.XmlSchemaValidationException> zostanie wygenerowany, gdy <xref:System.Xml.XmlDocument.Load%2A> jest wywoływana, jeśli dowolny atrybut lub typ elementu nie pasuje do odpowiedniego typu określonego w schemacie walidacji. Jeśli jest ustawiona dla walidacji <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> zostanie wywołane przy każdym napotkaniu nieprawidłowego typu. <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>  
  
 Zostanie wygenerowany, gdy atrybut lub element z <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> ustawionym <xref:System.Xml.XPath.XPathNavigator>na `invalid` jest dostępny przez. <xref:System.Xml.Schema.XmlSchemaException>  
  
 Właściwość może służyć do określenia, czy pojedynczy atrybut lub element jest prawidłowy podczas uzyskiwania dostępu do atrybutów lub elementów <xref:System.Xml.XPath.XPathNavigator>za pomocą. <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A>  
  
> [!NOTE]
> Gdy dokument XML jest ładowany do <xref:System.Xml.XmlDocument> obiektu ze skojarzonym schematem, który definiuje wartości domyślne <xref:System.Xml.XmlDocument> , obiekt traktuje te wartości domyślne tak, jakby pojawiły się w dokumencie XML. Oznacza to, że <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> Właściwość zawsze zwraca `false` dla elementu, który został domyślnie zwrócony ze schematu, nawet jeśli w dokumencie XML został zapisany jako pusty element.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Walidacja dokumentu przy użyciu metody weryfikacji  
 <xref:System.Xml.XmlDocument.Schemas%2A> <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> Metoda klasy sprawdza poprawność dokumentu XML zawartego w obiekcie względem schematów określonych we właściwości obiektu i wykonuje rozszerzanie sprawdzonych. <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Validate%2A> Wynikiem jest poprzednio niewpisany dokument XML w <xref:System.Xml.XmlDocument> obiekcie zastępowanym przez wpisany dokument.  
  
 Obiekt zgłasza błędy walidacji schematu i ostrzeżenia <xref:System.Xml.Schema.ValidationEventHandler> przy użyciu delegata przekazaną <xref:System.Xml.XmlDocument.Validate%2A> jako parametr do metody. <xref:System.Xml.XmlDocument>  
  
 Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku zawartego <xref:System.Xml.XmlDocument> w obiekcie względem `contosoBooks.xsd` schematu zawartego we <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> właściwości obiektu.  
  
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
  
 Przykład pobiera `contosoBooks.xsd` również jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Weryfikowanie modyfikacji  
 Po wprowadzeniu modyfikacji do dokumentu XML można sprawdzić poprawność modyfikacji względem schematu dokumentu XML przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
 Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku w trakcie jego ładowania <xref:System.Xml.XmlDocument> do obiektu przez utworzenie <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu. Dokument XML zostanie zweryfikowany pomyślnie, ponieważ jest załadowany bez generowania błędów walidacji schematu lub ostrzeżeń. W przykładzie wprowadzono dwie modyfikacje dokumentu XML, które są nieprawidłowe zgodnie `contosoBooks.xsd` ze schematem. Pierwsza modyfikacja powoduje wstawienie nieprawidłowego elementu podrzędnego w wyniku błędu walidacji schematu, a druga zmiana ustawia wartość węzła określonego przez wartość, która jest nieprawidłowa w zależności od typu węzła, w wyniku wyjątku.  
  
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
  
 Przykład pobiera `contosoBooks.xsd` również jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 W powyższym przykładzie dwa modyfikacje są wprowadzane do dokumentu XML zawartego w <xref:System.Xml.XmlDocument> obiekcie. Po załadowaniu dokumentu XML wszelkie napotkane błędy walidacji schematu byłyby obsługiwane przez metodę obsługi zdarzeń walidacji i zapisywane w konsoli.  
  
 W tym przykładzie błędy walidacji zostały wprowadzone po załadowaniu dokumentu XML i zostały znalezione przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
 Modyfikacje wprowadzone przy <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> użyciu metody <xref:System.Xml.XPath.XPathNavigator> klasy spowodowały, <xref:System.InvalidCastException> że nowa wartość była nieprawidłowa przy uwzględnieniu typu schematu węzła.  
  
 Aby uzyskać więcej informacji na temat modyfikowania wartości <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> przy użyciu metody, zobacz temat [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .  
  
### <a name="read-only-validation"></a>Walidacja tylko do odczytu  
 <xref:System.Xml.XPath.XPathDocument> Klasa jest reprezentacją w pamięci dokumentu XML tylko do odczytu. Klasy i klasy tworzą<xref:System.Xml.XPath.XPathNavigator> obiekty do nawigowania i edytowania dokumentów XML. <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> Ponieważ Klasa jest klasą tylko do odczytu, <xref:System.Xml.XPath.XPathNavigator> obiekt zwrócony z <xref:System.Xml.XPath.XPathDocument> obiektów <xref:System.Xml.XPath.XPathDocument> nie może edytować dokumentu XML zawartego w obiekcie. <xref:System.Xml.XPath.XPathDocument>  
  
 W przypadku weryfikacji można utworzyć <xref:System.Xml.XPath.XPathDocument> obiekt tak samo jak w przypadku <xref:System.Xml.XmlDocument> tworzenia obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu, jak opisano wcześniej w tym temacie. Obiekt sprawdza poprawność dokumentu XML w trakcie jego ładowania, ale ponieważ nie można edytować danych XML <xref:System.Xml.XPath.XPathDocument> w obiekcie, nie można ponownie sprawdzić poprawności dokumentu XML. <xref:System.Xml.XPath.XPathDocument>  
  
 Aby uzyskać więcej informacji na temat obiektów tylko do <xref:System.Xml.XPath.XPathNavigator> odczytu i edytowalnych, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
