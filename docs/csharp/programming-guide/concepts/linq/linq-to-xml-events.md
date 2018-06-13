---
title: LINQ do XML zdarzeń (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 3dd4eaa0261ae7d878e188572d260b34b64fc031
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322396"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="6c255-102">LINQ do XML zdarzeń (C#)</span><span class="sxs-lookup"><span data-stu-id="6c255-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6c255-103"> zdarzenia umożliwiają powiadomienia, gdy zostanie zmieniona drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="6c255-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="6c255-104">Zdarzenia można dodawać do wystąpienia dowolnego <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="6c255-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="6c255-105">Program obsługi zdarzeń Zadzwonimy zdarzenia dla zmian w tym <xref:System.Xml.Linq.XObject> i wszystkie jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="6c255-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="6c255-106">Można na przykład, Dodaj program obsługi zdarzeń do katalogu głównego drzewa i obsługiwać wszystkie modyfikacje w drzewie z tej obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6c255-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="6c255-107">Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzenia, zobacz <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="6c255-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="6c255-108">Typy i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6c255-108">Types and Events</span></span>  
 <span data-ttu-id="6c255-109">Podczas pracy ze zdarzeniami, można użyć następujących typów:</span><span class="sxs-lookup"><span data-stu-id="6c255-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="6c255-110">Typ</span><span class="sxs-lookup"><span data-stu-id="6c255-110">Type</span></span>|<span data-ttu-id="6c255-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6c255-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="6c255-112">Określa typ zdarzenia, gdy zdarzenie jest wywoływane dla <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="6c255-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="6c255-113">Udostępnia dane dla <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6c255-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="6c255-114">Następujące zdarzenia są generowane po zmodyfikowaniu drzewo XML:</span><span class="sxs-lookup"><span data-stu-id="6c255-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="6c255-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="6c255-115">Event</span></span>|<span data-ttu-id="6c255-116">Opis</span><span class="sxs-lookup"><span data-stu-id="6c255-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="6c255-117">Występuje bezpośrednio przed tym <xref:System.Xml.Linq.XObject> lub dowolnego z jego węzłów podrzędnych ma zmienić.</span><span class="sxs-lookup"><span data-stu-id="6c255-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="6c255-118">Występuje, gdy <xref:System.Xml.Linq.XObject> został zmieniony lub dowolną z jego elementy podrzędne zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="6c255-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6c255-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c255-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6c255-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6c255-120">Description</span></span>  
 <span data-ttu-id="6c255-121">Zdarzenia są przydatne, jeśli chcesz zachować niektóre agregują informacje w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="6c255-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="6c255-122">Można na przykład obsługa Suma faktury, który jest sumą pozycje, faktury.</span><span class="sxs-lookup"><span data-stu-id="6c255-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="6c255-123">W tym przykładzie użyto zdarzeń, aby zachować Suma wszystkich elementów podrzędnych w elemencie złożonych `Items`.</span><span class="sxs-lookup"><span data-stu-id="6c255-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6c255-124">Kod</span><span class="sxs-lookup"><span data-stu-id="6c255-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="6c255-125">Komentarze</span><span class="sxs-lookup"><span data-stu-id="6c255-125">Comments</span></span>  
 <span data-ttu-id="6c255-126">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6c255-126">This code produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="6c255-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c255-127">See Also</span></span>  
 [<span data-ttu-id="6c255-128">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="6c255-128">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
