---
title: XDocument, klasa — Przegląd (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: f9a531b9e90a8d6511dd0a2c6fc3131c9bfe1e89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907819"
---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="08b7d-102">XDocument, klasa — Przegląd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08b7d-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="08b7d-103">W tym temacie przedstawiono <xref:System.Xml.Linq.XDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="08b7d-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="08b7d-104">Omówienie XDocument, klasa</span><span class="sxs-lookup"><span data-stu-id="08b7d-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="08b7d-105"><xref:System.Xml.Linq.XDocument> Klasa zawiera informacje niezbędne do prawidłowy dokument XML.</span><span class="sxs-lookup"><span data-stu-id="08b7d-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="08b7d-106">Dotyczy to również deklaracji XML, takich jak przetwarzanie instrukcji i komentarze.</span><span class="sxs-lookup"><span data-stu-id="08b7d-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="08b7d-107">Należy zauważyć, że trzeba utworzyć <xref:System.Xml.Linq.XDocument> obiekty, jeśli potrzebujesz określonej funkcje udostępniane przez <xref:System.Xml.Linq.XDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="08b7d-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="08b7d-108">W wielu sytuacjach może współpracować bezpośrednio z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="08b7d-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="08b7d-109">Praca bezpośrednio z <xref:System.Xml.Linq.XElement> jest prostsze modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="08b7d-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="08b7d-110"><xref:System.Xml.Linq.XDocument> pochodzi od klasy <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="08b7d-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="08b7d-111">W związku z tym może zawierać węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="08b7d-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="08b7d-112">Jednak <xref:System.Xml.Linq.XDocument> obiekty mogą mieć tylko jeden element podrzędny <xref:System.Xml.Linq.XElement> węzła.</span><span class="sxs-lookup"><span data-stu-id="08b7d-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="08b7d-113">Odzwierciedla standardu XML, że może istnieć tylko jeden element główny dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="08b7d-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="08b7d-114">Składniki XDocument</span><span class="sxs-lookup"><span data-stu-id="08b7d-114">Components of XDocument</span></span>  
 <span data-ttu-id="08b7d-115"><xref:System.Xml.Linq.XDocument> Może zawierać następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="08b7d-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="08b7d-116">Jeden <xref:System.Xml.Linq.XDeclaration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="08b7d-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="08b7d-117"><xref:System.Xml.Linq.XDeclaration> można określić odpowiednie części deklaracji XML: Wersja XML, kodowania dokumentu, oraz czy dokument XML jest autonomicznym.</span><span class="sxs-lookup"><span data-stu-id="08b7d-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="08b7d-118">Jeden <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="08b7d-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="08b7d-119">Jest to węzeł główny dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="08b7d-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="08b7d-120">Dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> obiektów.</span><span class="sxs-lookup"><span data-stu-id="08b7d-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="08b7d-121">Instrukcja przetwarzania komunikuje się informacji do aplikacji, która przetwarza dane XML.</span><span class="sxs-lookup"><span data-stu-id="08b7d-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="08b7d-122">Dowolną liczbę <xref:System.Xml.Linq.XComment> obiektów.</span><span class="sxs-lookup"><span data-stu-id="08b7d-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="08b7d-123">Komentarze będą powiązane z elementem głównym.</span><span class="sxs-lookup"><span data-stu-id="08b7d-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="08b7d-124"><xref:System.Xml.Linq.XComment> Obiekt nie może być pierwszy argument na liście, ponieważ nie jest prawidłowy dla dokumentu XML, można uruchomić z komentarzem.</span><span class="sxs-lookup"><span data-stu-id="08b7d-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="08b7d-125">Jeden <xref:System.Xml.Linq.XDocumentType> DTD.</span><span class="sxs-lookup"><span data-stu-id="08b7d-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="08b7d-126">Podczas serializacji <xref:System.Xml.Linq.XDocument>, nawet jeśli `XDocument.Declaration` jest `null`, dane wyjściowe będą mieć deklaracji XML, jeśli moduł zapisujący `Writer.Settings.OmitXmlDeclaration` równa `false` (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="08b7d-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="08b7d-127">Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustawia wersji "1.0" i ustawia kodowanie "utf-8".</span><span class="sxs-lookup"><span data-stu-id="08b7d-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="08b7d-128">Za pomocą klasy XElement bez klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="08b7d-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="08b7d-129">Jak wcześniej wspomniano, <xref:System.Xml.Linq.XElement> klasa jest klasą głównego w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejs programowania.</span><span class="sxs-lookup"><span data-stu-id="08b7d-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="08b7d-130">W wielu przypadkach, Twoja aplikacja nie będzie wymagać tworzenia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="08b7d-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="08b7d-131">Za pomocą <xref:System.Xml.Linq.XElement> klasy, można utworzyć drzewa XML, dodać inne drzew XML do niego, modyfikowanie drzewa XML i zapisz go.</span><span class="sxs-lookup"><span data-stu-id="08b7d-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="08b7d-132">Za pomocą klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="08b7d-132">Using XDocument</span></span>  
 <span data-ttu-id="08b7d-133">Do konstruowania <xref:System.Xml.Linq.XDocument>, użyj konstrukcja funkcjonalna tak samo, jak możesz zrobić, aby skonstruować <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="08b7d-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="08b7d-134">Poniższy kod tworzy <xref:System.Xml.Linq.XDocument> obiekt i jego skojarzony zawarte obiekty.</span><span class="sxs-lookup"><span data-stu-id="08b7d-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
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
  
 <span data-ttu-id="08b7d-135">Podczas badania test.xml pliku możesz uzyskać następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="08b7d-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08b7d-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08b7d-136">See also</span></span>

- [<span data-ttu-id="08b7d-137">LINQ to XML — przegląd programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08b7d-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
