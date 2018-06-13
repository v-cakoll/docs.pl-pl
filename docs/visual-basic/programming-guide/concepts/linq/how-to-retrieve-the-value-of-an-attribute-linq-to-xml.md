---
title: 'Porady: pobieranie wartości atrybutu (LINQ do XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 96d5e5a0c7ee294b140385c93b13ee56f3f92491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642957"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="316e5-102">Porady: pobieranie wartości atrybutu (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="316e5-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="316e5-103">W tym temacie przedstawiono sposób uzyskiwania wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="316e5-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="316e5-104">Istnieją dwa sposoby: można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ.; operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="316e5-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="316e5-105">Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="316e5-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="316e5-106">Rzutowanie jest jednak ogólnie lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="316e5-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="316e5-107">Jeśli rzutowania atrybut do typu dopuszczającego wartość null, kod jest łatwiejsze do zapisania podczas pobierania wartości atrybutu, który może lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="316e5-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="316e5-108">Przykłady tej metody, zobacz [porady: pobieranie wartości elementu (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="316e5-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="316e5-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="316e5-109">Example</span></span>  
 <span data-ttu-id="316e5-110">W języku Visual Basic właściwość zintegrowane atrybutu służy do pobierania wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="316e5-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="316e5-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="316e5-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="316e5-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="316e5-112">Example</span></span>  
 <span data-ttu-id="316e5-113">W języku Visual Basic służy właściwości atrybutu zintegrowane można ustawić wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="316e5-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="316e5-114">Ponadto użycie właściwości atrybutu zintegrowane można ustawić wartość atrybutu, który nie istnieje, zostanie utworzona atrybutu.</span><span class="sxs-lookup"><span data-stu-id="316e5-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="316e5-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="316e5-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="316e5-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="316e5-116">Example</span></span>  
 <span data-ttu-id="316e5-117">Poniższy przykład pokazuje, jak można pobrać wartości atrybutu którym atrybut jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="316e5-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="316e5-118">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="316e5-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="316e5-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="316e5-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="316e5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="316e5-120">See Also</span></span>  
 [<span data-ttu-id="316e5-121">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="316e5-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
