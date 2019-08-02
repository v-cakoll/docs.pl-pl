---
title: 'Instrukcje: Pobierz wartość atrybutu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: e099c20a519563eba2a060320b36761ebe54e0f1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710072"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="5ffbe-102">Instrukcje: Pobierz wartość atrybutu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5ffbe-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5ffbe-103">W tym temacie pokazano, jak uzyskać wartość atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5ffbe-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="5ffbe-104">Istnieją dwa główne sposoby: Można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ; operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="5ffbe-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="5ffbe-105">Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ffbe-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="5ffbe-106">Jednak Rzutowanie jest ogólnie lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="5ffbe-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="5ffbe-107">Jeśli rzutowany atrybut na typ dopuszczający wartość null, kod jest łatwiejszy do zapisu podczas pobierania wartości atrybutu, który może lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="5ffbe-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="5ffbe-108">Przykłady tej techniki można znaleźć w temacie [How to: Pobierz wartość elementu (LINQ to XML) (C#).](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="5ffbe-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ffbe-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ffbe-109">Example</span></span>  
 <span data-ttu-id="5ffbe-110">Aby pobrać wartość atrybutu, wystarczy przerzutować <xref:System.Xml.Linq.XAttribute> obiekt na żądany typ.</span><span class="sxs-lookup"><span data-stu-id="5ffbe-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="5ffbe-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5ffbe-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="5ffbe-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ffbe-112">Example</span></span>  
 <span data-ttu-id="5ffbe-113">Poniższy przykład pokazuje, jak pobrać wartość atrybutu, gdzie atrybut znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5ffbe-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="5ffbe-114">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5ffbe-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="5ffbe-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="5ffbe-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ffbe-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ffbe-116">See also</span></span>

- [<span data-ttu-id="5ffbe-117">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5ffbe-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
