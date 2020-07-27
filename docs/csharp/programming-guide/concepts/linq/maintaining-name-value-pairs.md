---
title: Obsługa par nazwa-wartość (C#)
description: LINQ to XML zawiera metody, które ułatwiają zachowanie par nazwa-wartość, jako atrybuty lub jako zestaw elementów podrzędnych.
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 92a45d160cbb1ef470d93bf740d0b6f584681e72
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165273"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="4a609-103">Obsługa par nazwa-wartość (C#)</span><span class="sxs-lookup"><span data-stu-id="4a609-103">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="4a609-104">Wiele aplikacji musi utrzymywać informacje, które najlepiej są przechowywane jako pary nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="4a609-104">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="4a609-105">Te informacje mogą dotyczyć informacji konfiguracyjnych lub ustawień globalnych.</span><span class="sxs-lookup"><span data-stu-id="4a609-105">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4a609-106">zawiera kilka metod, które ułatwiają przechowywanie zestawu par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="4a609-106">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="4a609-107">Możesz zachować informacje jako atrybuty lub jako zestaw elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4a609-107">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="4a609-108">Jedną z różnic między przechowywaniem informacji jako atrybuty lub jako elementami podrzędnymi jest to, że atrybuty mogą mieć tylko jeden atrybut z określoną nazwą dla elementu.</span><span class="sxs-lookup"><span data-stu-id="4a609-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="4a609-109">To ograniczenie nie ma zastosowania do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4a609-109">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="4a609-110">SetAttributeValue i SetElementValue</span><span class="sxs-lookup"><span data-stu-id="4a609-110">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="4a609-111">Dwie metody, które ułatwiają utrzymywanie par nazwa/wartość <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> , i <xref:System.Xml.Linq.XElement.SetElementValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="4a609-111">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="4a609-112">Te dwie metody mają podobną semantykę.</span><span class="sxs-lookup"><span data-stu-id="4a609-112">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="4a609-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>może dodawać, modyfikować lub usuwać atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="4a609-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="4a609-114">Jeśli wywoływana jest <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwa atrybutu, który nie istnieje, metoda tworzy nowy atrybut i dodaje go do określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="4a609-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="4a609-115">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i z określoną zawartością, zawartość atrybutu zostanie zastąpiona określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="4a609-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="4a609-116">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i określisz wartość null dla zawartości, atrybut zostanie usunięty z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4a609-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="4a609-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A>może dodawać, modyfikować lub usuwać elementy podrzędne elementu.</span><span class="sxs-lookup"><span data-stu-id="4a609-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="4a609-118">W przypadku wywołania <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą elementu podrzędnego, który nie istnieje, metoda tworzy nowy element i dodaje go do określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="4a609-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="4a609-119">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i z określoną zawartością, zawartość elementu zostanie zastąpiona określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="4a609-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="4a609-120">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i określisz wartość null dla zawartości, element zostanie usunięty z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4a609-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a609-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a609-121">Example</span></span>  
 <span data-ttu-id="4a609-122">Poniższy przykład tworzy element bez atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4a609-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="4a609-123">Następnie używa metody, <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> Aby utworzyć i zachować listę par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="4a609-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="4a609-124">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4a609-124">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="4a609-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a609-125">Example</span></span>  
 <span data-ttu-id="4a609-126">Poniższy przykład tworzy element bez elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4a609-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="4a609-127">Następnie używa metody, <xref:System.Xml.Linq.XElement.SetElementValue%2A> Aby utworzyć i zachować listę par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="4a609-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="4a609-128">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="4a609-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a609-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a609-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="4a609-130">Modyfikowanie drzew XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4a609-130">Modifying XML Trees (LINQ to XML) (C#)</span></span>](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
