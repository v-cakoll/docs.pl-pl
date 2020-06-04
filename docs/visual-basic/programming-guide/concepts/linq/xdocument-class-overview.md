---
title: XDocument, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: 90c97349006407b2eca861be31080ec17901fa5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413235"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="419c8-102">MFC — Omówienie klasy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="419c8-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="419c8-103">Ten temat zawiera wprowadzenie do <xref:System.Xml.Linq.XDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="419c8-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="419c8-104">Przegląd klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="419c8-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="419c8-105"><xref:System.Xml.Linq.XDocument>Klasa zawiera informacje niezbędne do prawidłowego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="419c8-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="419c8-106">Obejmuje to deklarację XML, instrukcje przetwarzania i komentarze.</span><span class="sxs-lookup"><span data-stu-id="419c8-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="419c8-107">Należy pamiętać, że tylko należy utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli wymagane są konkretne funkcje dostarczone przez <xref:System.Xml.Linq.XDocument> klasę.</span><span class="sxs-lookup"><span data-stu-id="419c8-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="419c8-108">W wielu przypadkach można bezpośrednio korzystać z programu <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="419c8-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="419c8-109">Praca bezpośrednio z programem <xref:System.Xml.Linq.XElement> to prostszy model programowania.</span><span class="sxs-lookup"><span data-stu-id="419c8-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="419c8-110"><xref:System.Xml.Linq.XDocument>pochodzi od <xref:System.Xml.Linq.XContainer> .</span><span class="sxs-lookup"><span data-stu-id="419c8-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="419c8-111">W związku z tym może zawierać węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="419c8-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="419c8-112">Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć tylko jeden węzeł podrzędny <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="419c8-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="419c8-113">Odzwierciedla to standard XML, że w dokumencie XML może istnieć tylko jeden element główny.</span><span class="sxs-lookup"><span data-stu-id="419c8-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="419c8-114">Składniki klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="419c8-114">Components of XDocument</span></span>  
 <span data-ttu-id="419c8-115"><xref:System.Xml.Linq.XDocument>Może zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="419c8-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="419c8-116">Jeden <xref:System.Xml.Linq.XDeclaration> obiekt.</span><span class="sxs-lookup"><span data-stu-id="419c8-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="419c8-117"><xref:System.Xml.Linq.XDeclaration>umożliwia określenie odpowiednich części deklaracji XML: wersji XML, kodowania dokumentu oraz tego, czy dokument XML jest autonomiczny.</span><span class="sxs-lookup"><span data-stu-id="419c8-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="419c8-118">Jeden <xref:System.Xml.Linq.XElement> obiekt.</span><span class="sxs-lookup"><span data-stu-id="419c8-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="419c8-119">Jest to główny węzeł dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="419c8-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="419c8-120">Dowolna liczba <xref:System.Xml.Linq.XProcessingInstruction> obiektów.</span><span class="sxs-lookup"><span data-stu-id="419c8-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="419c8-121">Instrukcja przetwarzania komunikuje informacje z aplikacją, która przetwarza kod XML.</span><span class="sxs-lookup"><span data-stu-id="419c8-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="419c8-122">Dowolna liczba <xref:System.Xml.Linq.XComment> obiektów.</span><span class="sxs-lookup"><span data-stu-id="419c8-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="419c8-123">Komentarze będą elementy równorzędne z elementem głównym.</span><span class="sxs-lookup"><span data-stu-id="419c8-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="419c8-124"><xref:System.Xml.Linq.XComment>Obiekt nie może być pierwszym argumentem na liście, ponieważ nie jest on prawidłowy dla dokumentu XML, aby można było zacząć od komentarza.</span><span class="sxs-lookup"><span data-stu-id="419c8-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="419c8-125">Jeden <xref:System.Xml.Linq.XDocumentType> dla DTD.</span><span class="sxs-lookup"><span data-stu-id="419c8-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="419c8-126">W przypadku serializacji elementu <xref:System.Xml.Linq.XDocument> , nawet jeśli `XDocument.Declaration` jest `null` , wynik będzie miał deklarację XML, jeśli moduł zapisujący ma `Writer.Settings.OmitXmlDeclaration` ustawioną wartość `false` (wartość domyślna).</span><span class="sxs-lookup"><span data-stu-id="419c8-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="419c8-127">Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Ustawia wersję na "1,0" i ustawia kodowanie na "UTF-8".</span><span class="sxs-lookup"><span data-stu-id="419c8-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="419c8-128">Korzystanie z XElement bez klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="419c8-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="419c8-129">Jak wspomniano wcześniej, <xref:System.Xml.Linq.XElement> Klasa jest klasą główną w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsie programowania.</span><span class="sxs-lookup"><span data-stu-id="419c8-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="419c8-130">W wielu przypadkach aplikacja nie będzie wymagać tworzenia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="419c8-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="419c8-131">Korzystając z <xref:System.Xml.Linq.XElement> klasy, można utworzyć drzewo XML, dodać do niego inne drzewa XML, zmodyfikować drzewo XML i zapisać.</span><span class="sxs-lookup"><span data-stu-id="419c8-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="419c8-132">Przy użyciu metody XDocument</span><span class="sxs-lookup"><span data-stu-id="419c8-132">Using XDocument</span></span>  
 <span data-ttu-id="419c8-133">Aby utworzyć obiekt <xref:System.Xml.Linq.XDocument> , użyj konstrukcji funkcjonalnej, tak jak w przypadku konstruowania <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="419c8-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="419c8-134">Poniższy kod tworzy <xref:System.Xml.Linq.XDocument> obiekt i powiązane z nim obiekty zawarte.</span><span class="sxs-lookup"><span data-stu-id="419c8-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="419c8-135">Podczas badania pliku test. XML otrzymujesz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="419c8-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="419c8-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="419c8-136">See also</span></span>

- [<span data-ttu-id="419c8-137">Omówienie programowania LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="419c8-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
