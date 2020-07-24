---
title: Jak pobrać pojedynczy atrybut (LINQ to XML) (C#)
description: Dowiedz się, jak używać LINQ to XML pobrać pojedynczy atrybut elementu w języku C#, używając nazwy atrybutu.
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4efcae5324ad5a2e4664e68e35e15ec2053daece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103434"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="996ab-103">Jak pobrać pojedynczy atrybut (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="996ab-103">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="996ab-104">W tym temacie wyjaśniono, jak pobrać pojedynczy atrybut elementu, pod nazwą atrybutu.</span><span class="sxs-lookup"><span data-stu-id="996ab-104">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="996ab-105">Jest to przydatne w przypadku pisania wyrażeń zapytania, gdzie chcesz znaleźć element, który ma określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="996ab-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="996ab-106"><xref:System.Xml.Linq.XElement.Attribute%2A>Metoda <xref:System.Xml.Linq.XElement> klasy zwraca <xref:System.Xml.Linq.XAttribute> z określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="996ab-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="996ab-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="996ab-107">Example</span></span>  
 <span data-ttu-id="996ab-108">W poniższym przykładzie zastosowano <xref:System.Xml.Linq.XElement.Attribute%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="996ab-108">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="996ab-109">Ten przykład umożliwia znalezienie wszystkich elementów podrzędnych w drzewie o nazwie `Phone` , a następnie znalezienie atrybutu o nazwie `type` .</span><span class="sxs-lookup"><span data-stu-id="996ab-109">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="996ab-110">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="996ab-110">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="996ab-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="996ab-111">Example</span></span>  
 <span data-ttu-id="996ab-112">Jeśli chcesz pobrać wartość atrybutu, możesz go rzutować, tak jak w przypadku <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="996ab-112">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="996ab-113">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="996ab-113">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="996ab-114">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="996ab-114">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="996ab-115">zapewnia jawne Operatory rzutowania dla klasy do,,,,,,,,,,,,,,,,,,,, <xref:System.Xml.Linq.XAttribute> `string` `bool` `bool?` `int` `int?` `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` ,, `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `GUID` i `GUID?` .</span><span class="sxs-lookup"><span data-stu-id="996ab-115">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="996ab-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="996ab-116">Example</span></span>  
 <span data-ttu-id="996ab-117">Poniższy przykład pokazuje ten sam kod dla atrybutu, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="996ab-117">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="996ab-118">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="996ab-118">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="996ab-119">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="996ab-119">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="996ab-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="996ab-120">See also</span></span>

- [<span data-ttu-id="996ab-121">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="996ab-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
