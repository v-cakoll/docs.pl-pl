---
title: 'Instrukcje: Asynchroniczne wywoływanie usługi sieci Web (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 9127b0edce029f8b2944ddf692e85166ee8c89b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616150"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="457b7-102">Instrukcje: Asynchroniczne wywoływanie usługi sieci Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="457b7-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>
<span data-ttu-id="457b7-103">W tym przykładzie dołącza obsługę do zdarzenia asynchronicznej obsługi usługi sieci Web tak, aby możliwe było pobieranie wynik wywołania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="457b7-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="457b7-104">W tym przykładzie użyto usługi sieci DemoTemperatureService Web na `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="457b7-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>  
  
 <span data-ttu-id="457b7-105">Gdy odwołujesz usługi sieci Web w projekcie w Visual Studio rozwoju środowiska IDE (Integrated) jest dodawany do `My.WebServices` obiektu oraz środowiska IDE generuje klasę proxy klienta do dostępu do określonej usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="457b7-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>  
  
 <span data-ttu-id="457b7-106">Klasa proxy umożliwia wywołania metody usługi sieci Web synchronicznie, gdzie aplikacja czeka, aż funkcja do wykonania.</span><span class="sxs-lookup"><span data-stu-id="457b7-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="457b7-107">Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby pomóc asynchronicznie Wywołaj metodę.</span><span class="sxs-lookup"><span data-stu-id="457b7-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="457b7-108">Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, tworzy serwer proxy *NameOfWebServiceFunction* `Async` podprocedury, *NameOfWebServiceFunction* `Completed` zdarzeń, a *NameOfWebServiceFunction* `CompletedEventArgs` klasy.</span><span class="sxs-lookup"><span data-stu-id="457b7-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="457b7-109">W tym przykładzie przedstawiono sposób użycia asynchronicznych elementów członkowskich dostęp do `getTemp` funkcji usługi sieci DemoTemperatureService Web.</span><span class="sxs-lookup"><span data-stu-id="457b7-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="457b7-110">Ten kod nie działa w aplikacjach sieci Web, ponieważ nie obsługuje platformy ASP.NET `My.WebServices` obiektu.</span><span class="sxs-lookup"><span data-stu-id="457b7-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>  
  
### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="457b7-111">Aby asynchroniczne wywoływanie usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="457b7-111">To call a Web service asynchronously</span></span>  
  
1.  <span data-ttu-id="457b7-112">Odwoływać się do usługi sieci DemoTemperatureService Web na `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="457b7-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="457b7-113">Adres to</span><span class="sxs-lookup"><span data-stu-id="457b7-113">The address is</span></span>  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  <span data-ttu-id="457b7-114">Dodawanie obsługi zdarzeń dla `getTempCompleted` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="457b7-114">Add an event handler for the `getTempCompleted` event:</span></span>  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="457b7-115">Nie można użyć `Handles` instrukcję, aby skojarzyć program obsługi zdarzeń za pomocą `My.WebServices` zdarzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="457b7-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>  
  
3.  <span data-ttu-id="457b7-116">Dodaj pole do śledzenia, czy program obsługi zdarzeń została dodana do `getTempCompleted` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="457b7-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  <span data-ttu-id="457b7-117">Dodaj metodę, aby dodać program obsługi zdarzeń do `getTempCompleted` zdarzeń, jeśli to konieczne oraz wywołanie `getTempAsynch` metody:</span><span class="sxs-lookup"><span data-stu-id="457b7-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsynch` method:</span></span>  
  
    ```  
    Sub CallGetTempAsync(ByVal zipCode As Integer)  
        If Not handlerAttached Then  
            AddHandler My.WebServices.  
                TemperatureService.getTempCompleted,   
                AddressOf Me.TS_getTempCompleted  
            handlerAttached = True  
        End If  
        My.WebServices.TemperatureService.getTempAsync(zipCode)  
    End Sub  
    ```  
  
     <span data-ttu-id="457b7-118">Aby wywołać `getTemp` asynchronicznie metodę sieci Web, wywołaj `CallGetTempAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="457b7-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="457b7-119">Po zakończeniu metody sieci Web, jego wartość zwracana jest przekazywany do `getTempCompletedHandler` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="457b7-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457b7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="457b7-120">See also</span></span>
- [<span data-ttu-id="457b7-121">Uzyskiwanie dostępu do usług sieci Web aplikacji</span><span class="sxs-lookup"><span data-stu-id="457b7-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [<span data-ttu-id="457b7-122">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="457b7-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
