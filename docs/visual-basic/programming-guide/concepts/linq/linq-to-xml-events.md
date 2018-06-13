---
title: LINQ do XML zdarzenia (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: 216c2af87d2ae3a767548ccaa1efe118215cc6a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645993"
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="3f38e-102">LINQ do XML zdarzenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f38e-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="3f38e-103"> zdarzenia umożliwiają powiadomienia, gdy zostanie zmieniona drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="3f38e-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="3f38e-104">Zdarzenia można dodawać do wystąpienia dowolnego <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="3f38e-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="3f38e-105">Program obsługi zdarzeń Zadzwonimy zdarzenia dla zmian w tym <xref:System.Xml.Linq.XObject> i wszystkie jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f38e-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="3f38e-106">Można na przykład, Dodaj program obsługi zdarzeń do katalogu głównego drzewa i obsługiwać wszystkie modyfikacje w drzewie z tej obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3f38e-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="3f38e-107">Przykłady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zdarzenia, zobacz <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed>.</span><span class="sxs-lookup"><span data-stu-id="3f38e-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="3f38e-108">Typy i zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3f38e-108">Types and Events</span></span>  
 <span data-ttu-id="3f38e-109">Podczas pracy ze zdarzeniami, można użyć następujących typów:</span><span class="sxs-lookup"><span data-stu-id="3f38e-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="3f38e-110">Typ</span><span class="sxs-lookup"><span data-stu-id="3f38e-110">Type</span></span>|<span data-ttu-id="3f38e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3f38e-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="3f38e-112">Określa typ zdarzenia, gdy zdarzenie jest wywoływane dla <xref:System.Xml.Linq.XObject>.</span><span class="sxs-lookup"><span data-stu-id="3f38e-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="3f38e-113">Udostępnia dane dla <xref:System.Xml.Linq.XObject.Changing> i <xref:System.Xml.Linq.XObject.Changed> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3f38e-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="3f38e-114">Następujące zdarzenia są generowane po zmodyfikowaniu drzewo XML:</span><span class="sxs-lookup"><span data-stu-id="3f38e-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="3f38e-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="3f38e-115">Event</span></span>|<span data-ttu-id="3f38e-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3f38e-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="3f38e-117">Występuje bezpośrednio przed tym <xref:System.Xml.Linq.XObject> lub dowolnego z jego węzłów podrzędnych ma zmienić.</span><span class="sxs-lookup"><span data-stu-id="3f38e-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="3f38e-118">Występuje, gdy <xref:System.Xml.Linq.XObject> został zmieniony lub dowolną z jego elementy podrzędne zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="3f38e-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3f38e-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f38e-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="3f38e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3f38e-120">Description</span></span>  
 <span data-ttu-id="3f38e-121">Zdarzenia są przydatne, jeśli chcesz zachować niektóre agregują informacje w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="3f38e-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="3f38e-122">Można na przykład obsługa Suma faktury, który jest sumą pozycje, faktury.</span><span class="sxs-lookup"><span data-stu-id="3f38e-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="3f38e-123">W tym przykładzie użyto zdarzeń, aby zachować Suma wszystkich elementów podrzędnych w elemencie złożonych `Items`.</span><span class="sxs-lookup"><span data-stu-id="3f38e-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3f38e-124">Kod</span><span class="sxs-lookup"><span data-stu-id="3f38e-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="3f38e-125">Komentarze</span><span class="sxs-lookup"><span data-stu-id="3f38e-125">Comments</span></span>  
 <span data-ttu-id="3f38e-126">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3f38e-126">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f38e-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f38e-127">See Also</span></span>  
 [<span data-ttu-id="3f38e-128">Zaawansowane LINQ do XML programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f38e-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
