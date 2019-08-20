---
title: Obsługa par nazwa-wartość (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 9c42a154a4c3ed1463e428faab4c7d33197ef4a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591702"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="c3139-102">Obsługa par nazwa/wartość (C#)</span><span class="sxs-lookup"><span data-stu-id="c3139-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="c3139-103">Wiele aplikacji musi utrzymywać informacje, które najlepiej są przechowywane jako pary nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="c3139-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="c3139-104">Te informacje mogą dotyczyć informacji konfiguracyjnych lub ustawień globalnych.</span><span class="sxs-lookup"><span data-stu-id="c3139-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c3139-105">zawiera kilka metod, które ułatwiają przechowywanie zestawu par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="c3139-105">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="c3139-106">Możesz zachować informacje jako atrybuty lub jako zestaw elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c3139-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="c3139-107">Jedną z różnic między przechowywaniem informacji jako atrybuty lub jako elementami podrzędnymi jest to, że atrybuty mogą mieć tylko jeden atrybut z określoną nazwą dla elementu.</span><span class="sxs-lookup"><span data-stu-id="c3139-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="c3139-108">To ograniczenie nie ma zastosowania do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c3139-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="c3139-109">SetAttributeValue i SetElementValue</span><span class="sxs-lookup"><span data-stu-id="c3139-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="c3139-110">Dwie metody, które ułatwiają utrzymywanie par <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwa/wartość, i. <xref:System.Xml.Linq.XElement.SetElementValue%2A></span><span class="sxs-lookup"><span data-stu-id="c3139-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="c3139-111">Te dwie metody mają podobną semantykę.</span><span class="sxs-lookup"><span data-stu-id="c3139-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="c3139-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>może dodawać, modyfikować lub usuwać atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="c3139-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="c3139-113">Jeśli wywoływana <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> jest nazwa atrybutu, który nie istnieje, metoda tworzy nowy atrybut i dodaje go do określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="c3139-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="c3139-114">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i z określoną zawartością, zawartość atrybutu zostanie zastąpiona określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="c3139-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="c3139-115">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i określisz wartość null dla zawartości, atrybut zostanie usunięty z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c3139-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="c3139-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>może dodawać, modyfikować lub usuwać elementy podrzędne elementu.</span><span class="sxs-lookup"><span data-stu-id="c3139-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="c3139-117">W przypadku wywołania <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą elementu podrzędnego, który nie istnieje, metoda tworzy nowy element i dodaje go do określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="c3139-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="c3139-118">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i z określoną zawartością, zawartość elementu zostanie zastąpiona określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="c3139-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="c3139-119">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i określisz wartość null dla zawartości, element zostanie usunięty z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c3139-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3139-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3139-120">Example</span></span>  
 <span data-ttu-id="c3139-121">Poniższy przykład tworzy element bez atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c3139-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="c3139-122">Następnie używa <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> metody, aby utworzyć i zachować listę par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="c3139-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="c3139-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c3139-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="c3139-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3139-124">Example</span></span>  
 <span data-ttu-id="c3139-125">Poniższy przykład tworzy element bez elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c3139-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="c3139-126">Następnie używa <xref:System.Xml.Linq.XElement.SetElementValue%2A> metody, aby utworzyć i zachować listę par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="c3139-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
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
  
 <span data-ttu-id="c3139-127">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c3139-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3139-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3139-128">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="c3139-129">Modyfikowanie drzew XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c3139-129">Modifying XML Trees (LINQ to XML) (C#)</span></span>](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
