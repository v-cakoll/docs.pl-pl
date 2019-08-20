---
title: 'Instrukcje: Pobierz pojedynczy atrybut (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4a1be51c7f0e89a8f211ae523eb102282bd9747b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592652"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="850dd-102">Instrukcje: Pobierz pojedynczy atrybut (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="850dd-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="850dd-103">W tym temacie wyjaśniono, jak pobrać pojedynczy atrybut elementu, pod nazwą atrybutu.</span><span class="sxs-lookup"><span data-stu-id="850dd-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="850dd-104">Jest to przydatne w przypadku pisania wyrażeń zapytania, gdzie chcesz znaleźć element, który ma określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="850dd-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="850dd-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Metoda klasy<xref:System.Xml.Linq.XElement> zwraca z<xref:System.Xml.Linq.XAttribute> określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="850dd-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="850dd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="850dd-106">Example</span></span>  
 <span data-ttu-id="850dd-107">W poniższym przykładzie zastosowano <xref:System.Xml.Linq.XElement.Attribute%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="850dd-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="850dd-108">Ten przykład umożliwia znalezienie wszystkich elementów podrzędnych w drzewie o nazwie `Phone`, a następnie znalezienie atrybutu o nazwie `type`.</span><span class="sxs-lookup"><span data-stu-id="850dd-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="850dd-109">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="850dd-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="850dd-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="850dd-110">Example</span></span>  
 <span data-ttu-id="850dd-111">Jeśli chcesz pobrać wartość atrybutu, możesz go rzutować, tak jak w przypadku <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="850dd-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="850dd-112">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="850dd-112">The following example demonstrates this.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =   
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="850dd-113">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="850dd-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="850dd-114">zapewnia jawne Operatory rzutowania dla <xref:System.Xml.Linq.XAttribute> klasy do `string` `int` `bool?` `bool` `int?`,, ,,`long?`,, ,,,`uint?` `uint` `long` `ulong`, `ulong?` ,`float?` ,,`TimeSpan`, ,`decimal?`, ,,`TimeSpan?`,, ,`GUID`i `float` `double` `DateTime` `double?` `decimal` `DateTime?`  `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="850dd-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="850dd-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="850dd-115">Example</span></span>  
 <span data-ttu-id="850dd-116">Poniższy przykład pokazuje ten sam kod dla atrybutu, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="850dd-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="850dd-117">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="850dd-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 <span data-ttu-id="850dd-118">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="850dd-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="850dd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="850dd-119">See also</span></span>

- [<span data-ttu-id="850dd-120">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="850dd-120">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
