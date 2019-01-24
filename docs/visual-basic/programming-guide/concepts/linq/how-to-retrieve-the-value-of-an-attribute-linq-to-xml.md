---
title: 'Instrukcje: Pobieranie wartości atrybutu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: ab14072317bf963e87534b743e3c5a6c39ee39c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690725"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="f8827-102">Instrukcje: Pobieranie wartości atrybutu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8827-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="f8827-103">W tym temacie przedstawiono sposób uzyskania wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f8827-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="f8827-104">Istnieją dwa sposoby: Można rzutować <xref:System.Xml.Linq.XAttribute> żądany typ; operator jawnej konwersji następnie konwertuje zawartość element lub atrybut do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="f8827-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="f8827-105">Alternatywnie, można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8827-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="f8827-106">Jednak zazwyczaj lepszym rozwiązaniem jest rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="f8827-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="f8827-107">Jeśli możesz rzutować atrybutu typu dopuszczającego wartość null, kod jest prostszy do zapisania podczas pobierania wartości atrybutu, który może być lub może nie istnieć.</span><span class="sxs-lookup"><span data-stu-id="f8827-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="f8827-108">Aby zapoznać się z przykładami korzystania z tej techniki, zobacz [jak: Pobieranie wartości elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f8827-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8827-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8827-109">Example</span></span>  
 <span data-ttu-id="f8827-110">W języku Visual Basic właściwość atrybutu zintegrowane służy do pobierania wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f8827-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="f8827-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f8827-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="f8827-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8827-112">Example</span></span>  
 <span data-ttu-id="f8827-113">W języku Visual Basic właściwość atrybutu zintegrowane służy do ustawiania wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f8827-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="f8827-114">Dodatkowo Jeśli używasz właściwości atrybutu zintegrowane można ustawić wartość atrybutu, który nie istnieje atrybut zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="f8827-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="f8827-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f8827-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="f8827-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8827-116">Example</span></span>  
 <span data-ttu-id="f8827-117">Poniższy przykład pokazuje sposób pobierania wartości atrybutu którym atrybut jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f8827-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="f8827-118">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="f8827-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f8827-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f8827-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8827-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8827-120">See also</span></span>
- [<span data-ttu-id="f8827-121">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8827-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
