---
title: Weryfikacja schematu przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: f6e56616543bf7d2ad2e6be4d7bf7cbc50ba3a23
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292010"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="f0d15-102">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f0d15-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="f0d15-103">Korzystając z <xref:System.Xml.XmlDocument> klasy, można sprawdzić poprawność zawartości XML zawartej w <xref:System.Xml.XmlDocument> obiekcie na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="f0d15-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="f0d15-104">Pierwszym sposobem jest zweryfikowanie zawartości XML przy użyciu obiektu sprawdzającego poprawność, <xref:System.Xml.XmlReader> a drugi — użycie <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f0d15-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f0d15-105">Można również wykonać walidację zawartości XML tylko do odczytu przy użyciu <xref:System.Xml.XPath.XPathDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f0d15-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="f0d15-106">Walidacja danych XML</span><span class="sxs-lookup"><span data-stu-id="f0d15-106">Validating XML Data</span></span>  
 <span data-ttu-id="f0d15-107"><xref:System.Xml.XmlDocument>Klasa nie sprawdza poprawności dokumentu XML przy użyciu opcji walidacji schematu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="f0d15-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="f0d15-108">Sprawdza tylko, czy dokument XML jest poprawnie sformułowany.</span><span class="sxs-lookup"><span data-stu-id="f0d15-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="f0d15-109">Pierwszy sposób sprawdzania poprawności dokumentu XML polega na sprawdzeniu, czy dokument jest ładowany do <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0d15-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f0d15-110">Drugi sposób polega na sprawdzeniu, czy niewpisany wcześniej dokument XML przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f0d15-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f0d15-111">W obu przypadkach zmiany zweryfikowanego dokumentu XML mogą być ponownie weryfikowane przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f0d15-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="f0d15-112">Sprawdzanie poprawności dokumentu w trakcie jego ładowania</span><span class="sxs-lookup"><span data-stu-id="f0d15-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="f0d15-113">Obiekt walidacji <xref:System.Xml.XmlReader> jest tworzony przez przekazanie <xref:System.Xml.XmlReaderSettings> obiektu do <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy, która przyjmuje <xref:System.Xml.XmlReaderSettings> obiekt jako parametr.</span><span class="sxs-lookup"><span data-stu-id="f0d15-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="f0d15-114"><xref:System.Xml.XmlReaderSettings>Obiekt przeszedł jako parametr ma <xref:System.Xml.XmlReaderSettings.ValidationType%2A> ustawioną właściwość `Schema` i schemat XML dla dokumentu XML zawartego w <xref:System.Xml.XmlDocument> obiekcie dodanym do jego <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0d15-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="f0d15-115">Obiekt walidacji <xref:System.Xml.XmlReader> jest następnie używany do tworzenia <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0d15-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="f0d15-116">Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku w trakcie jego ładowania do <xref:System.Xml.XmlDocument> obiektu przez utworzenie <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0d15-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f0d15-117">Ponieważ dokument XML jest prawidłowy zgodnie ze schematem, nie są generowane żadne błędy walidacji schematu ani Ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="f0d15-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
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
  
 <span data-ttu-id="f0d15-118">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f0d15-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f0d15-119">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f0d15-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="f0d15-120">W powyższym przykładzie <xref:System.Xml.Schema.XmlSchemaValidationException> zostanie wygenerowany, gdy <xref:System.Xml.XmlDocument.Load%2A> jest wywoływana, jeśli dowolny atrybut lub typ elementu nie pasuje do odpowiedniego typu określonego w schemacie walidacji.</span><span class="sxs-lookup"><span data-stu-id="f0d15-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="f0d15-121">Jeśli <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest ustawiona dla walidacji <xref:System.Xml.XmlReader> , <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> zostanie wywołane przy każdym napotkaniu nieprawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="f0d15-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="f0d15-122"><xref:System.Xml.Schema.XmlSchemaException>Zostanie wygenerowany, gdy atrybut lub element z <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> ustawionym na `invalid` jest dostępny przez <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="f0d15-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="f0d15-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A>Właściwość może służyć do określenia, czy pojedynczy atrybut lub element jest prawidłowy podczas uzyskiwania dostępu do atrybutów lub elementów za pomocą <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="f0d15-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0d15-124">Gdy dokument XML jest ładowany do <xref:System.Xml.XmlDocument> obiektu ze skojarzonym schematem, który definiuje wartości domyślne, <xref:System.Xml.XmlDocument> obiekt traktuje te wartości domyślne tak, jakby pojawiły się w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="f0d15-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="f0d15-125">Oznacza to, że <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> Właściwość zawsze zwraca `false` dla elementu, który został domyślnie zwrócony ze schematu, nawet jeśli w dokumencie XML został zapisany jako pusty element.</span><span class="sxs-lookup"><span data-stu-id="f0d15-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="f0d15-126">Walidacja dokumentu przy użyciu metody weryfikacji</span><span class="sxs-lookup"><span data-stu-id="f0d15-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="f0d15-127"><xref:System.Xml.XmlDocument.Validate%2A>Metoda <xref:System.Xml.XmlDocument> klasy sprawdza poprawność dokumentu XML zawartego w <xref:System.Xml.XmlDocument> obiekcie względem schematów określonych we <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> właściwości obiektu i wykonuje rozszerzanie sprawdzonych.</span><span class="sxs-lookup"><span data-stu-id="f0d15-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="f0d15-128">Wynikiem jest poprzednio niewpisany dokument XML w <xref:System.Xml.XmlDocument> obiekcie zastępowanym przez wpisany dokument.</span><span class="sxs-lookup"><span data-stu-id="f0d15-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="f0d15-129"><xref:System.Xml.XmlDocument>Obiekt zgłasza błędy walidacji schematu i ostrzeżenia przy użyciu <xref:System.Xml.Schema.ValidationEventHandler> delegata przekazaną jako parametr do <xref:System.Xml.XmlDocument.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f0d15-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="f0d15-130">Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku zawartego w <xref:System.Xml.XmlDocument> obiekcie względem `contosoBooks.xsd` schematu zawartego we <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0d15-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="f0d15-131">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f0d15-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f0d15-132">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f0d15-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="f0d15-133">Weryfikowanie modyfikacji</span><span class="sxs-lookup"><span data-stu-id="f0d15-133">Validating Modifications</span></span>  
 <span data-ttu-id="f0d15-134">Po wprowadzeniu modyfikacji do dokumentu XML można sprawdzić poprawność modyfikacji względem schematu dokumentu XML przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f0d15-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="f0d15-135">Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku w trakcie jego ładowania do <xref:System.Xml.XmlDocument> obiektu przez utworzenie <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f0d15-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f0d15-136">Dokument XML zostanie zweryfikowany pomyślnie, ponieważ jest załadowany bez generowania błędów walidacji schematu lub ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="f0d15-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="f0d15-137">W przykładzie wprowadzono dwie modyfikacje dokumentu XML, które są nieprawidłowe zgodnie ze `contosoBooks.xsd` schematem.</span><span class="sxs-lookup"><span data-stu-id="f0d15-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="f0d15-138">Pierwsza modyfikacja powoduje wstawienie nieprawidłowego elementu podrzędnego w wyniku błędu walidacji schematu, a druga zmiana ustawia wartość węzła określonego przez wartość, która jest nieprawidłowa w zależności od typu węzła, w wyniku wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f0d15-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
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
  
 <span data-ttu-id="f0d15-139">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f0d15-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f0d15-140">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f0d15-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="f0d15-141">W powyższym przykładzie dwa modyfikacje są wprowadzane do dokumentu XML zawartego w <xref:System.Xml.XmlDocument> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="f0d15-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="f0d15-142">Po załadowaniu dokumentu XML wszelkie napotkane błędy walidacji schematu byłyby obsługiwane przez metodę obsługi zdarzeń walidacji i zapisywane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="f0d15-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="f0d15-143">W tym przykładzie błędy walidacji zostały wprowadzone po załadowaniu dokumentu XML i zostały znalezione przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f0d15-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="f0d15-144">Modyfikacje wprowadzone przy użyciu <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy spowodowały, że <xref:System.InvalidCastException> Nowa wartość była nieprawidłowa przy uwzględnieniu typu schematu węzła.</span><span class="sxs-lookup"><span data-stu-id="f0d15-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="f0d15-145">Aby uzyskać więcej informacji na temat modyfikowania wartości przy użyciu <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, zobacz temat [modyfikowanie danych XML przy użyciu klasy XPathNavigator](modify-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="f0d15-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="f0d15-146">Walidacja tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f0d15-146">Read-Only Validation</span></span>  
 <span data-ttu-id="f0d15-147"><xref:System.Xml.XPath.XPathDocument>Klasa jest reprezentacją w pamięci dokumentu XML tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="f0d15-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="f0d15-148"><xref:System.Xml.XPath.XPathDocument>Klasy i <xref:System.Xml.XmlDocument> klasy tworzą <xref:System.Xml.XPath.XPathNavigator> obiekty do nawigowania i edytowania dokumentów XML.</span><span class="sxs-lookup"><span data-stu-id="f0d15-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="f0d15-149">Ponieważ <xref:System.Xml.XPath.XPathDocument> Klasa jest klasą tylko do odczytu, <xref:System.Xml.XPath.XPathNavigator> obiekt zwrócony z <xref:System.Xml.XPath.XPathDocument> obiektów nie może edytować dokumentu XML zawartego w <xref:System.Xml.XPath.XPathDocument> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="f0d15-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="f0d15-150">W przypadku weryfikacji można utworzyć <xref:System.Xml.XPath.XPathDocument> obiekt tak samo jak w przypadku tworzenia <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu, jak opisano wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f0d15-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="f0d15-151"><xref:System.Xml.XPath.XPathDocument>Obiekt sprawdza poprawność dokumentu XML w trakcie jego ładowania, ale ponieważ nie można edytować danych XML w <xref:System.Xml.XPath.XPathDocument> obiekcie, nie można ponownie sprawdzić poprawności dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f0d15-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="f0d15-152">Aby uzyskać więcej informacji na temat obiektów tylko do odczytu i edytowalnych <xref:System.Xml.XPath.XPathNavigator> , zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md) .</span><span class="sxs-lookup"><span data-stu-id="f0d15-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d15-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0d15-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f0d15-154">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="f0d15-154">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f0d15-155">Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="f0d15-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="f0d15-156">Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f0d15-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f0d15-157">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f0d15-157">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f0d15-158">Edytowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f0d15-158">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
