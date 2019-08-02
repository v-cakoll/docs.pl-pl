---
title: 'Instrukcje: Pobierz wartość atrybutu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: d03b2b146ad2f6b796ba6589cf99d06aa429535d
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710495"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="ba4cf-102">Instrukcje: Pobierz wartość atrybutu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba4cf-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ba4cf-103">W tym temacie pokazano, jak uzyskać wartość atrybutów.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="ba4cf-104">Istnieją dwa główne sposoby: Można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ; operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="ba4cf-105">Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="ba4cf-106">Jednak Rzutowanie jest ogólnie lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="ba4cf-107">Jeśli rzutowany atrybut na typ dopuszczający wartość null, kod jest łatwiejszy do zapisu podczas pobierania wartości atrybutu, który może lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="ba4cf-108">Przykłady tej techniki można znaleźć w temacie [How to: Pobierz wartość elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ba4cf-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba4cf-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba4cf-109">Example</span></span>  
 <span data-ttu-id="ba4cf-110">W Visual Basic można użyć właściwości Integrated Attribute, aby pobrać wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="ba4cf-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ba4cf-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="ba4cf-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba4cf-112">Example</span></span>  
 <span data-ttu-id="ba4cf-113">W Visual Basic można użyć właściwości Integrated Attribute, aby ustawić wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="ba4cf-114">Ponadto w przypadku użycia właściwości Integrated Attribute do ustawienia wartości atrybutu, który nie istnieje, atrybut zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="ba4cf-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ba4cf-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="ba4cf-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba4cf-116">Example</span></span>  
 <span data-ttu-id="ba4cf-117">Poniższy przykład pokazuje, jak pobrać wartość atrybutu, gdzie atrybut znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="ba4cf-118">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ba4cf-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="ba4cf-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ba4cf-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba4cf-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba4cf-120">See also</span></span>

- [<span data-ttu-id="ba4cf-121">Osie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba4cf-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
