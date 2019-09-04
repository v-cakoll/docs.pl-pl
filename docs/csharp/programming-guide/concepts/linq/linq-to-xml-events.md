---
title: Zdarzenia LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253174"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="2421d-102">Zdarzenia LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2421d-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2421d-103">zdarzenia umożliwiają otrzymywanie powiadomień, gdy drzewo XML zostanie zmienione.</span><span class="sxs-lookup"><span data-stu-id="2421d-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="2421d-104">Zdarzenia można dodać do wystąpienia dowolnego <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="2421d-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="2421d-105">Procedura obsługi zdarzeń będzie następnie otrzymywać zdarzenia dotyczące modyfikacji tego <xref:System.Xml.Linq.XObject> elementu i jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2421d-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="2421d-106">Na przykład można dodać program obsługi zdarzeń do elementu głównego drzewa i obsłużyć wszystkie modyfikacje drzewa z tego programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2421d-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="2421d-107">Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzeń można znaleźć w tematach <xref:System.Xml.Linq.XObject.Changed> <xref:System.Xml.Linq.XObject.Changing> i.</span><span class="sxs-lookup"><span data-stu-id="2421d-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="2421d-108">Typy i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2421d-108">Types and Events</span></span>  
 <span data-ttu-id="2421d-109">Następujące typy są używane podczas pracy ze zdarzeniami:</span><span class="sxs-lookup"><span data-stu-id="2421d-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="2421d-110">Typ</span><span class="sxs-lookup"><span data-stu-id="2421d-110">Type</span></span>|<span data-ttu-id="2421d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2421d-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="2421d-112">Określa typ zdarzenia, gdy zdarzenie jest zgłaszane dla elementu <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="2421d-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="2421d-113">Dostarcza dane dla <xref:System.Xml.Linq.XObject.Changing> zdarzeń i <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="2421d-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="2421d-114">Podczas modyfikowania drzewa XML są zgłaszane następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="2421d-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="2421d-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="2421d-115">Event</span></span>|<span data-ttu-id="2421d-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2421d-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="2421d-117">Występuje tuż przed tym <xref:System.Xml.Linq.XObject> lub dowolnym z jego obiektów podrzędnych zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="2421d-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="2421d-118">Występuje po <xref:System.Xml.Linq.XObject> zmianie lub dowolnych jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2421d-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2421d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="2421d-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2421d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2421d-120">Description</span></span>  
 <span data-ttu-id="2421d-121">Zdarzenia są przydatne, gdy chcesz zachować pewne zagregowane informacje w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="2421d-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="2421d-122">Na przykład możesz chcieć zachować sumę faktury, która jest sumą wierszy faktury.</span><span class="sxs-lookup"><span data-stu-id="2421d-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="2421d-123">Ten przykład używa zdarzeń, aby zachować sumę wszystkich elementów podrzędnych w ramach elementu `Items`złożonego.</span><span class="sxs-lookup"><span data-stu-id="2421d-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2421d-124">Kod</span><span class="sxs-lookup"><span data-stu-id="2421d-124">Code</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="2421d-125">Komentarze</span><span class="sxs-lookup"><span data-stu-id="2421d-125">Comments</span></span>  
 <span data-ttu-id="2421d-126">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2421d-126">This code produces the following output:</span></span>  
  
```output  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  