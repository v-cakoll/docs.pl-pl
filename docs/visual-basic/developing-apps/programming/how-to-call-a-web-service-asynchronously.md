---
title: 'Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c7a9666141accdcc0b1346de7b0c2903c7cc86df
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="b9a23-102">Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9a23-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>
<span data-ttu-id="b9a23-103">W tym przykładzie dołącza program obsługi do Zdarzenie asynchroniczne obsługi usługi sieci Web, dzięki czemu można pobrać wyniku asynchroniczne wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="b9a23-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="b9a23-104">W tym przykładzie użyto usługi sieci DemoTemperatureService Web na http://www.xmethods.net.</span><span class="sxs-lookup"><span data-stu-id="b9a23-104">This example used the DemoTemperatureService Web service at http://www.xmethods.net.</span></span>  
  
 <span data-ttu-id="b9a23-105">Usługi sieci Web w przypadku odwołania do projektu w programie Visual Studio programowanie środowiska IDE (Integrated), jest ona dodawana do `My.WebServices` obiekt i IDE generuje klasy serwera proxy klienta do dostępu do określonej usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="b9a23-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>  
  
 <span data-ttu-id="b9a23-106">Klasy serwera proxy można wywołać metody usługi sieci Web synchronicznie, gdy aplikacja oczekuje na funkcja do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b9a23-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="b9a23-107">Ponadto serwer proxy tworzy dodatkowych członków, aby wywołać metodę asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="b9a23-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="b9a23-108">Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, tworzy serwer proxy *NameOfWebServiceFunction* `Async` podprocedury, *NameOfWebServiceFunction* `Completed` zdarzeń, a *NameOfWebServiceFunction* `CompletedEventArgs` klasy.</span><span class="sxs-lookup"><span data-stu-id="b9a23-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="b9a23-109">W tym przykładzie pokazano, jak uzyskiwać dostęp do członków asynchroniczne `getTemp` funkcji usługi sieci DemoTemperatureService Web.</span><span class="sxs-lookup"><span data-stu-id="b9a23-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9a23-110">Ten kod nie działa w aplikacji sieci Web, ponieważ nie obsługuje platformy ASP.NET `My.WebServices` obiektu.</span><span class="sxs-lookup"><span data-stu-id="b9a23-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>  
  
### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="b9a23-111">Aby asynchroniczne wywoływanie usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="b9a23-111">To call a Web service asynchronously</span></span>  
  
1.  <span data-ttu-id="b9a23-112">Odwołanie do usługi sieci DemoTemperatureService Web na http://www.xmethods.net.</span><span class="sxs-lookup"><span data-stu-id="b9a23-112">Reference the DemoTemperatureService Web service at http://www.xmethods.net.</span></span> <span data-ttu-id="b9a23-113">Adres jest</span><span class="sxs-lookup"><span data-stu-id="b9a23-113">The address is</span></span>  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  <span data-ttu-id="b9a23-114">Dodaj program obsługi zdarzeń dla `getTempCompleted` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="b9a23-114">Add an event handler for the `getTempCompleted` event:</span></span>  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="b9a23-115">Nie można użyć `Handles` instrukcji do skojarzenia z obsługi zdarzeń `My.WebServices` zdarzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="b9a23-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>  
  
3.  <span data-ttu-id="b9a23-116">Dodawanie pola do śledzenia, jeśli program obsługi zdarzeń został dodany do `getTempCompleted` zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="b9a23-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  <span data-ttu-id="b9a23-117">Dodaj metodę Dodaj program obsługi zdarzeń do `getTempCompleted` zdarzeń, jeśli to konieczne oraz wywołanie `getTempAsynch` metody:</span><span class="sxs-lookup"><span data-stu-id="b9a23-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsynch` method:</span></span>  
  
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
  
     <span data-ttu-id="b9a23-118">Aby wywołać `getTemp` sieci Web metody asynchronicznie, wywołaj `CallGetTempAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="b9a23-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="b9a23-119">Po zakończeniu działania metody sieci Web, jego wartości zwracanej są przekazywane do `getTempCompletedHandler` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b9a23-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a23-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9a23-120">See Also</span></span>  
 [<span data-ttu-id="b9a23-121">Uzyskiwanie dostępu do usług sieci Web aplikacji</span><span class="sxs-lookup"><span data-stu-id="b9a23-121">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [<span data-ttu-id="b9a23-122">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="b9a23-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
