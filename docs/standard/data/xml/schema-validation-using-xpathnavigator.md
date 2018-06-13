---
title: Weryfikacja schematu za pomocą parametrem XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98403176c3af8e110bd8d7677fae715fee84baec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578356"
---
# <a name="schema-validation-using-xpathnavigator"></a>Weryfikacja schematu za pomocą parametrem XPathNavigator
Przy użyciu <xref:System.Xml.XmlDocument> klasy, można sprawdzić poprawność zawartości XML zawartych w <xref:System.Xml.XmlDocument> obiektu na dwa sposoby. Pierwszym sposobem jest sprawdzanie zawartości XML przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiekt i drugim sposobem jest użycie <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. Można również wykonywać walidacji tylko do odczytu zawartości przy użyciu XML <xref:System.Xml.XPath.XPathDocument> klasy.  
  
## <a name="validating-xml-data"></a>Sprawdzanie poprawności danych XML  
 <xref:System.Xml.XmlDocument> Klasy nie można zweryfikować dokument XML przy użyciu DTD lub XML schematu definition language (XSD) sprawdzanie poprawności schematu domyślnie. Sprawdza tylko, że dokument XML jest prawidłowo sformatowany.  
  
 Pierwszym sposobem zweryfikować dokument XML jest do walidacji dokumentu, ponieważ jest on ładowany do <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu. Drugim sposobem jest zweryfikowanie wcześniej bez typu dokumentu XML, za pomocą <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. W obu przypadkach zmiany zweryfikowanych dokumentu XML można można ponownie sprawdzić poprawności przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Sprawdzanie poprawności dokumentu, ponieważ jest załadowana.  
 Sprawdzanie poprawności <xref:System.Xml.XmlReader> obiekt jest tworzony przez przekazanie <xref:System.Xml.XmlReaderSettings> do obiektu <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy, która przyjmuje <xref:System.Xml.XmlReaderSettings> obiektu jako parametr. <xref:System.Xml.XmlReaderSettings> Przekazano obiekt jako parametr ma <xref:System.Xml.XmlReaderSettings.ValidationType%2A> ustawioną właściwość `Schema` i schematu XML dla dokumentu XML zawartych w <xref:System.Xml.XmlDocument> obiekt dodany do jego <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości. Sprawdzanie poprawności <xref:System.Xml.XmlReader> obiekt jest następnie używany do tworzenia <xref:System.Xml.XmlDocument> obiektu.  
  
 Poniższy przykład weryfikuje `contosoBooks.xml` plików, jak został załadowany <xref:System.Xml.XmlDocument> obiektu przez utworzenie <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu. Ponieważ dokument XML jest nieprawidłowa według jego schematu, są generowane nie błędy sprawdzania poprawności schematu lub ostrzeżenia.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład również przyjmuje `contosoBooks.xsd` jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 W powyższym przykładzie <xref:System.Xml.Schema.XmlSchemaValidationException> będzie zostać zgłoszony, gdy <xref:System.Xml.XmlDocument.Load%2A> nosi nazwę dowolnego typu elementu lub atrybutu jest niezgodny z danego typu określonego w sprawdzania poprawności schematu. Jeśli <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest ustawiony na weryfikacji <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> będzie jest wywoływana przy każdym napotkano nieprawidłowy typ.  
  
 <xref:System.Xml.Schema.XmlSchemaException> Zgłaszane w sytuacji, gdy atrybut lub element z <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> ustawioną `invalid` uzyskuje się dostęp za <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Właściwości można użyć do ustalenia, czy poszczególne atrybut lub element jest nieprawidłowy podczas uzyskiwania dostępu do atrybutów ani elementów z <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
