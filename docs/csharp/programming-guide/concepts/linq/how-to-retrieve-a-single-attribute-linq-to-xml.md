---
title: 'Porady: pobieranie jeden atrybut (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 55da36099af72259a4e72205f142ab855f000c4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="6fed2-102">Porady: pobieranie jeden atrybut (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6fed2-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="6fed2-103">W tym temacie wyjaśniono, jak pobrać jeden atrybut elementu jest podana nazwa atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6fed2-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="6fed2-104">Jest to przydatne dla wyrażeń zapytania, które chcesz znaleźć element, który ma określonego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6fed2-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="6fed2-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Metody <xref:System.Xml.Linq.XElement> klasy zwraca <xref:System.Xml.Linq.XAttribute> o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="6fed2-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fed2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fed2-106">Example</span></span>  
 <span data-ttu-id="6fed2-107">W poniższym przykładzie użyto <xref:System.Xml.Linq.XElement.Attribute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6fed2-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="6fed2-108">W tym przykładzie znajduje wszystkie elementy podrzędne w drzewie o nazwie `Phone`, a następnie znalezienie atrybutu o nazwie `type`.</span><span class="sxs-lookup"><span data-stu-id="6fed2-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="6fed2-109">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6fed2-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="6fed2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fed2-110">Example</span></span>  
 <span data-ttu-id="6fed2-111">Jeśli chcesz pobrać wartość atrybutu można rzutować, podobnie jak w przypadku z <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6fed2-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="6fed2-112">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="6fed2-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="6fed2-113">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6fed2-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6fed2-114"> zawiera operatory jawnego rzutowania <xref:System.Xml.Linq.XAttribute> klasy do `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`i `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="6fed2-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fed2-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fed2-115">Example</span></span>  
 <span data-ttu-id="6fed2-116">Poniższy przykład przedstawia ten sam kod dla atrybutu, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6fed2-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="6fed2-117">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="6fed2-117">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="6fed2-118">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6fed2-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fed2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fed2-119">See Also</span></span>  
 [<span data-ttu-id="6fed2-120">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6fed2-120">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
