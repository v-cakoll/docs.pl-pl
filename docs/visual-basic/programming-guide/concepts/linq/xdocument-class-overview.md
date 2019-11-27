---
title: XDocument, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: cbc1ccca53978da07f31c0ba7e54eca9f06b0e72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349287"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="cde02-102">MFC — Omówienie klasy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cde02-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="cde02-103">Ten temat zawiera wprowadzenie do klasy <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="cde02-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="cde02-104">Przegląd klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="cde02-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="cde02-105">Klasa <xref:System.Xml.Linq.XDocument> zawiera informacje niezbędne do prawidłowego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cde02-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="cde02-106">Obejmuje to deklarację XML, instrukcje przetwarzania i komentarze.</span><span class="sxs-lookup"><span data-stu-id="cde02-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="cde02-107">Należy pamiętać, że należy tylko utworzyć obiekty <xref:System.Xml.Linq.XDocument>, jeśli potrzebujesz określonych funkcji dostarczonych przez klasę <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="cde02-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="cde02-108">W wielu przypadkach można bezpośrednio korzystać z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="cde02-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="cde02-109">Praca bezpośrednio z <xref:System.Xml.Linq.XElement> jest prostszym modelem programowania.</span><span class="sxs-lookup"><span data-stu-id="cde02-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="cde02-110"><xref:System.Xml.Linq.XDocument> pochodzi od <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="cde02-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="cde02-111">W związku z tym może zawierać węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="cde02-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="cde02-112">Jednak obiekty <xref:System.Xml.Linq.XDocument> mogą mieć tylko jeden węzeł podrzędny <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="cde02-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="cde02-113">Odzwierciedla to standard XML, że w dokumencie XML może istnieć tylko jeden element główny.</span><span class="sxs-lookup"><span data-stu-id="cde02-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="cde02-114">Składniki klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="cde02-114">Components of XDocument</span></span>  
 <span data-ttu-id="cde02-115"><xref:System.Xml.Linq.XDocument> może zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="cde02-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="cde02-116">Jeden <xref:System.Xml.Linq.XDeclaration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cde02-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="cde02-117"><xref:System.Xml.Linq.XDeclaration> umożliwia określenie odpowiednich części deklaracji XML: wersji XML, kodowania dokumentu oraz tego, czy dokument XML jest autonomiczny.</span><span class="sxs-lookup"><span data-stu-id="cde02-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="cde02-118">Jeden <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cde02-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="cde02-119">Jest to główny węzeł dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cde02-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="cde02-120">Dowolna liczba obiektów <xref:System.Xml.Linq.XProcessingInstruction>.</span><span class="sxs-lookup"><span data-stu-id="cde02-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="cde02-121">Instrukcja przetwarzania komunikuje informacje z aplikacją, która przetwarza kod XML.</span><span class="sxs-lookup"><span data-stu-id="cde02-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="cde02-122">Dowolna liczba obiektów <xref:System.Xml.Linq.XComment>.</span><span class="sxs-lookup"><span data-stu-id="cde02-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="cde02-123">Komentarze będą elementy równorzędne z elementem głównym.</span><span class="sxs-lookup"><span data-stu-id="cde02-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="cde02-124">Obiekt <xref:System.Xml.Linq.XComment> nie może być pierwszym argumentem na liście, ponieważ nie jest on prawidłowy dla dokumentu XML, aby można było zacząć od komentarza.</span><span class="sxs-lookup"><span data-stu-id="cde02-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="cde02-125">Jeden <xref:System.Xml.Linq.XDocumentType> DTD.</span><span class="sxs-lookup"><span data-stu-id="cde02-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="cde02-126">Podczas serializacji <xref:System.Xml.Linq.XDocument>, nawet jeśli `XDocument.Declaration` jest `null`, dane wyjściowe będą zawierały deklarację XML, jeśli składnik zapisywania ma `Writer.Settings.OmitXmlDeclaration` ustawione na `false` (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="cde02-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="cde02-127">Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawia wersję na "1,0" i ustawia kodowanie na "UTF-8".</span><span class="sxs-lookup"><span data-stu-id="cde02-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="cde02-128">Korzystanie z XElement bez klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="cde02-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="cde02-129">Jak wspomniano wcześniej, Klasa <xref:System.Xml.Linq.XElement> jest klasą główną w interfejsie programowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cde02-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="cde02-130">W wielu przypadkach aplikacja nie będzie wymagać tworzenia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cde02-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="cde02-131">Korzystając z klasy <xref:System.Xml.Linq.XElement>, można utworzyć drzewo XML, dodać do niego inne drzewa XML, zmodyfikować drzewo XML i zapisać.</span><span class="sxs-lookup"><span data-stu-id="cde02-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="cde02-132">Przy użyciu metody XDocument</span><span class="sxs-lookup"><span data-stu-id="cde02-132">Using XDocument</span></span>  
 <span data-ttu-id="cde02-133">Aby skonstruować <xref:System.Xml.Linq.XDocument>, użyj konstrukcji funkcjonalnej, tak jak w przypadku konstruowania obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="cde02-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="cde02-134">Poniższy kod tworzy obiekt <xref:System.Xml.Linq.XDocument> i jego skojarzone zawarte obiekty.</span><span class="sxs-lookup"><span data-stu-id="cde02-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
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
doc.Save("test.xml")  
```  
  
 <span data-ttu-id="cde02-135">Podczas badania pliku test. XML otrzymujesz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="cde02-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cde02-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cde02-136">See also</span></span>

- [<span data-ttu-id="cde02-137">Omówienie programowania LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cde02-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
