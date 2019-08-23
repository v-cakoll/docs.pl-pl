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
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="9cb53-102">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9cb53-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="9cb53-103">Korzystając z <xref:System.Xml.XmlDocument> klasy, można sprawdzić poprawność zawartości XML zawartej <xref:System.Xml.XmlDocument> w obiekcie na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="9cb53-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="9cb53-104">Pierwszym sposobem jest zweryfikowanie zawartości XML przy użyciu obiektu sprawdzającego <xref:System.Xml.XmlReader> poprawność, a drugi — <xref:System.Xml.XmlDocument.Validate%2A> użycie metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="9cb53-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="9cb53-105">Można również wykonać walidację zawartości XML tylko do odczytu przy użyciu <xref:System.Xml.XPath.XPathDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="9cb53-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="9cb53-106">Walidacja danych XML</span><span class="sxs-lookup"><span data-stu-id="9cb53-106">Validating XML Data</span></span>  
 <span data-ttu-id="9cb53-107"><xref:System.Xml.XmlDocument> Klasa nie sprawdza poprawności dokumentu XML przy użyciu opcji walidacji schematu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="9cb53-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="9cb53-108">Sprawdza tylko, czy dokument XML jest poprawnie sformułowany.</span><span class="sxs-lookup"><span data-stu-id="9cb53-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="9cb53-109">Pierwszy sposób sprawdzania poprawności dokumentu XML polega na sprawdzeniu, czy dokument jest ładowany do <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9cb53-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="9cb53-110">Drugi sposób polega na sprawdzeniu, czy niewpisany wcześniej dokument XML przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="9cb53-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="9cb53-111">W obu przypadkach zmiany zweryfikowanego dokumentu XML mogą być ponownie weryfikowane przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="9cb53-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="9cb53-112">Sprawdzanie poprawności dokumentu w trakcie jego ładowania</span><span class="sxs-lookup"><span data-stu-id="9cb53-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="9cb53-113">Obiekt <xref:System.Xml.XmlReader> walidacji jest tworzony przez <xref:System.Xml.XmlReader.Create%2A> <xref:System.Xml.XmlReaderSettings> przekazanie obiektu <xref:System.Xml.XmlReader> do metody klasy, która przyjmuje <xref:System.Xml.XmlReaderSettings> obiekt jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9cb53-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="9cb53-114">`Schema` <xref:System.Xml.XmlReaderSettings.ValidationType%2A> <xref:System.Xml.XmlReaderSettings.Schemas%2A> <xref:System.Xml.XmlDocument> Obiekt przeszedł jako parametr ma ustawioną właściwość i schemat XML dla dokumentu XML zawartego w obiekcie dodanym do jego właściwości. <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="9cb53-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="9cb53-115">Obiekt walidacji <xref:System.Xml.XmlReader> jest następnie używany do <xref:System.Xml.XmlDocument> tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="9cb53-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="9cb53-116">Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku w trakcie jego ładowania <xref:System.Xml.XmlDocument> do obiektu przez utworzenie <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9cb53-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="9cb53-117">Ponieważ dokument XML jest prawidłowy zgodnie ze schematem, nie są generowane żadne błędy walidacji schematu ani Ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="9cb53-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
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
  
 <span data-ttu-id="9cb53-118">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9cb53-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="9cb53-119">Przykład pobiera `contosoBooks.xsd` również jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9cb53-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="9cb53-120">W powyższym przykładzie <xref:System.Xml.Schema.XmlSchemaValidationException> zostanie wygenerowany, gdy <xref:System.Xml.XmlDocument.Load%2A> jest wywoływana, jeśli dowolny atrybut lub typ elementu nie pasuje do odpowiedniego typu określonego w schemacie walidacji.</span><span class="sxs-lookup"><span data-stu-id="9cb53-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="9cb53-121">Jeśli jest ustawiona dla walidacji <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> zostanie wywołane przy każdym napotkaniu nieprawidłowego typu. <xref:System.Xml.XmlReaderSettings.ValidationEventHandler></span><span class="sxs-lookup"><span data-stu-id="9cb53-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="9cb53-122">Zostanie wygenerowany, gdy atrybut lub element z <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> ustawionym <xref:System.Xml.XPath.XPathNavigator>na `invalid` jest dostępny przez. <xref:System.Xml.Schema.XmlSchemaException></span><span class="sxs-lookup"><span data-stu-id="9cb53-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="9cb53-123">Właściwość może służyć do określenia, czy pojedynczy atrybut lub element jest prawidłowy podczas uzyskiwania dostępu do atrybutów lub elementów <xref:System.Xml.XPath.XPathNavigator>za pomocą. <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A></span><span class="sxs-lookup"><span data-stu-id="9cb53-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9cb53-124">Gdy dokument XML jest ładowany do <xref:System.Xml.XmlDocument> obiektu ze skojarzonym schematem, który definiuje wartości domyślne <xref:System.Xml.XmlDocument> , obiekt traktuje te wartości domyślne tak, jakby pojawiły się w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="9cb53-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="9cb53-125">Oznacza to, że <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> Właściwość zawsze zwraca `false` dla elementu, który został domyślnie zwrócony ze schematu, nawet jeśli w dokumencie XML został zapisany jako pusty element.</span><span class="sxs-lookup"><span data-stu-id="9cb53-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="9cb53-126">Walidacja dokumentu przy użyciu metody weryfikacji</span><span class="sxs-lookup"><span data-stu-id="9cb53-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="9cb53-127"><xref:System.Xml.XmlDocument.Schemas%2A> <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument> Metoda klasy sprawdza poprawność dokumentu XML zawartego w obiekcie względem schematów określonych we właściwości obiektu i wykonuje rozszerzanie sprawdzonych. <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Validate%2A></span><span class="sxs-lookup"><span data-stu-id="9cb53-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="9cb53-128">Wynikiem jest poprzednio niewpisany dokument XML w <xref:System.Xml.XmlDocument> obiekcie zastępowanym przez wpisany dokument.</span><span class="sxs-lookup"><span data-stu-id="9cb53-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="9cb53-129">Obiekt zgłasza błędy walidacji schematu i ostrzeżenia <xref:System.Xml.Schema.ValidationEventHandler> przy użyciu delegata przekazaną <xref:System.Xml.XmlDocument.Validate%2A> jako parametr do metody. <xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="9cb53-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="9cb53-130">Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku zawartego <xref:System.Xml.XmlDocument> w obiekcie względem `contosoBooks.xsd` schematu zawartego we <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlDocument.Schemas%2A> właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="9cb53-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="9cb53-131">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9cb53-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="9cb53-132">Przykład pobiera `contosoBooks.xsd` również jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9cb53-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="9cb53-133">Weryfikowanie modyfikacji</span><span class="sxs-lookup"><span data-stu-id="9cb53-133">Validating Modifications</span></span>  
 <span data-ttu-id="9cb53-134">Po wprowadzeniu modyfikacji do dokumentu XML można sprawdzić poprawność modyfikacji względem schematu dokumentu XML przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="9cb53-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="9cb53-135">Poniższy przykład sprawdza poprawność `contosoBooks.xml` pliku w trakcie jego ładowania <xref:System.Xml.XmlDocument> do obiektu przez utworzenie <xref:System.Xml.XmlDocument> obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9cb53-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="9cb53-136">Dokument XML zostanie zweryfikowany pomyślnie, ponieważ jest załadowany bez generowania błędów walidacji schematu lub ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="9cb53-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="9cb53-137">W przykładzie wprowadzono dwie modyfikacje dokumentu XML, które są nieprawidłowe zgodnie `contosoBooks.xsd` ze schematem.</span><span class="sxs-lookup"><span data-stu-id="9cb53-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="9cb53-138">Pierwsza modyfikacja powoduje wstawienie nieprawidłowego elementu podrzędnego w wyniku błędu walidacji schematu, a druga zmiana ustawia wartość węzła określonego przez wartość, która jest nieprawidłowa w zależności od typu węzła, w wyniku wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9cb53-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
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
  
 <span data-ttu-id="9cb53-139">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9cb53-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="9cb53-140">Przykład pobiera `contosoBooks.xsd` również jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9cb53-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="9cb53-141">W powyższym przykładzie dwa modyfikacje są wprowadzane do dokumentu XML zawartego w <xref:System.Xml.XmlDocument> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="9cb53-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="9cb53-142">Po załadowaniu dokumentu XML wszelkie napotkane błędy walidacji schematu byłyby obsługiwane przez metodę obsługi zdarzeń walidacji i zapisywane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="9cb53-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="9cb53-143">W tym przykładzie błędy walidacji zostały wprowadzone po załadowaniu dokumentu XML i zostały znalezione przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="9cb53-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="9cb53-144">Modyfikacje wprowadzone przy <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> użyciu metody <xref:System.Xml.XPath.XPathNavigator> klasy spowodowały, <xref:System.InvalidCastException> że nowa wartość była nieprawidłowa przy uwzględnieniu typu schematu węzła.</span><span class="sxs-lookup"><span data-stu-id="9cb53-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="9cb53-145">Aby uzyskać więcej informacji na temat modyfikowania wartości <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> przy użyciu metody, zobacz temat [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="9cb53-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="9cb53-146">Walidacja tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9cb53-146">Read-Only Validation</span></span>  
 <span data-ttu-id="9cb53-147"><xref:System.Xml.XPath.XPathDocument> Klasa jest reprezentacją w pamięci dokumentu XML tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="9cb53-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="9cb53-148">Klasy i klasy tworzą<xref:System.Xml.XPath.XPathNavigator> obiekty do nawigowania i edytowania dokumentów XML. <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument></span><span class="sxs-lookup"><span data-stu-id="9cb53-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="9cb53-149">Ponieważ Klasa jest klasą tylko do odczytu, <xref:System.Xml.XPath.XPathNavigator> obiekt zwrócony z <xref:System.Xml.XPath.XPathDocument> obiektów <xref:System.Xml.XPath.XPathDocument> nie może edytować dokumentu XML zawartego w obiekcie. <xref:System.Xml.XPath.XPathDocument></span><span class="sxs-lookup"><span data-stu-id="9cb53-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="9cb53-150">W przypadku weryfikacji można utworzyć <xref:System.Xml.XPath.XPathDocument> obiekt tak samo jak w przypadku <xref:System.Xml.XmlDocument> tworzenia obiektu za pomocą walidacji <xref:System.Xml.XmlReader> obiektu, jak opisano wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="9cb53-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="9cb53-151">Obiekt sprawdza poprawność dokumentu XML w trakcie jego ładowania, ale ponieważ nie można edytować danych XML <xref:System.Xml.XPath.XPathDocument> w obiekcie, nie można ponownie sprawdzić poprawności dokumentu XML. <xref:System.Xml.XPath.XPathDocument></span><span class="sxs-lookup"><span data-stu-id="9cb53-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="9cb53-152">Aby uzyskać więcej informacji na temat obiektów tylko do <xref:System.Xml.XPath.XPathNavigator> odczytu i edytowalnych, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) .</span><span class="sxs-lookup"><span data-stu-id="9cb53-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb53-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cb53-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="9cb53-154">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="9cb53-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="9cb53-155">Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="9cb53-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="9cb53-156">Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9cb53-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="9cb53-157">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9cb53-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="9cb53-158">Edytowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9cb53-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
