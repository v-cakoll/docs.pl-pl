---
title: Zdarzenia LINQ to XML
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: d00f6f1b2a14ac73c1bcd4a1f74b9714ca304da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368819"
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="0b61a-102">Zdarzenia LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b61a-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0b61a-103">zdarzenia umożliwiają otrzymywanie powiadomień, gdy drzewo XML zostanie zmienione.</span><span class="sxs-lookup"><span data-stu-id="0b61a-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="0b61a-104">Zdarzenia można dodać do wystąpienia dowolnego <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="0b61a-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="0b61a-105">Procedura obsługi zdarzeń będzie następnie otrzymywać zdarzenia dotyczące modyfikacji tego <xref:System.Xml.Linq.XObject> elementu i jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0b61a-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="0b61a-106">Na przykład można dodać program obsługi zdarzeń do elementu głównego drzewa i obsłużyć wszystkie modyfikacje drzewa z tego programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0b61a-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="0b61a-107">Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzeń można znaleźć w tematach <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="0b61a-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="0b61a-108">Typy i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0b61a-108">Types and Events</span></span>  
 <span data-ttu-id="0b61a-109">Następujące typy są używane podczas pracy ze zdarzeniami:</span><span class="sxs-lookup"><span data-stu-id="0b61a-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="0b61a-110">Typ</span><span class="sxs-lookup"><span data-stu-id="0b61a-110">Type</span></span>|<span data-ttu-id="0b61a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0b61a-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="0b61a-112">Określa typ zdarzenia, gdy zdarzenie jest zgłaszane dla elementu <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="0b61a-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="0b61a-113">Dostarcza dane dla <xref:System.Xml.Linq.XObject.Changing> zdarzeń i <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="0b61a-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="0b61a-114">Podczas modyfikowania drzewa XML są zgłaszane następujące zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="0b61a-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="0b61a-115">Wydarzenie</span><span class="sxs-lookup"><span data-stu-id="0b61a-115">Event</span></span>|<span data-ttu-id="0b61a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="0b61a-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="0b61a-117">Występuje tuż przed tym <xref:System.Xml.Linq.XObject> lub dowolnym z jego obiektów podrzędnych zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="0b61a-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="0b61a-118">Występuje po <xref:System.Xml.Linq.XObject> zmianie lub dowolnych jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0b61a-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b61a-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b61a-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0b61a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0b61a-120">Description</span></span>  
 <span data-ttu-id="0b61a-121">Zdarzenia są przydatne, gdy chcesz zachować pewne zagregowane informacje w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="0b61a-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="0b61a-122">Na przykład możesz chcieć zachować sumę faktury, która jest sumą wierszy faktury.</span><span class="sxs-lookup"><span data-stu-id="0b61a-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="0b61a-123">Ten przykład używa zdarzeń, aby zachować sumę wszystkich elementów podrzędnych w ramach elementu złożonego `Items` .</span><span class="sxs-lookup"><span data-stu-id="0b61a-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0b61a-124">Kod</span><span class="sxs-lookup"><span data-stu-id="0b61a-124">Code</span></span>  
  
```vb  
Module Module1  
    Dim WithEvents items As XElement = Nothing  
    Dim total As XElement = Nothing  
    Dim root As XElement = _  
            <Root>  
                <Total>0</Total>  
                <Items></Items>  
            </Root>  
  
    Private Sub XObjectChanged( _  
            ByVal sender As Object, _  
            ByVal cea As XObjectChangeEventArgs) _  
            Handles items.Changed  
        Select Case cea.ObjectChange  
            Case XObjectChange.Add  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) + _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
            Case XObjectChange.Remove  
                If sender.GetType() Is GetType(XElement) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XElement)).Value))  
                End If  
                If sender.GetType() Is GetType(XText) Then  
                    total.Value = CStr(CInt(total.Value) - _  
                            CInt((DirectCast(sender, XText)).Value))  
                End If  
        End Select  
        Console.WriteLine("Changed {0} {1}", _  
                            sender.GetType().ToString(), _  
                            cea.ObjectChange.ToString())  
    End Sub  
  
    Sub Main()  
        total = root.<Total>(0)  
        items = root.<Items>(0)  
        items.SetElementValue("Item1", 25)  
        items.SetElementValue("Item2", 50)  
        items.SetElementValue("Item2", 75)  
        items.SetElementValue("Item3", 133)  
        items.SetElementValue("Item1", Nothing)  
        items.SetElementValue("Item4", 100)  
        Console.WriteLine("Total:{0}", CInt(total))  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="0b61a-125">Komentarze</span><span class="sxs-lookup"><span data-stu-id="0b61a-125">Comments</span></span>  
 <span data-ttu-id="0b61a-126">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0b61a-126">This code produces the following output:</span></span>  
  
```console  
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
  
## <a name="see-also"></a><span data-ttu-id="0b61a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b61a-127">See also</span></span>

- [<span data-ttu-id="0b61a-128">Zaawansowane programowanie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b61a-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
