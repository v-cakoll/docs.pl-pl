---
title: Wprowadzenie do literałów XML w języku Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 9f5c54574e51c537d9ea58d307afda10736d0d88
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266953"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="3a9fe-102">Wprowadzenie do literałów XML w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a9fe-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="3a9fe-103">Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="3a9fe-104">Aby uzyskać informacje na temat używania wyników zapytań LINQ jako zawartości drzewa XML, zobacz [Konstrukcja funkcjonalna (LINQ do XML) (Visual Basic).](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="3a9fe-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3a9fe-105">Aby uzyskać więcej informacji na temat literałów XML w języku Visual Basic, zobacz [Omówienie LINQ do XML w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3a9fe-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="3a9fe-106">Tworzenie drzew XML</span><span class="sxs-lookup"><span data-stu-id="3a9fe-106">Creating XML Trees</span></span>  
 <span data-ttu-id="3a9fe-107">W poniższym <xref:System.Xml.Linq.XElement>przykładzie pokazano, jak `contacts`utworzyć , w tym przypadku:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="3a9fe-108">Tworzenie XElement z prostą zawartością</span><span class="sxs-lookup"><span data-stu-id="3a9fe-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="3a9fe-109">Można utworzyć <xref:System.Xml.Linq.XElement> zawartość prostą w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 <span data-ttu-id="3a9fe-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="3a9fe-111">Tworzenie pustego elementu</span><span class="sxs-lookup"><span data-stu-id="3a9fe-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="3a9fe-112">Można utworzyć pustą <xref:System.Xml.Linq.XElement>, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="3a9fe-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="3a9fe-114">Korzystanie z wyrażeń osadzonych</span><span class="sxs-lookup"><span data-stu-id="3a9fe-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="3a9fe-115">Ważną cechą literałów XML jest to, że zezwalają na osadzone wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="3a9fe-116">Osadzone wyrażenia umożliwiają ocenę wyrażenia i wstawianie wyników wyrażenia do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="3a9fe-117">Jeśli wyrażenie jest obliczane <xref:System.Xml.Linq.XElement>na typ , element jest wstawiany do drzewa.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="3a9fe-118">Jeśli wyrażenie jest obliczane <xref:System.Xml.Linq.XAttribute>na typ , atrybut jest wstawiany do drzewa.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="3a9fe-119">Elementy i atrybuty można wstawiać do drzewa tylko wtedy, gdy są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="3a9fe-120">Należy pamiętać, że tylko pojedyncze wyrażenie może przejść do wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="3a9fe-121">Nie można osadzić wielu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="3a9fe-122">Jeśli wyrażenie wykracza poza pojedynczy wiersz, należy użyć znaku kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="3a9fe-123">Jeśli użyto wyrażenia osadzonego do dodania istniejących węzłów (w tym elementów) i atrybutów do nowego drzewa XML, a istniejące węzły są już nadrzędne, węzły zostaną sklonowane.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="3a9fe-124">Nowo sklonowane węzły są dołączone do nowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="3a9fe-125">Jeśli istniejące węzły nie są nadrzędne, węzły są po prostu dołączone do nowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="3a9fe-126">Ostatni przykład w tym temacie pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="3a9fe-127">W poniższym przykładzie użyto wyrażenia osadzonego w celu wstawienia elementu do drzewa:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 <span data-ttu-id="3a9fe-128">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="3a9fe-129">Używanie osadzonych wyrażeń dla zawartości</span><span class="sxs-lookup"><span data-stu-id="3a9fe-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="3a9fe-130">Za pomocą wyrażenia osadzonego można podać zawartość elementu:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="3a9fe-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="3a9fe-132">Używanie zapytania LINQ w wyrażeniu osadzonym</span><span class="sxs-lookup"><span data-stu-id="3a9fe-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="3a9fe-133">Można użyć wyników kwerendy LINQ dla zawartości elementu:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="3a9fe-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="3a9fe-135">Używanie osadzonych wyrażeń dla nazw węzłów</span><span class="sxs-lookup"><span data-stu-id="3a9fe-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="3a9fe-136">Można również użyć wyrażeń osadzonych do obliczania nazw atrybutów, wartości atrybutów, nazw elementów i wartości elementów:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="3a9fe-137">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="3a9fe-138">Klonowanie a dołączanie</span><span class="sxs-lookup"><span data-stu-id="3a9fe-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="3a9fe-139">Jak wspomniano wcześniej, jeśli używasz wyrażenia osadzonego, aby dodać istniejące węzły (w tym elementy) i atrybuty do nowego drzewa XML, jeśli istniejące węzły są już nadrzędne, węzły są klonowane, a nowo sklonowane węzły są dołączone do nowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="3a9fe-140">Jeśli istniejące węzły nie są nadrzędne, są po prostu dołączone do nowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3a9fe-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="3a9fe-141">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a9fe-141">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a9fe-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a9fe-142">See also</span></span>

- [<span data-ttu-id="3a9fe-143">Tworzenie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a9fe-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
