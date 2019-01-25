---
title: Wprowadzenie do literałów XML w Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: b6c4773236c3af83603033c74e2e12e9f47a86b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624031"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="28986-102">Wprowadzenie do literałów XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28986-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="28986-103">Ta sekcja zawiera informacje dotyczące tworzenia drzew XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="28986-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="28986-104">Aby dowiedzieć się, jak za pomocą wyników zapytania LINQ jako zawartość dla drzewa XML, zobacz [konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="28986-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="28986-105">Aby uzyskać więcej informacji na temat literałów XML w Visual Basic, zobacz [Przegląd LINQ to XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="28986-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="28986-106">Tworzenie drzew XML</span><span class="sxs-lookup"><span data-stu-id="28986-106">Creating XML Trees</span></span>  
 <span data-ttu-id="28986-107">Poniższy przykład pokazuje, jak utworzyć <xref:System.Xml.Linq.XElement>, w tym przypadku `contacts`:</span><span class="sxs-lookup"><span data-stu-id="28986-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="28986-108">Tworzenie XElement za pomocą prostej zawartości</span><span class="sxs-lookup"><span data-stu-id="28986-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="28986-109">Możesz utworzyć <xref:System.Xml.Linq.XElement> prostej zawartości, która zawiera w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="28986-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 <span data-ttu-id="28986-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28986-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="28986-111">Tworzenie pustego elementu</span><span class="sxs-lookup"><span data-stu-id="28986-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="28986-112">Możesz utworzyć pustą <xref:System.Xml.Linq.XElement>, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="28986-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="28986-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28986-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="28986-114">Za pomocą wyrażenia osadzone</span><span class="sxs-lookup"><span data-stu-id="28986-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="28986-115">Ważną funkcją literałów XML jest, że zezwalają na wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="28986-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="28986-116">Wyrażenia osadzone umożliwiają ocena wyrażenia i Wstaw wyniki wyrażenia do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="28986-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="28986-117">Jeśli wyrażenie typu <xref:System.Xml.Linq.XElement>, element jest wstawiany do drzewa.</span><span class="sxs-lookup"><span data-stu-id="28986-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="28986-118">Jeśli wyrażenie typu <xref:System.Xml.Linq.XAttribute>, atrybut jest wstawiany do drzewa.</span><span class="sxs-lookup"><span data-stu-id="28986-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="28986-119">W drzewie, tylko gdy są one prawidłowe, można wstawić elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="28986-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="28986-120">Należy zauważyć pojedyncze wyrażenie mogą być wprowadzanie do wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="28986-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="28986-121">Nie można osadzić użycie wielu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="28986-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="28986-122">Jeśli wyrażenie wykracza poza jednym wierszu, należy użyć wstawić znak kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="28986-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="28986-123">Jeśli używasz osadzone wyrażenie Aby dodać istniejące węzły (w tym elementy) i atrybuty do nowego drzewa XML, a jeśli istniejące węzły są już elementem nadrzędnym w węzłach są klonowane.</span><span class="sxs-lookup"><span data-stu-id="28986-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="28986-124">Nowo sklonowanego węzły są dołączone do nowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="28986-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="28986-125">Jeśli istniejące węzły są elementu nadrzędnego, węzły są po prostu dołączone do nowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="28986-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="28986-126">Przykład ostatniego, w tym temacie przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="28986-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="28986-127">W poniższym przykładzie użyto wyrażenia osadzone, aby wstawić element do drzewa:</span><span class="sxs-lookup"><span data-stu-id="28986-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
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
  
 <span data-ttu-id="28986-128">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28986-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="28986-129">Za pomocą wyrażenia osadzone w zawartości</span><span class="sxs-lookup"><span data-stu-id="28986-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="28986-130">Wyrażenia osadzone służy do dostarczania zawartości elementu:</span><span class="sxs-lookup"><span data-stu-id="28986-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="28986-131">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28986-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="28986-132">W wyrażeniu Embedded za pomocą zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="28986-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="28986-133">Można użyć z wynikami zapytania LINQ dla zawartości elementu:</span><span class="sxs-lookup"><span data-stu-id="28986-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="28986-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28986-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="28986-135">Za pomocą wyrażenia osadzone dla nazwy węzła</span><span class="sxs-lookup"><span data-stu-id="28986-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="28986-136">Wyrażenia osadzone umożliwia również obliczyć nazwy atrybutu, wartości atrybutów, nazwy elementów i wartości elementów:</span><span class="sxs-lookup"><span data-stu-id="28986-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
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
  
 <span data-ttu-id="28986-137">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28986-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="28986-138">Klonowanie a Dołączanie</span><span class="sxs-lookup"><span data-stu-id="28986-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="28986-139">Jak wspomniano wcześniej, korzystając z wyrażenia osadzone dodać istniejące węzły (w tym elementy) i atrybuty do nowego drzewa XML, jeśli istniejące węzły są już nadrzędny, węzły są klonowane, a nowo sklonowanego węzły są dołączone do nowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="28986-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="28986-140">Jeśli istniejące węzły są elementu nadrzędnego, są one po prostu dołączone do nowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="28986-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
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
  
 <span data-ttu-id="28986-141">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28986-141">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="28986-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28986-142">See also</span></span>
- [<span data-ttu-id="28986-143">Tworzenie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28986-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
