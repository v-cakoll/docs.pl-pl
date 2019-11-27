---
title: 'Porady: modyfikowanie literałów XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 99ec35addcb9fc8d886c9151cde87227b5113eb9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330861"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="89885-102">Porady: modyfikowanie literałów XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89885-102">How to: Modify XML Literals (Visual Basic)</span></span>

<span data-ttu-id="89885-103">Visual Basic zapewnia wygodny sposób modyfikacji literałów XML.</span><span class="sxs-lookup"><span data-stu-id="89885-103">Visual Basic provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="89885-104">Można dodawać lub usuwać elementy i atrybuty, a także zastąpić istniejący element nowym elementem XML.</span><span class="sxs-lookup"><span data-stu-id="89885-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="89885-105">Ten temat zawiera kilka przykładów modyfikacji istniejącego literału XML.</span><span class="sxs-lookup"><span data-stu-id="89885-105">This topic provides several examples of how to modify an existing XML literal.</span></span>

### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="89885-106">Aby zmodyfikować wartość literału XML</span><span class="sxs-lookup"><span data-stu-id="89885-106">To modify the value of an XML literal</span></span>

1. <span data-ttu-id="89885-107">Aby zmodyfikować wartość literału XML, Uzyskaj odwołanie do literału XML i ustaw właściwość `Value` na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="89885-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>

    <span data-ttu-id="89885-108">Poniższy przykład kodu aktualizuje wartość wszystkich \<cena > elementów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="89885-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>

    [!code-vb[VbXmlSamples2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#4)]

    <span data-ttu-id="89885-109">Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="89885-109">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="89885-110">Źródłowy kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-110">Source XML:</span></span>

    ```xml
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
    ```

    <span data-ttu-id="89885-111">Zmodyfikowano kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-111">Modified XML:</span></span>

    ```xml
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
    > <span data-ttu-id="89885-112">Właściwość `Value` odwołuje się do pierwszego elementu XML w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="89885-112">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="89885-113">Jeśli istnieje więcej niż jeden element, który ma taką samą nazwę w kolekcji, ustawienie właściwości `Value` dotyczy tylko pierwszego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="89885-113">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>

### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="89885-114">Aby dodać atrybut do literału XML</span><span class="sxs-lookup"><span data-stu-id="89885-114">To add an attribute to an XML literal</span></span>

1. <span data-ttu-id="89885-115">Aby dodać atrybut do literału XML, najpierw Uzyskaj odwołanie do literału XML.</span><span class="sxs-lookup"><span data-stu-id="89885-115">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="89885-116">Następnie można dodać atrybut, dodając nową właściwość osi atrybutu XML.</span><span class="sxs-lookup"><span data-stu-id="89885-116">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="89885-117">Można również dodać nowy obiekt <xref:System.Xml.Linq.XAttribute> do literału XML przy użyciu metody <xref:System.Xml.Linq.XContainer.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="89885-117">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="89885-118">W poniższym przykładzie przedstawiono obie opcje.</span><span class="sxs-lookup"><span data-stu-id="89885-118">The following example shows both options.</span></span>

    [!code-vb[VbXmlSamples2#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#5)]

    <span data-ttu-id="89885-119">Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="89885-119">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="89885-120">Źródłowy kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-120">Source XML:</span></span>

    ```xml
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
    ```

    <span data-ttu-id="89885-121">Zmodyfikowano kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-121">Modified XML:</span></span>

    ```xml
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

    <span data-ttu-id="89885-122">Aby uzyskać więcej informacji na temat właściwości osi atrybutu XML, zobacz [Właściwość osi atrybutu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="89885-122">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>

### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="89885-123">Aby dodać element do literału XML</span><span class="sxs-lookup"><span data-stu-id="89885-123">To add an element to an XML literal</span></span>

1. <span data-ttu-id="89885-124">Aby dodać element do literału XML, najpierw Uzyskaj odwołanie do literału XML.</span><span class="sxs-lookup"><span data-stu-id="89885-124">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="89885-125">Następnie można dodać nowy obiekt <xref:System.Xml.Linq.XElement> jako ostatni element podrzędny elementu przy użyciu metody <xref:System.Xml.Linq.XContainer.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="89885-125">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="89885-126">Nowy obiekt <xref:System.Xml.Linq.XElement> można dodać jako pierwszy podelement przy użyciu metody <xref:System.Xml.Linq.XContainer.AddFirst%2A>.</span><span class="sxs-lookup"><span data-stu-id="89885-126">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>

    <span data-ttu-id="89885-127">Aby dodać nowy element w określonej lokalizacji względem innych elementów podrzędnych, najpierw Uzyskaj odwołanie do sąsiadującego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="89885-127">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="89885-128">Następnie można dodać nowy obiekt <xref:System.Xml.Linq.XElement> przed przyległych elementu podrzędnego za pomocą metody <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="89885-128">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="89885-129">Nowy obiekt <xref:System.Xml.Linq.XElement> można również dodać po przyległych podelementach przy użyciu metody <xref:System.Xml.Linq.XNode.AddAfterSelf%2A>.</span><span class="sxs-lookup"><span data-stu-id="89885-129">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>

    <span data-ttu-id="89885-130">W poniższym przykładzie przedstawiono przykłady poszczególnych technik.</span><span class="sxs-lookup"><span data-stu-id="89885-130">The following example shows examples of each of these techniques.</span></span>

    [!code-vb[VbXmlSamples2#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#6)]

    <span data-ttu-id="89885-131">Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="89885-131">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="89885-132">Źródłowy kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-132">Source XML:</span></span>

    ```xml
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
    ```

    <span data-ttu-id="89885-133">Zmodyfikowano kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-133">Modified XML:</span></span>

    ```xml
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

### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="89885-134">Aby usunąć element lub atrybut z literału XML</span><span class="sxs-lookup"><span data-stu-id="89885-134">To remove an element or attribute from an XML literal</span></span>

1. <span data-ttu-id="89885-135">Aby usunąć element lub atrybut z literału XML, Uzyskaj odwołanie do elementu lub atrybutu i Wywołaj metodę `Remove`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="89885-135">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>

    [!code-vb[VbXmlSamples2#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#7)]

    <span data-ttu-id="89885-136">Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="89885-136">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="89885-137">Źródłowy kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-137">Source XML:</span></span>

    ```xml
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
    ```

    <span data-ttu-id="89885-138">Zmodyfikowano kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-138">Modified XML:</span></span>

    ```xml
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

    <span data-ttu-id="89885-139">Aby usunąć wszystkie elementy lub atrybuty z literału XML, Uzyskaj odwołanie do literału XML i Wywołaj metodę <xref:System.Xml.Linq.XElement.RemoveAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="89885-139">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>

### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="89885-140">Aby zmodyfikować literał XML</span><span class="sxs-lookup"><span data-stu-id="89885-140">To modify an XML literal</span></span>

1. <span data-ttu-id="89885-141">Aby zmienić nazwę elementu XML, najpierw Uzyskaj odwołanie do elementu.</span><span class="sxs-lookup"><span data-stu-id="89885-141">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="89885-142">Następnie można utworzyć nowy obiekt <xref:System.Xml.Linq.XElement>, który ma nową nazwę i przekazać nowy obiekt <xref:System.Xml.Linq.XElement> do metody <xref:System.Xml.Linq.XNode.ReplaceWith%2A> istniejącego obiektu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="89885-142">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>

    <span data-ttu-id="89885-143">Jeśli element, który jest zastępowany, ma elementy podrzędne, które muszą zostać zachowane, ustaw wartość nowego obiektu <xref:System.Xml.Linq.XElement> na Właściwość <xref:System.Xml.Linq.XContainer.Nodes%2A> istniejącego elementu.</span><span class="sxs-lookup"><span data-stu-id="89885-143">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="89885-144">Spowoduje to ustawienie wartości nowego elementu na wewnętrzny kod XML istniejącego elementu.</span><span class="sxs-lookup"><span data-stu-id="89885-144">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="89885-145">W przeciwnym razie można ustawić wartość nowego elementu na Właściwość `Value` istniejącego elementu.</span><span class="sxs-lookup"><span data-stu-id="89885-145">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>

    <span data-ttu-id="89885-146">Poniższy przykład kodu zastępuje wszystkie \<opis > elementy z \<abstrakcyjną > elementu.</span><span class="sxs-lookup"><span data-stu-id="89885-146">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="89885-147">Zawartość elementu \<Description > jest zachowywana w nowym \<abstrakcyjnym > elementu przy użyciu właściwości <xref:System.Xml.Linq.XContainer.Nodes%2A> opis \<>.<xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="89885-147">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>

    [!code-vb[VbXmlSamples2#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXmlSamples2/VB/Module2.vb#8)]

    <span data-ttu-id="89885-148">Poniżej przedstawiono przykładowy źródłowy kod XML i zmodyfikowany kod XML z tego przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="89885-148">The following shows sample source XML and modified XML from this code example.</span></span>

    <span data-ttu-id="89885-149">Źródłowy kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-149">Source XML:</span></span>

    ```xml
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
    ```

    <span data-ttu-id="89885-150">Zmodyfikowano kod XML:</span><span class="sxs-lookup"><span data-stu-id="89885-150">Modified XML:</span></span>

    ```xml
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

## <a name="see-also"></a><span data-ttu-id="89885-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89885-151">See also</span></span>

- [<span data-ttu-id="89885-152">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89885-152">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="89885-153">XML</span><span class="sxs-lookup"><span data-stu-id="89885-153">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="89885-154">Instrukcje: ładowanie kodu XML z pliku, ciągu lub strumienia</span><span class="sxs-lookup"><span data-stu-id="89885-154">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="89885-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="89885-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="89885-156">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89885-156">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
