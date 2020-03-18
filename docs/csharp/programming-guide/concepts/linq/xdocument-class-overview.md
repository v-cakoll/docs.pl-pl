---
title: Przegląd klasy XDocument (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590841"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="883c9-102">Przegląd klasy XDocument (C#)</span><span class="sxs-lookup"><span data-stu-id="883c9-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="883c9-103">W tym temacie <xref:System.Xml.Linq.XDocument> przedstawiono klasę.</span><span class="sxs-lookup"><span data-stu-id="883c9-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="883c9-104">Omówienie klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="883c9-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="883c9-105">Klasa <xref:System.Xml.Linq.XDocument> zawiera informacje niezbędne dla prawidłowego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="883c9-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="883c9-106">Obejmuje to deklarację XML, instrukcje przetwarzania i komentarze.</span><span class="sxs-lookup"><span data-stu-id="883c9-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="883c9-107">Należy zauważyć, że <xref:System.Xml.Linq.XDocument> należy utworzyć obiekty tylko wtedy, <xref:System.Xml.Linq.XDocument> gdy wymagane są określone funkcje dostarczone przez klasę.</span><span class="sxs-lookup"><span data-stu-id="883c9-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="883c9-108">W wielu okolicznościach można <xref:System.Xml.Linq.XElement>pracować bezpośrednio z .</span><span class="sxs-lookup"><span data-stu-id="883c9-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="883c9-109">Praca bezpośrednio <xref:System.Xml.Linq.XElement> z jest prostszy model programowania.</span><span class="sxs-lookup"><span data-stu-id="883c9-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="883c9-110"><xref:System.Xml.Linq.XDocument>pochodzi z <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="883c9-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="883c9-111">W związku z tym może zawierać węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="883c9-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="883c9-112">Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć <xref:System.Xml.Linq.XElement> tylko jeden węzeł podrzędny.</span><span class="sxs-lookup"><span data-stu-id="883c9-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="883c9-113">Odzwierciedla to standard XML, że w dokumencie XML może znajdować się tylko jeden element główny.</span><span class="sxs-lookup"><span data-stu-id="883c9-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="883c9-114">Składniki XDocument</span><span class="sxs-lookup"><span data-stu-id="883c9-114">Components of XDocument</span></span>  
 <span data-ttu-id="883c9-115"><xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="883c9-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="883c9-116">Jeden <xref:System.Xml.Linq.XDeclaration> obiekt.</span><span class="sxs-lookup"><span data-stu-id="883c9-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="883c9-117"><xref:System.Xml.Linq.XDeclaration>umożliwia określenie istotnych części deklaracji XML: wersji XML, kodowania dokumentu i tego, czy dokument XML jest autonomiczny.</span><span class="sxs-lookup"><span data-stu-id="883c9-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="883c9-118">Jeden <xref:System.Xml.Linq.XElement> obiekt.</span><span class="sxs-lookup"><span data-stu-id="883c9-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="883c9-119">Jest to węzeł główny dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="883c9-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="883c9-120">Dowolna <xref:System.Xml.Linq.XProcessingInstruction> liczba obiektów.</span><span class="sxs-lookup"><span data-stu-id="883c9-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="883c9-121">Instrukcja przetwarzania przekazuje informacje do aplikacji, która przetwarza XML.</span><span class="sxs-lookup"><span data-stu-id="883c9-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="883c9-122">Dowolna <xref:System.Xml.Linq.XComment> liczba obiektów.</span><span class="sxs-lookup"><span data-stu-id="883c9-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="883c9-123">Komentarze będą rodzeństwem elementu głównego.</span><span class="sxs-lookup"><span data-stu-id="883c9-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="883c9-124">Obiekt <xref:System.Xml.Linq.XComment> nie może być pierwszym argumentem na liście, ponieważ nie jest prawidłowy dla dokumentu XML, aby rozpocząć od komentarza.</span><span class="sxs-lookup"><span data-stu-id="883c9-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="883c9-125">Jeden <xref:System.Xml.Linq.XDocumentType> dla DTD.</span><span class="sxs-lookup"><span data-stu-id="883c9-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="883c9-126">Podczas serializacji <xref:System.Xml.Linq.XDocument>, nawet `XDocument.Declaration` jeśli `null`jest , dane wyjściowe będą miały `Writer.Settings.OmitXmlDeclaration` deklarację `false` XML, jeśli moduł zapisujący ustawiono (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="883c9-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="883c9-127">Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawia wersję na "1.0" i ustawia kodowanie na "utf-8".</span><span class="sxs-lookup"><span data-stu-id="883c9-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="883c9-128">Korzystanie z XElement bez XDocument</span><span class="sxs-lookup"><span data-stu-id="883c9-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="883c9-129">Jak wcześniej wspomniano, <xref:System.Xml.Linq.XElement> klasa jest główną [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] klasą w interfejsie programowania.</span><span class="sxs-lookup"><span data-stu-id="883c9-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="883c9-130">W wielu przypadkach aplikacja nie będzie wymagać utworzenia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="883c9-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="883c9-131">Za pomocą <xref:System.Xml.Linq.XElement> klasy, można utworzyć drzewo XML, dodać inne drzewa XML do niego, zmodyfikować drzewo XML i zapisać go.</span><span class="sxs-lookup"><span data-stu-id="883c9-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="883c9-132">Korzystanie z XDocument</span><span class="sxs-lookup"><span data-stu-id="883c9-132">Using XDocument</span></span>  
 <span data-ttu-id="883c9-133">Aby zbudować konstrukcję funkcjonalną, <xref:System.Xml.Linq.XDocument>tak <xref:System.Xml.Linq.XElement> jak do konstruowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="883c9-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="883c9-134">Poniższy kod tworzy <xref:System.Xml.Linq.XDocument> obiekt i jego skojarzone zawarte obiekty.</span><span class="sxs-lookup"><span data-stu-id="883c9-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="883c9-135">Podczas badania pliku test.xml, otrzymasz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="883c9-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="883c9-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="883c9-136">See also</span></span>

- [<span data-ttu-id="883c9-137">Omówienie programowania LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="883c9-137">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
