---
title: 'Porady: pobieranie wartości atrybutu (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 224ba9ba47d68afd7c29d0f33fe20d290d0b5ef5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319130"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="6c807-102">Porady: pobieranie wartości atrybutu (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6c807-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="6c807-103">W tym temacie przedstawiono sposób uzyskiwania wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6c807-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="6c807-104">Istnieją dwa sposoby: można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ.; operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="6c807-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="6c807-105">Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6c807-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="6c807-106">Rzutowanie jest jednak ogólnie lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="6c807-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="6c807-107">Jeśli rzutowania atrybut do typu dopuszczającego wartość null, kod jest łatwiejsze do zapisania podczas pobierania wartości atrybutu, który może lub nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="6c807-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="6c807-108">Przykłady tej metody, zobacz [porady: pobieranie wartości elementu (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6c807-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c807-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c807-109">Example</span></span>  
 <span data-ttu-id="6c807-110">Można pobrać wartości atrybutu, możesz po prostu rzutowania <xref:System.Xml.Linq.XAttribute> obiektu do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="6c807-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="6c807-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="6c807-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="6c807-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c807-112">Example</span></span>  
 <span data-ttu-id="6c807-113">Poniższy przykład pokazuje, jak można pobrać wartości atrybutu którym atrybut jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6c807-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="6c807-114">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="6c807-114">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="6c807-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="6c807-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c807-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c807-116">See Also</span></span>  
 [<span data-ttu-id="6c807-117">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6c807-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
