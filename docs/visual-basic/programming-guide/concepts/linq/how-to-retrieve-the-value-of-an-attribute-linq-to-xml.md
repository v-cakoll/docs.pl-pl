---
title: 'Jak: Pobieranie wartości atrybutu (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 6593639dcdc234ddda808cfdb5e85ebe1a771b62
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248950"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="518d9-102">Jak: Pobieranie wartości atrybutu (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="518d9-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="518d9-103">W tym temacie pokazano, jak uzyskać wartość atrybutów.</span><span class="sxs-lookup"><span data-stu-id="518d9-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="518d9-104">Istnieją dwa główne sposoby: <xref:System.Xml.Linq.XAttribute> można rzucić do żądanego typu; operator konwersji jawne następnie konwertuje zawartość elementu lub atrybutu do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="518d9-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="518d9-105">Goście mogą również skorzystać <xref:System.Xml.Linq.XAttribute.Value%2A> z obiektu.</span><span class="sxs-lookup"><span data-stu-id="518d9-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="518d9-106">Jednak odlewanie jest na ogół lepszym podejściem.</span><span class="sxs-lookup"><span data-stu-id="518d9-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="518d9-107">Jeśli rzutujesz atrybut na typ wartości możliwej do wartości null, kod jest prostszy do zapisania podczas pobierania wartości atrybutu, który może lub nie może istnieć.</span><span class="sxs-lookup"><span data-stu-id="518d9-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="518d9-108">Aby zapoznać się z przykładami tej techniki, zobacz [Jak: Pobieranie wartości elementu (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="518d9-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="518d9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="518d9-109">Example</span></span>  
 <span data-ttu-id="518d9-110">W języku Visual Basic można użyć właściwości atrybutu zintegrowanego, aby pobrać wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="518d9-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="518d9-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="518d9-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="518d9-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="518d9-112">Example</span></span>  
 <span data-ttu-id="518d9-113">W języku Visual Basic można użyć właściwości atrybutu zintegrowanego, aby ustawić wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="518d9-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="518d9-114">Ponadto jeśli używasz właściwości atrybutu zintegrowanego, aby ustawić wartość atrybutu, który nie istnieje, zostanie utworzony atrybut.</span><span class="sxs-lookup"><span data-stu-id="518d9-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="518d9-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="518d9-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="518d9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="518d9-116">Example</span></span>  
 <span data-ttu-id="518d9-117">W poniższym przykładzie pokazano, jak pobrać wartość atrybutu, w którym atrybut znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="518d9-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="518d9-118">Aby uzyskać więcej informacji, zobacz [Omówienie obszarów nazw (LINQ do XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="518d9-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="518d9-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="518d9-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="518d9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="518d9-120">See also</span></span>

- [<span data-ttu-id="518d9-121">Osie LINQ do XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="518d9-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
