---
title: Klasa XDocument — OmówienieC#()
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590841"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="3224a-102">Klasa XDocument — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="3224a-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="3224a-103">Ten temat zawiera wprowadzenie <xref:System.Xml.Linq.XDocument> do klasy.</span><span class="sxs-lookup"><span data-stu-id="3224a-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="3224a-104">Przegląd klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="3224a-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="3224a-105"><xref:System.Xml.Linq.XDocument> Klasa zawiera informacje niezbędne do prawidłowego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3224a-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="3224a-106">Obejmuje to deklarację XML, instrukcje przetwarzania i komentarze.</span><span class="sxs-lookup"><span data-stu-id="3224a-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="3224a-107">Należy pamiętać, że tylko należy utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli wymagane są konkretne funkcje dostarczone <xref:System.Xml.Linq.XDocument> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="3224a-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="3224a-108">W wielu przypadkach można bezpośrednio korzystać z <xref:System.Xml.Linq.XElement>programu.</span><span class="sxs-lookup"><span data-stu-id="3224a-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="3224a-109">Praca bezpośrednio z <xref:System.Xml.Linq.XElement> programem to prostszy model programowania.</span><span class="sxs-lookup"><span data-stu-id="3224a-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="3224a-110"><xref:System.Xml.Linq.XDocument>pochodzi od <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="3224a-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="3224a-111">W związku z tym może zawierać węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3224a-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="3224a-112">Jednak obiekty mogą mieć tylko jeden węzeł podrzędny <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="3224a-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="3224a-113">Odzwierciedla to standard XML, że w dokumencie XML może istnieć tylko jeden element główny.</span><span class="sxs-lookup"><span data-stu-id="3224a-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="3224a-114">Składniki klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="3224a-114">Components of XDocument</span></span>  
 <span data-ttu-id="3224a-115"><xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="3224a-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="3224a-116">Jeden <xref:System.Xml.Linq.XDeclaration> obiekt.</span><span class="sxs-lookup"><span data-stu-id="3224a-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="3224a-117"><xref:System.Xml.Linq.XDeclaration>umożliwia określenie odpowiednich części deklaracji XML: wersji XML, kodowania dokumentu oraz tego, czy dokument XML jest autonomiczny.</span><span class="sxs-lookup"><span data-stu-id="3224a-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="3224a-118">Jeden <xref:System.Xml.Linq.XElement> obiekt.</span><span class="sxs-lookup"><span data-stu-id="3224a-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="3224a-119">Jest to główny węzeł dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="3224a-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="3224a-120">Dowolna liczba <xref:System.Xml.Linq.XProcessingInstruction> obiektów.</span><span class="sxs-lookup"><span data-stu-id="3224a-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="3224a-121">Instrukcja przetwarzania komunikuje informacje z aplikacją, która przetwarza kod XML.</span><span class="sxs-lookup"><span data-stu-id="3224a-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="3224a-122">Dowolna liczba <xref:System.Xml.Linq.XComment> obiektów.</span><span class="sxs-lookup"><span data-stu-id="3224a-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="3224a-123">Komentarze będą elementy równorzędne z elementem głównym.</span><span class="sxs-lookup"><span data-stu-id="3224a-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="3224a-124"><xref:System.Xml.Linq.XComment> Obiekt nie może być pierwszym argumentem na liście, ponieważ nie jest on prawidłowy dla dokumentu XML, aby można było zacząć od komentarza.</span><span class="sxs-lookup"><span data-stu-id="3224a-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="3224a-125">Jeden <xref:System.Xml.Linq.XDocumentType> dla DTD.</span><span class="sxs-lookup"><span data-stu-id="3224a-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="3224a-126">W przypadku serializacji elementu <xref:System.Xml.Linq.XDocument>, nawet jeśli `XDocument.Declaration` jest `null`, wynik będzie miał deklarację `false` XML, jeśli moduł zapisujący `Writer.Settings.OmitXmlDeclaration` ma ustawioną wartość (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="3224a-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="3224a-127">Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawia wersję na "1,0" i ustawia kodowanie na "UTF-8".</span><span class="sxs-lookup"><span data-stu-id="3224a-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="3224a-128">Korzystanie z XElement bez klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="3224a-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="3224a-129">Jak wspomniano wcześniej, <xref:System.Xml.Linq.XElement> Klasa jest klasą główną [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w interfejsie programowania.</span><span class="sxs-lookup"><span data-stu-id="3224a-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="3224a-130">W wielu przypadkach aplikacja nie będzie wymagać tworzenia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3224a-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="3224a-131">Korzystając z <xref:System.Xml.Linq.XElement> klasy, można utworzyć drzewo XML, dodać do niego inne drzewa XML, zmodyfikować drzewo XML i zapisać.</span><span class="sxs-lookup"><span data-stu-id="3224a-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="3224a-132">Przy użyciu metody XDocument</span><span class="sxs-lookup"><span data-stu-id="3224a-132">Using XDocument</span></span>  
 <span data-ttu-id="3224a-133">Aby utworzyć <xref:System.Xml.Linq.XDocument>obiekt, użyj konstrukcji funkcjonalnej, tak jak w przypadku konstruowania <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="3224a-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="3224a-134">Poniższy kod tworzy obiekt i <xref:System.Xml.Linq.XDocument> powiązane z nim obiekty zawarte.</span><span class="sxs-lookup"><span data-stu-id="3224a-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
```  
  
 <span data-ttu-id="3224a-135">Podczas badania pliku test. XML otrzymujesz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3224a-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="3224a-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3224a-136">See also</span></span>

- [<span data-ttu-id="3224a-137">Omówienie programowania LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3224a-137">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
