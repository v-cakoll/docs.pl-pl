---
title: LINQ do zdarzeń XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253174"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="a406a-102">LINQ do zdarzeń XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a406a-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a406a-103">zdarzenia umożliwiają powiadamianie o zmianie drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="a406a-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="a406a-104">Zdarzenia można dodać do wystąpienia <xref:System.Xml.Linq.XObject>dowolnego pliku .</span><span class="sxs-lookup"><span data-stu-id="a406a-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="a406a-105">Program obsługi zdarzeń otrzyma zdarzenia dla <xref:System.Xml.Linq.XObject> modyfikacji tego i dowolnego z jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a406a-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="a406a-106">Na przykład można dodać program obsługi zdarzeń do katalogu głównego drzewa i obsługiwać wszystkie modyfikacje do drzewa z tego programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a406a-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="a406a-107">Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzeń można <xref:System.Xml.Linq.XObject.Changing> znaleźć <xref:System.Xml.Linq.XObject.Changed>w części I .</span><span class="sxs-lookup"><span data-stu-id="a406a-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="a406a-108">Typy i wydarzenia</span><span class="sxs-lookup"><span data-stu-id="a406a-108">Types and Events</span></span>  
 <span data-ttu-id="a406a-109">Podczas pracy ze zdarzeniami należy używać następujących typów:</span><span class="sxs-lookup"><span data-stu-id="a406a-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="a406a-110">Typ</span><span class="sxs-lookup"><span data-stu-id="a406a-110">Type</span></span>|<span data-ttu-id="a406a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a406a-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="a406a-112">Określa typ zdarzenia, gdy zdarzenie jest <xref:System.Xml.Linq.XObject>wywoływane dla pliku .</span><span class="sxs-lookup"><span data-stu-id="a406a-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="a406a-113">Zawiera dane <xref:System.Xml.Linq.XObject.Changing> dla <xref:System.Xml.Linq.XObject.Changed> i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a406a-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="a406a-114">Podczas modyfikowania drzewa XML są wywoływane następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a406a-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="a406a-115">Wydarzenie</span><span class="sxs-lookup"><span data-stu-id="a406a-115">Event</span></span>|<span data-ttu-id="a406a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a406a-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="a406a-117">Występuje tuż <xref:System.Xml.Linq.XObject> przed tym lub którykolwiek z jego elementów podrzędnych będzie się zmieniać.</span><span class="sxs-lookup"><span data-stu-id="a406a-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="a406a-118">Występuje, <xref:System.Xml.Linq.XObject> gdy zmienił się lub którykolwiek z jego elementów podrzędnych uległ zmianie.</span><span class="sxs-lookup"><span data-stu-id="a406a-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a406a-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a406a-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a406a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a406a-120">Description</span></span>  
 <span data-ttu-id="a406a-121">Zdarzenia są przydatne, gdy chcesz zachować pewne informacje zagregowane w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="a406a-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="a406a-122">Na przykład można zachować sumę faktury, która jest sumą pozycji faktury.</span><span class="sxs-lookup"><span data-stu-id="a406a-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="a406a-123">W tym przykładzie użyto zdarzeń do utrzymania sumy `Items`wszystkich elementów podrzędnych w elemencie złożonym .</span><span class="sxs-lookup"><span data-stu-id="a406a-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a406a-124">Code</span><span class="sxs-lookup"><span data-stu-id="a406a-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="a406a-125">Komentarze</span><span class="sxs-lookup"><span data-stu-id="a406a-125">Comments</span></span>  
 <span data-ttu-id="a406a-126">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a406a-126">This code produces the following output:</span></span>  
  
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
  