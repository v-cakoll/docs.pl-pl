---
title: 'Instrukcje: Modyfikowanie literałów XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 7a01fdc9d0541b5d277c2f283e25e9a1cef3b862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636342"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="2d2d1-102">Instrukcje: Modyfikowanie literałów XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d2d1-102">How to: Modify XML Literals (Visual Basic)</span></span>
<span data-ttu-id="2d2d1-103">Zapewnia wygodne metody modyfikowanie literałów XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="2d2d1-104">Możesz dodawać lub usuwać elementy i atrybuty, a za pomocą nowego elementu XML może również zastąpić istniejący element.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="2d2d1-105">Ten temat zawiera kilka przykładów sposobu modyfikowania istniejących literał XML.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="2d2d1-106">Aby zmodyfikować wartość literał XML</span><span class="sxs-lookup"><span data-stu-id="2d2d1-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="2d2d1-107">Aby zmodyfikować wartość literał XML, Uzyskaj odwołanie do pliku XML literału i ustaw `Value` właściwości na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="2d2d1-108">Poniższy kod aktualizuje wartość wszystkich \<cena > elementów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     <span data-ttu-id="2d2d1-109">Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-109">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>47.20</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>48.25</Price>  
      </Book>  
    </Catalog>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2d2d1-110">`Value` Właściwość odwołuje się do pierwszego elementu XML w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-110">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="2d2d1-111">Jeśli istnieje więcej niż jeden element, który ma taką samą nazwę w kolekcji, ustawienie `Value` właściwość dotyczy tylko pierwszego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-111">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="2d2d1-112">Aby dodać atrybut na literał XML</span><span class="sxs-lookup"><span data-stu-id="2d2d1-112">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="2d2d1-113">Aby dodać atrybut literał XML, należy najpierw uzyskać odwołanie do literał XML.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-113">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="2d2d1-114">Następnie można dodać atrybutu przez dodanie nowych właściwości osi atrybutu XML.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-114">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="2d2d1-115">Można również dodać nowy <xref:System.Xml.Linq.XAttribute> obiekt do formatu XML literału przy użyciu <xref:System.Xml.Linq.XContainer.Add%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-115">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="2d2d1-116">Poniższy kod przedstawia obie opcje.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-116">The following example shows both options.</span></span>  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     <span data-ttu-id="2d2d1-117">Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-117">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
    ```  
  
     <span data-ttu-id="2d2d1-118">Aby uzyskać więcej informacji na temat właściwości osi atrybutu XML, zobacz [właściwości osi atrybutu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="2d2d1-118">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="2d2d1-119">Aby dodać element do literał XML</span><span class="sxs-lookup"><span data-stu-id="2d2d1-119">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="2d2d1-120">Aby dodać element do literał XML, należy najpierw uzyskać odwołanie do literał XML.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-120">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="2d2d1-121">Następnie można dodać nowego <xref:System.Xml.Linq.XElement> obiektu jako ostatniego elementu podrzędnego elementu za pomocą <xref:System.Xml.Linq.XContainer.Add%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-121">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="2d2d1-122">Można dodać nowego <xref:System.Xml.Linq.XElement> obiektu jako pierwszego elementu podrzędnego przy użyciu <xref:System.Xml.Linq.XContainer.AddFirst%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-122">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="2d2d1-123">Aby dodać nowy element w określonej lokalizacji względnej wobec innych elementów podrzędnych, należy najpierw uzyskać odwołanie do sąsiadujących elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-123">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="2d2d1-124">Następnie można dodać nowego <xref:System.Xml.Linq.XElement> obiektu przed sąsiadujących elementu podrzędnego przy użyciu <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-124">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="2d2d1-125">Możesz także dodać nowe <xref:System.Xml.Linq.XElement> obiektu po sąsiadujących elementu podrzędnego przy użyciu <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-125">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="2d2d1-126">Poniższy przykład pokazuje przykłady każdego z tych metod.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-126">The following example shows examples of each of these techniques.</span></span>  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     <span data-ttu-id="2d2d1-127">Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-127">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331">  
        <Publisher>Microsoft Press</Publisher>  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <PublishDate>2005-2-14</PublishDate>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
    ```  
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="2d2d1-128">Aby usunąć element lub atrybut z literał XML</span><span class="sxs-lookup"><span data-stu-id="2d2d1-128">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="2d2d1-129">Usuwanie elementu lub atrybutu literał XML, Uzyskaj odwołanie do elementu lub atrybutu i wywołania `Remove` metodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-129">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     <span data-ttu-id="2d2d1-130">Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book></Catalog>  
    ```  
  
     <span data-ttu-id="2d2d1-131">Aby usunąć wszystkie elementy lub atrybuty z literał XML, Uzyskaj odwołanie do literał XML, a następnie wywołać <xref:System.Xml.Linq.XElement.RemoveAll%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-131">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="2d2d1-132">Aby zmodyfikować literał XML</span><span class="sxs-lookup"><span data-stu-id="2d2d1-132">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="2d2d1-133">Aby zmienić nazwę elementu XML, należy najpierw uzyskać odwołanie do elementu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-133">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="2d2d1-134">Następnie możesz utworzyć nową <xref:System.Xml.Linq.XElement> obiekt, który ma nową nazwę, a następnie przekazać nowy <xref:System.Xml.Linq.XElement> obiekt <xref:System.Xml.Linq.XNode.ReplaceWith%2A> metoda istniejącej <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-134">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="2d2d1-135">Jeśli element, który jest zamieniany ma elementy podrzędne, które muszą zostać zachowane, ustaw wartość nowego <xref:System.Xml.Linq.XElement> obiekt <xref:System.Xml.Linq.XContainer.Nodes%2A> właściwości istniejącego elementu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-135">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="2d2d1-136">Spowoduje to ustawienie wartość nowego elementu do wewnętrzny kod XML z istniejącego elementu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-136">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="2d2d1-137">W przeciwnym razie można ustawić wartość nowy element do `Value` właściwości istniejącego elementu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-137">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="2d2d1-138">Poniższy przykładowy kod zastępuje wszystkie \<opis > elementy z \<abstrakcyjne > element.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-138">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="2d2d1-139">Zawartość \<opis > element są zachowywane w nowym \<abstrakcyjne > element przy użyciu <xref:System.Xml.Linq.XContainer.Nodes%2A> właściwość \<opis > <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-139">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     <span data-ttu-id="2d2d1-140">Poniżej przedstawiono przykładowe źródło XML i zmodyfikować XML w tym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2d2d1-140">The following shows sample source XML and modified XML from this code example.</span></span>  
  
    ```  
    Source XML:  
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
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Description>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <MSRP>44.95</MSRP>    <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>    <Abstract>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Abstract>  
      </Book>  
    </Catalog>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d2d1-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d2d1-141">See also</span></span>
- [<span data-ttu-id="2d2d1-142">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d2d1-142">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="2d2d1-143">XML</span><span class="sxs-lookup"><span data-stu-id="2d2d1-143">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="2d2d1-144">Instrukcje: Ładowanie kodu XML z pliku, ciągu lub Stream</span><span class="sxs-lookup"><span data-stu-id="2d2d1-144">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="2d2d1-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="2d2d1-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="2d2d1-146">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d2d1-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
