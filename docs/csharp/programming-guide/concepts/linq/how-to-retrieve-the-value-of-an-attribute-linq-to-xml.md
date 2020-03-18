---
title: Jak pobrać wartość atrybutu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347433"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="21baa-102">Jak pobrać wartość atrybutu (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="21baa-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="21baa-103">W tym temacie pokazano, jak uzyskać wartość atrybutów.</span><span class="sxs-lookup"><span data-stu-id="21baa-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="21baa-104">Istnieją dwa główne sposoby: Można <xref:System.Xml.Linq.XAttribute> rzucić do żądanego typu; operator konwersji jawnej następnie konwertuje zawartość elementu lub atrybutu na określony typ.</span><span class="sxs-lookup"><span data-stu-id="21baa-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="21baa-105">Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="21baa-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="21baa-106">Jednak casting jest na ogół lepszym podejściem.</span><span class="sxs-lookup"><span data-stu-id="21baa-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="21baa-107">Jeśli rzutowane atrybut udopuszczający typ, kod jest prostszy do zapisu podczas pobierania wartości atrybutu, który może lub nie może istnieć.</span><span class="sxs-lookup"><span data-stu-id="21baa-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="21baa-108">Przykłady tej techniki można znaleźć w [części Jak pobrać wartość elementu (LINQ do XML) (C#).](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="21baa-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21baa-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="21baa-109">Example</span></span>  
 <span data-ttu-id="21baa-110">Aby pobrać wartość atrybutu, wystarczy <xref:System.Xml.Linq.XAttribute> rzutować obiekt do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="21baa-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="21baa-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="21baa-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="21baa-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="21baa-112">Example</span></span>  
 <span data-ttu-id="21baa-113">W poniższym przykładzie pokazano, jak pobrać wartość atrybutu, w którym atrybut znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="21baa-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="21baa-114">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="21baa-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="21baa-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="21baa-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="21baa-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21baa-116">See also</span></span>

- [<span data-ttu-id="21baa-117">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="21baa-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