>  Gdy dokument XML jest ładowany do <xref:System.Xml.XmlDocument> obiektu o skojarzony schemat, który definiuje wartości domyślne <xref:System.Xml.XmlDocument> obiektu traktuje te wartości domyślne, jak gdyby znajdowały się one w dokumencie XML. Oznacza to, że <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> właściwość zawsze zwraca `false` elementu była ustawiana domyślnie na podstawie schematu, nawet wtedy, gdy w dokumencie XML został zapisany jako pustego elementu.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Sprawdzanie poprawności dokumentu przy użyciu metody sprawdzania poprawności  
 <xref:System.Xml.XmlDocument.Validate%2A> Metody <xref:System.Xml.XmlDocument> klasy weryfikuje zawarte w dokumencie XML <xref:System.Xml.XmlDocument> obiektu względem schematów określone w <xref:System.Xml.XmlDocument> obiektu <xref:System.Xml.XmlDocument.Schemas%2A> właściwości i wykonuje rozszerzeniu typu infoset. Wynik jest wcześniej bez typu dokumentu XML w <xref:System.Xml.XmlDocument> obiektu zastąpione typu dokumentu.  
  
 <xref:System.Xml.XmlDocument> Obiekt zgłasza błędy sprawdzania poprawności schematu i ostrzeżenia przy użyciu <xref:System.Xml.Schema.ValidationEventHandler> delegata przekazany jako parametr <xref:System.Xml.XmlDocument.Validate%2A> metody.  
  
 Poniższy przykład weryfikuje `contosoBooks.xml` zawarte w pliku <xref:System.Xml.XmlDocument> obiekt przed `contosoBooks.xsd` zawartych w schemacie <xref:System.Xml.XmlDocument> obiektu <xref:System.Xml.XmlDocument.Schemas%2A> właściwości.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład również przyjmuje `contosoBooks.xsd` jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Sprawdzanie poprawności zmiany  
 Po dokonaniu zmiany w dokumencie XML można sprawdzić poprawność zmiany względem schematu dla dokumentów XML za pomocą <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
 Poniższy przykład weryfikuje `contosoBooks.xml` plików, jak został załadowany <xref:System.Xml.XmlDocument> obiektu przez utworzenie <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu. Dokumentu XML została sprawdzona pomyślnie, ponieważ jest on załadowany bez generowania występują błędy sprawdzania poprawności schematu lub ostrzeżenia. Następnie uaktywniane dwóch modyfikacje do dokumentu XML, które nie są prawidłowe, zgodnie z `contosoBooks.xsd` schematu. Pierwszy modyfikacji wstawia nieprawidłowym elementem podrzędnym powodujące błąd sprawdzania poprawności schematu i drugi modyfikacji ustawia wartość węzła typu wartość, która jest nieprawidłowa przy uwzględnieniu typu węzła, co powoduje wyjątek.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład również przyjmuje `contosoBooks.xsd` jako danych wejściowych.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 W powyższym przykładzie dwóch modyfikacje są dokonywane w dokumencie XML zawartych w <xref:System.Xml.XmlDocument> obiektu. Jako dokument XML został załadowany, napotkano błędy sprawdzania poprawności schematu zostały obsłużone przez metodę sprawdzania poprawności programu obsługi zdarzeń i wyświetlony w konsoli.  
  
 W tym przykładzie błędy sprawdzania poprawności zostały wprowadzone po dokumentu XML została załadowana, a znaleziono przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
 Zmiany dokonane za pomocą <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> spowodowała klasy <xref:System.InvalidCastException> ponieważ nowa wartość jest nieprawidłowa przy uwzględnieniu typu schematu węzła.  
  
 Aby uzyskać więcej informacji na temat modyfikowania wartości przy użyciu <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, zobacz [zmodyfikować danych XML przy użyciu Element XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.  
  
### <a name="read-only-validation"></a>Sprawdzanie poprawności tylko do odczytu  
 <xref:System.Xml.XPath.XPathDocument> Klasy jest tylko do odczytu, w pamięci reprezentację dokumentu XML. Zarówno <xref:System.Xml.XPath.XPathDocument> klasy i <xref:System.Xml.XmlDocument> Tworzenie klasy <xref:System.Xml.XPath.XPathNavigator> obiekty do nawigowania i edycji dokumentów XML. Ponieważ <xref:System.Xml.XPath.XPathDocument> klasa jest klasą tylko do odczytu <xref:System.Xml.XPath.XPathNavigator> obiektu zwróciła obiekt <xref:System.Xml.XPath.XPathDocument> obiektów nie można edytować dokumentu XML zawartych w <xref:System.Xml.XPath.XPathDocument> obiektu.  
  
 W przypadku weryfikacji, można utworzyć <xref:System.Xml.XPath.XPathDocument> obiekt tak samo, jak możesz utworzyć <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiekt zgodnie z opisem we wcześniejszej części tego tematu. <xref:System.Xml.XPath.XPathDocument> Obiektu weryfikuje dokumentu XML został załadowany, ale ponieważ nie można edytować danych XML w <xref:System.Xml.XPath.XPathDocument> obiektu, nie można ponownie zatwierdzać dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat tylko do odczytu i edycji <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
