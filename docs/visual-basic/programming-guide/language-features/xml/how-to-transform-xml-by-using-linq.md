---
title: 'Porady: przekształcanie XML za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 94ad5180c7921a5ace09f9161de5f275475e46d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652964"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="cf965-102">Porady: przekształcanie XML za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf965-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="cf965-103">[Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md) ułatwiają Odczytaj dane XML z jednego źródła i przekształcenie go do nowego formatu XML.</span><span class="sxs-lookup"><span data-stu-id="cf965-103">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="cf965-104">Można korzystać z zapytania LINQ do pobierania zawartości do transformacji lub zmieniać zawartość istniejącego dokumentu do nowego formatu XML.</span><span class="sxs-lookup"><span data-stu-id="cf965-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>  
  
 <span data-ttu-id="cf965-105">Przykład, w tym temacie przekształca zawartości z dokumentu XML źródła w formacie HTML do wyświetlenia w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="cf965-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a><span data-ttu-id="cf965-106">Do transformacji dokumentów XML</span><span class="sxs-lookup"><span data-stu-id="cf965-106">To transform an XML document</span></span>  
  
1.  <span data-ttu-id="cf965-107">W programie Visual Studio Utwórz nowy projekt Visual Basic w **aplikacji konsoli** szablonu projektu.</span><span class="sxs-lookup"><span data-stu-id="cf965-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>  
  
2.  <span data-ttu-id="cf965-108">Kliknij dwukrotnie plik Module1.vb utworzone w projekcie, aby zmodyfikować kod Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cf965-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="cf965-109">Dodaj następujący kod do `Sub Main` z `Module1` modułu.</span><span class="sxs-lookup"><span data-stu-id="cf965-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="cf965-110">Ten kod tworzy dokument XML źródła jako <xref:System.Xml.Linq.XDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf965-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
    ```vb  
    Dim catalog =   
      <?xml version="1.0"?>  
        <Catalog>  
          <Book id="bk101">  
            <Author>Garghentini, Davide</Author>  
            <Title>XML Developer's Guide</Title>  
            <Price>44.95</Price>  
            <Description>  
              An in-depth look at creating applications  
              with <technology>XML</technology>. For   
              <audience>beginners</audience> or   
              <audience>advanced</audience> developers.  
            </Description>  
          </Book>  
          <Book id="bk331">  
            <Author>Spencer, Phil</Author>  
            <Title>Developing Applications with Visual Basic .NET</Title>  
            <Price>45.95</Price>  
            <Description>  
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     <span data-ttu-id="cf965-111">[Porady: ładowanie XML z pliku, ciągu lub strumienia](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span><span class="sxs-lookup"><span data-stu-id="cf965-111">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span></span>  
  
3.  <span data-ttu-id="cf965-112">Po kodzie można utworzyć dokumentu XML źródła, Dodaj następujący kod, aby pobrać wszystkie \<książki > elementy z obiektu i przekształcania dokumentu HTML.</span><span class="sxs-lookup"><span data-stu-id="cf965-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="cf965-113">Lista \<książki > elementów jest tworzona przy użyciu zapytania LINQ, która zwraca kolekcję <xref:System.Xml.Linq.XElement> obiektów zawierających przekształcone HTML.</span><span class="sxs-lookup"><span data-stu-id="cf965-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="cf965-114">Wyrażenia osadzone umożliwia umieszczanie wartości z dokumentu źródłowego do nowego formatu XML.</span><span class="sxs-lookup"><span data-stu-id="cf965-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>  
  
     <span data-ttu-id="cf965-115">Wynikowy dokument HTML jest zapisywane w pliku za pomocą <xref:System.Xml.Linq.XElement.Save%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cf965-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4.  <span data-ttu-id="cf965-116">Po `Sub Main` z `Module1`, dodać nową metodę (`Sub`) do przekształcania \<opis > węzła w określonym formacie HTML.</span><span class="sxs-lookup"><span data-stu-id="cf965-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="cf965-117">Ta metoda jest wywoływany przez kod w poprzednim kroku i pozwala zachować format \<opis > elementów.</span><span class="sxs-lookup"><span data-stu-id="cf965-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>  
  
     <span data-ttu-id="cf965-118">Ta metoda zastępuje elementy podrzędne elementu \<opis > elementu HTML.</span><span class="sxs-lookup"><span data-stu-id="cf965-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="cf965-119">`ReplaceWith` Metoda jest używana w celu zachowania położenie elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="cf965-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="cf965-120">Po przekształceniu zawartość \<opis > element znajduje się w akapitu HTML (\<p >) elementu.</span><span class="sxs-lookup"><span data-stu-id="cf965-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="cf965-121"><xref:System.Xml.Linq.XContainer.Nodes%2A> Właściwość służy do pobierania zawartości po przekształceniu \<opis > elementu.</span><span class="sxs-lookup"><span data-stu-id="cf965-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="cf965-122">Daje to pewność, że elementy podrzędne są uwzględniane w zawartości po przekształceniu.</span><span class="sxs-lookup"><span data-stu-id="cf965-122">This ensures that sub-elements are included in the transformed content.</span></span>  
  
     <span data-ttu-id="cf965-123">Dodaj następujący kod po `Sub Main` z `Module1`.</span><span class="sxs-lookup"><span data-stu-id="cf965-123">Add the following code after `Sub Main` of `Module1`.</span></span>  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5.  <span data-ttu-id="cf965-124">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="cf965-124">Save your changes.</span></span>  
  
6.  <span data-ttu-id="cf965-125">Naciśnij klawisz F5, aby uruchomić kod.</span><span class="sxs-lookup"><span data-stu-id="cf965-125">Press F5 to run the code.</span></span> <span data-ttu-id="cf965-126">Powstałe w ten sposób zapisać dokumentu będą wyglądać w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cf965-126">The resulting saved document will resemble the following:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cf965-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf965-127">See Also</span></span>  
 [<span data-ttu-id="cf965-128">Literały XML</span><span class="sxs-lookup"><span data-stu-id="cf965-128">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="cf965-129">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf965-129">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [<span data-ttu-id="cf965-130">XML</span><span class="sxs-lookup"><span data-stu-id="cf965-130">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="cf965-131">Instrukcje: ładowanie kodu XML z pliku, ciągu lub strumienia</span><span class="sxs-lookup"><span data-stu-id="cf965-131">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [<span data-ttu-id="cf965-132">LINQ</span><span class="sxs-lookup"><span data-stu-id="cf965-132">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="cf965-133">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf965-133">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
