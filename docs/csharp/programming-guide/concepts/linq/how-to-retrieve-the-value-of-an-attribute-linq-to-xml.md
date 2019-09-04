---
title: 'Instrukcje: Pobierz wartość atrybutu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 635aee3bd08618b94fb5c091f8eef212c067acef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253380"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="84fe7-102">Instrukcje: Pobierz wartość atrybutu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="84fe7-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="84fe7-103">W tym temacie pokazano, jak uzyskać wartość atrybutów.</span><span class="sxs-lookup"><span data-stu-id="84fe7-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="84fe7-104">Istnieją dwa główne sposoby: Można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ; operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="84fe7-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="84fe7-105">Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="84fe7-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="84fe7-106">Jednak Rzutowanie jest ogólnie lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="84fe7-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="84fe7-107">Jeśli rzutowany atrybut na typ dopuszczający wartość null, kod jest łatwiejszy do zapisu podczas pobierania wartości atrybutu, który może lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="84fe7-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="84fe7-108">Przykłady tej techniki można znaleźć w temacie [How to: Pobierz wartość elementu (LINQ to XML) (C#).](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="84fe7-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84fe7-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="84fe7-109">Example</span></span>  
 <span data-ttu-id="84fe7-110">Aby pobrać wartość atrybutu, wystarczy przerzutować <xref:System.Xml.Linq.XAttribute> obiekt na żądany typ.</span><span class="sxs-lookup"><span data-stu-id="84fe7-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="84fe7-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="84fe7-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="84fe7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="84fe7-112">Example</span></span>  
 <span data-ttu-id="84fe7-113">Poniższy przykład pokazuje, jak pobrać wartość atrybutu, gdzie atrybut znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="84fe7-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="84fe7-114">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="84fe7-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="84fe7-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="84fe7-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="84fe7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84fe7-116">See also</span></span>

- [<span data-ttu-id="84fe7-117">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="84fe7-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
