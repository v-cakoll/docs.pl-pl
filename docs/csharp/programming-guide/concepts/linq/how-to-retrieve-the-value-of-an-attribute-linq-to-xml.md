---
title: Jak pobrać wartość atrybutu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 212ad3bb3097e7e2c76da8f165011b181f329d4c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249197"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="faac9-102">Jak pobrać wartość atrybutu (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="faac9-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="faac9-103">W tym temacie pokazano, jak uzyskać wartość atrybutów.</span><span class="sxs-lookup"><span data-stu-id="faac9-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="faac9-104">Istnieją dwa główne sposoby: <xref:System.Xml.Linq.XAttribute> można rzucić do żądanego typu; operator konwersji jawne następnie konwertuje zawartość elementu lub atrybutu do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="faac9-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="faac9-105">Goście mogą również skorzystać <xref:System.Xml.Linq.XAttribute.Value%2A> z obiektu.</span><span class="sxs-lookup"><span data-stu-id="faac9-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="faac9-106">Jednak odlewanie jest na ogół lepszym podejściem.</span><span class="sxs-lookup"><span data-stu-id="faac9-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="faac9-107">Jeśli rzutujesz atrybut na typ wartości możliwej do wartości null, kod jest prostszy do zapisania podczas pobierania wartości atrybutu, który może lub nie może istnieć.</span><span class="sxs-lookup"><span data-stu-id="faac9-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="faac9-108">Aby zapoznać się z przykładami tej techniki, zobacz [Jak pobrać wartość elementu (LINQ do XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="faac9-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="faac9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="faac9-109">Example</span></span>  
 <span data-ttu-id="faac9-110">Aby pobrać wartość atrybutu, wystarczy rzutować <xref:System.Xml.Linq.XAttribute> obiekt do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="faac9-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="faac9-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="faac9-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="faac9-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="faac9-112">Example</span></span>  
 <span data-ttu-id="faac9-113">W poniższym przykładzie pokazano, jak pobrać wartość atrybutu, w którym atrybut znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="faac9-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="faac9-114">Aby uzyskać więcej informacji, zobacz [Omówienie obszarów nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="faac9-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="faac9-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="faac9-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="faac9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="faac9-116">See also</span></span>

- [<span data-ttu-id="faac9-117">Osie LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="faac9-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
