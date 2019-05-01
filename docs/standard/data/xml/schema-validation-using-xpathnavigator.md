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
ms.openlocfilehash: 335e6578767c130760f322aa2b015ea7b0f317f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026994"
---
# <a name="schema-validation-using-xpathnavigator"></a>Weryfikacja schematu przy użyciu klasy XPathNavigator
Za pomocą <xref:System.Xml.XmlDocument> klasy, można sprawdzić poprawność zawartości XML zawartych w <xref:System.Xml.XmlDocument> obiektu na dwa sposoby. Pierwszym sposobem jest do weryfikowania zawartości XML przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu i drugim sposobem jest użycie <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. Można również wykonać walidacji tylko do odczytu zawartości przy użyciu XML <xref:System.Xml.XPath.XPathDocument> klasy.  
  
## <a name="validating-xml-data"></a>Sprawdzanie poprawności danych XML  
 <xref:System.Xml.XmlDocument> Klasy nie można zweryfikować za pomocą definicji DTD lub XML schematu definicji języka (XSD) sprawdzanie poprawności schematu domyślnie dokumentu XML. Sprawdza tylko, że jest poprawnie sformułowany dokument XML.  
  
 Pierwszym sposobem Sprawdź poprawność dokumentu XML jest do walidacji dokumentu, ponieważ jest ładowany do <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu. Drugi sposób polega na weryfikowanie wcześniej bez typu dokumentu XML, przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy. W obu przypadkach zmiany zweryfikowanych dokumentu XML może być sprawdzony ponownie przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
### <a name="validating-a-document-as-it-is-loaded"></a>Sprawdzanie poprawności dokumentu w postaci, w jakiej jest ładowany.  
 Sprawdzanie poprawności <xref:System.Xml.XmlReader> obiekt jest tworzony przez przekazanie <xref:System.Xml.XmlReaderSettings> obiekt <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy, która przyjmuje <xref:System.Xml.XmlReaderSettings> obiektu jako parametr. <xref:System.Xml.XmlReaderSettings> Przekazano obiekt jako parametr ma <xref:System.Xml.XmlReaderSettings.ValidationType%2A> właściwością `Schema` a schematu XML w dokumencie XML zawartych w <xref:System.Xml.XmlDocument> obiekt dodany do jego <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości. Sprawdzanie poprawności <xref:System.Xml.XmlReader> obiekt jest następnie używany do tworzenia <xref:System.Xml.XmlDocument> obiektu.  
  
 Poniższy przykład sprawdza `contosoBooks.xml` plików jest ładowany do <xref:System.Xml.XmlDocument> obiektu, tworząc <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu. Ponieważ dokument XML jest nieprawidłowa zgodnie z jego schematu, są generowane, nie ostrzeżeń ani błędów sprawdzania poprawności schematu.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 W powyższym przykładzie <xref:System.Xml.Schema.XmlSchemaValidationException> zostanie zgłoszony, gdy <xref:System.Xml.XmlDocument.Load%2A> jest wywoływana, jeśli dowolny typ atrybutu lub elementu nie jest zgodny z odpowiedniego typu, określona w schemacie sprawdzania poprawności. Jeśli <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest ustawiona na sprawdzanie poprawności <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> będzie wywoływana zawsze wtedy, gdy zostanie osiągnięty nieprawidłowego typu.  
  
 <xref:System.Xml.Schema.XmlSchemaException> Zgłaszany w sytuacji, gdy atrybut lub element z <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> równa `invalid` odbywa się przez <xref:System.Xml.XPath.XPathNavigator>.  
  
 <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Właściwość może służyć do określenia czy poszczególne atrybut lub element obowiązuje podczas uzyskiwania dostępu do atrybutów lub elementów z <xref:System.Xml.XPath.XPathNavigator>.  
  
> [!NOTE]
>  Podczas ładowania dokumentu XML do <xref:System.Xml.XmlDocument> obiektu za pomocą skojarzonego schematu, który definiuje wartości domyślne <xref:System.Xml.XmlDocument> obiektu traktuje te ustawienia domyślne tak, jakby były one wyświetlane w dokumencie XML. Oznacza to, że <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> właściwość zawsze zwraca `false` element, który został przyjmujące wartości domyślne ze schematu, nawet jeśli w dokumencie XML został zapisany jako pusty element.  
  
