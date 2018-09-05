---
title: 'Porady: pobieranie wartości atrybutu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: a78cda390cc7b3d489cfda212cf8fb8111e4dde2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501507"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="9c017-102">Porady: pobieranie wartości atrybutu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9c017-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9c017-103">W tym temacie przedstawiono sposób uzyskania wartości atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9c017-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="9c017-104">Istnieją dwa sposoby: mogą być rzutowane <xref:System.Xml.Linq.XAttribute> żądany typ; operator jawnej konwersji następnie konwertuje zawartość element lub atrybut do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="9c017-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="9c017-105">Alternatywnie, można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9c017-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="9c017-106">Jednak zazwyczaj lepszym rozwiązaniem jest rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="9c017-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="9c017-107">Jeśli możesz rzutować atrybutu typu dopuszczającego wartość null, kod jest prostszy do zapisania podczas pobierania wartości atrybutu, który może być lub może nie istnieć.</span><span class="sxs-lookup"><span data-stu-id="9c017-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="9c017-108">Aby zapoznać się z przykładami korzystania z tej techniki, zobacz [porady: pobieranie wartości elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9c017-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c017-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c017-109">Example</span></span>  
 <span data-ttu-id="9c017-110">Aby pobrać wartość atrybutu, możesz po prostu rzutowania <xref:System.Xml.Linq.XAttribute> obiektu do żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="9c017-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="9c017-111">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9c017-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="9c017-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c017-112">Example</span></span>  
 <span data-ttu-id="9c017-113">Poniższy przykład pokazuje sposób pobierania wartości atrybutu którym atrybut jest w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9c017-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="9c017-114">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="9c017-114">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="9c017-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9c017-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c017-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c017-116">See Also</span></span>

- [<span data-ttu-id="9c017-117">LINQ do XML osi (C#)</span><span class="sxs-lookup"><span data-stu-id="9c017-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
