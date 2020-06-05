---
title: Obsługiwanie par nazwa-wartość
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: 1e30f010311dda393f65b1424e56f5b5ad014963
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389220"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a><span data-ttu-id="b035a-102">Obsługa par nazwa/wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b035a-102">Maintaining Name/Value Pairs (Visual Basic)</span></span>
<span data-ttu-id="b035a-103">Wiele aplikacji musi utrzymywać informacje, które najlepiej są przechowywane jako pary nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="b035a-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="b035a-104">Te informacje mogą dotyczyć informacji konfiguracyjnych lub ustawień globalnych.</span><span class="sxs-lookup"><span data-stu-id="b035a-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b035a-105">zawiera kilka metod, które ułatwiają przechowywanie zestawu par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="b035a-105">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="b035a-106">Możesz zachować informacje jako atrybuty lub jako zestaw elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b035a-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="b035a-107">Jedną z różnic między przechowywaniem informacji jako atrybuty lub jako elementami podrzędnymi jest to, że atrybuty mogą mieć tylko jeden atrybut z określoną nazwą dla elementu.</span><span class="sxs-lookup"><span data-stu-id="b035a-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="b035a-108">To ograniczenie nie ma zastosowania do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b035a-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="b035a-109">SetAttributeValue i SetElementValue</span><span class="sxs-lookup"><span data-stu-id="b035a-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="b035a-110">Dwie metody, które ułatwiają utrzymywanie par nazwa/wartość <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> , i <xref:System.Xml.Linq.XElement.SetElementValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="b035a-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="b035a-111">Te dwie metody mają podobną semantykę.</span><span class="sxs-lookup"><span data-stu-id="b035a-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="b035a-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A>może dodawać, modyfikować lub usuwać atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="b035a-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="b035a-113">Jeśli wywoływana jest <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwa atrybutu, który nie istnieje, metoda tworzy nowy atrybut i dodaje go do określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="b035a-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="b035a-114">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i z określoną zawartością, zawartość atrybutu zostanie zastąpiona określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="b035a-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="b035a-115">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> nazwę istniejącego atrybutu i określisz wartość null dla zawartości, atrybut zostanie usunięty z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b035a-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="b035a-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A>może dodawać, modyfikować lub usuwać elementy podrzędne elementu.</span><span class="sxs-lookup"><span data-stu-id="b035a-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="b035a-117">W przypadku wywołania <xref:System.Xml.Linq.XElement.SetElementValue%2A> z nazwą elementu podrzędnego, który nie istnieje, metoda tworzy nowy element i dodaje go do określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="b035a-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="b035a-118">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i z określoną zawartością, zawartość elementu zostanie zastąpiona określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="b035a-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="b035a-119">Jeśli wywołasz <xref:System.Xml.Linq.XElement.SetElementValue%2A> nazwę istniejącego elementu i określisz wartość null dla zawartości, element zostanie usunięty z jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b035a-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b035a-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="b035a-120">Example</span></span>  
 <span data-ttu-id="b035a-121">Poniższy przykład tworzy element bez atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b035a-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="b035a-122">Następnie używa metody, <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> Aby utworzyć i zachować listę par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="b035a-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="b035a-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b035a-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="b035a-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="b035a-124">Example</span></span>  
 <span data-ttu-id="b035a-125">Poniższy przykład tworzy element bez elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b035a-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="b035a-126">Następnie używa metody, <xref:System.Xml.Linq.XElement.SetElementValue%2A> Aby utworzyć i zachować listę par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="b035a-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="b035a-127">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b035a-127">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b035a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b035a-128">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="b035a-129">Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b035a-129">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