### <a name="validating-a-document-using-the-validate-method"></a>Sprawdzanie poprawności dokumentu przy użyciu metody sprawdzania poprawności  
 <xref:System.Xml.XmlDocument.Validate%2A> Metody <xref:System.Xml.XmlDocument> klasy weryfikuje zawarte w dokumencie XML <xref:System.Xml.XmlDocument> obiektu względem schematów określone w <xref:System.Xml.XmlDocument> obiektu <xref:System.Xml.XmlDocument.Schemas%2A> właściwości i wykonuje rozszerzeniu zestaw informacji. Wynik jest wcześniej bez typu dokumentu XML w <xref:System.Xml.XmlDocument> obiektu zastąpione wpisane dokumentu.  
  
 <xref:System.Xml.XmlDocument> Obiektu raporty schematu błędy i ostrzeżenia walidacji za pomocą <xref:System.Xml.Schema.ValidationEventHandler> delegowany przekazany jako parametr do <xref:System.Xml.XmlDocument.Validate%2A> metody.  
  
 Poniższy przykład sprawdza `contosoBooks.xml` zawarte w pliku <xref:System.Xml.XmlDocument> obiektu względem `contosoBooks.xsd` zawartych w schemacie <xref:System.Xml.XmlDocument> obiektu <xref:System.Xml.XmlDocument.Schemas%2A> właściwości.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a>Sprawdzanie poprawności zmian  
 Po dokonaniu modyfikacji dokumentu XML, można sprawdzić poprawność modyfikacji względem schematu dla dokumentów XML za pomocą <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
 Poniższy przykład sprawdza `contosoBooks.xml` plików jest ładowany do <xref:System.Xml.XmlDocument> obiektu, tworząc <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu. Dokument XML jest pomyślnie zweryfikowane, ponieważ został załadowany bez generowania żadnych ostrzeżeń ani błędów sprawdzania poprawności schematu. Przykład następnie udostępnia dwie zmiany w dokumencie XML, które są nieprawidłowe, zgodnie z opisem w `contosoBooks.xsd` schematu. Pierwszy modyfikacji wstawia nieprawidłowy element podrzędny spowodowało błąd walidacji schematu, a drugi modyfikacji ustawia wartość węzła typu wartości, która jest nieprawidłowa przy uwzględnieniu typu węzła spowodowało wyjątek.  
  
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
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 W powyższym przykładzie dwie zmiany zostaną wprowadzone do dokumentu XML zawartych w <xref:System.Xml.XmlDocument> obiektu. Zgodnie z dokumentu XML została załadowana, wszelkie błędy sprawdzania poprawności schematu, napotkano będzie zostały obsłużone przez metodę programu obsługi zdarzeń sprawdzania poprawności i wyświetlony w konsoli.  
  
 W tym przykładzie błędy sprawdzania poprawności zostały wprowadzone po dokumentu XML została załadowana, a znaleziono za pomocą <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.  
  
 Zmiany dokonane za pomocą <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy spowodowało <xref:System.InvalidCastException> ponieważ nowa wartość jest nieprawidłowa przy uwzględnieniu typu schematu węzła.  
  
 Aby uzyskać więcej informacji o modyfikowaniu wartości za pomocą <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, zobacz [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.  
  
### <a name="read-only-validation"></a>Sprawdzanie poprawności tylko do odczytu  
 <xref:System.Xml.XPath.XPathDocument> Klasy jest tylko do odczytu, w pamięci reprezentacją dokumentu XML. Zarówno <xref:System.Xml.XPath.XPathDocument> klasy i <xref:System.Xml.XmlDocument> tworzenia klasy <xref:System.Xml.XPath.XPathNavigator> obiekty do nawigowania i edycji dokumentów XML. Ponieważ <xref:System.Xml.XPath.XPathDocument> klasa jest klasą tylko do odczytu <xref:System.Xml.XPath.XPathNavigator> użytkownika zwróciła obiekt <xref:System.Xml.XPath.XPathDocument> obiektów nie można edytować dokumentu XML zawartych w <xref:System.Xml.XPath.XPathDocument> obiektu.  
  
 W przypadku sprawdzania poprawności, można utworzyć <xref:System.Xml.XPath.XPathDocument> obiektu tak samo, jak tworzysz <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu zgodnie z opisem we wcześniejszej części tego tematu. <xref:System.Xml.XPath.XPathDocument> Obiektu sprawdza poprawność dokumentu XML jest ładowany, ale ponieważ nie można edytować danych XML w <xref:System.Xml.XPath.XPathDocument> obiektu, nie można ponownie sprawdź poprawność dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat tylko do odczytu i edycji <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) tematu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [Edytowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
