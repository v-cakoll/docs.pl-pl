---
title: Jak pobrać pojedynczy atrybut (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 830a7be24702b6037ac62471060fbe49d8ded598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168716"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="63851-102">Jak pobrać pojedynczy atrybut (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="63851-102">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="63851-103">W tym temacie wyjaśniono, jak pobrać pojedynczy atrybut elementu, biorąc pod uwagę nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="63851-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="63851-104">Jest to przydatne do pisania wyrażeń kwerendy, gdzie chcesz znaleźć element, który ma określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="63851-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="63851-105">Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement> klasy zwraca <xref:System.Xml.Linq.XAttribute> o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="63851-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63851-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="63851-106">Example</span></span>  
 <span data-ttu-id="63851-107">W poniższym <xref:System.Xml.Linq.XElement.Attribute%2A> przykładzie użyto metody.</span><span class="sxs-lookup"><span data-stu-id="63851-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="63851-108">W tym przykładzie znajduje wszystkie elementy `Phone`podrzędne w `type`drzewie o nazwie , a następnie znajduje atrybut o nazwie .</span><span class="sxs-lookup"><span data-stu-id="63851-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="63851-109">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="63851-109">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="63851-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="63851-110">Example</span></span>  
 <span data-ttu-id="63851-111">Jeśli chcesz pobrać wartość atrybutu, możesz rzutować go, tak <xref:System.Xml.Linq.XElement> jak w przypadku obiektów.</span><span class="sxs-lookup"><span data-stu-id="63851-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="63851-112">Poniższy przykład pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="63851-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="63851-113">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="63851-113">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="63851-114">zapewnia wyraźne odlewane operatory <xref:System.Xml.Linq.XAttribute> dla `uint`klasy `uint?` `long`do `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `bool?` `int` `int?` `TimeSpan` `TimeSpan?` `GUID` `GUID?`, `bool`, , , , , , , , , , , , , , , , i . `string`</span><span class="sxs-lookup"><span data-stu-id="63851-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63851-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="63851-115">Example</span></span>  
 <span data-ttu-id="63851-116">W poniższym przykładzie przedstawiono ten sam kod atrybutu, który znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="63851-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="63851-117">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="63851-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="63851-118">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="63851-118">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="63851-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63851-119">See also</span></span>

- [<span data-ttu-id="63851-120">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="63851-120">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
