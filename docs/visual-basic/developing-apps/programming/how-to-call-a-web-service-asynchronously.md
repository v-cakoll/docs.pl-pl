---
title: 'Porady: asynchroniczne wywoływanie usługi sieci Web'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: d288cc1f2991a8f504dc9f1b206bba76fa378b75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76794563"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="c86b9-102">Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c86b9-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="c86b9-103">W tym przykładzie dołącza program obsługi do zdarzenia asynchroniczne obsługi usługi sieci Web, dzięki czemu można pobrać wynik wywołania metody asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="c86b9-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="c86b9-104">W tym przykładzie użyto usługi sieci `http://www.xmethods.net`Web Usługi DemoTemperature w .</span><span class="sxs-lookup"><span data-stu-id="c86b9-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="c86b9-105">Podczas odwoływania się do usługi sieci Web w projekcie w programie Visual `My.WebServices` Studio Integrated Development Environment (IDE) jest ona dodawana do obiektu, a IDE generuje klasę serwera proxy klienta w celu uzyskania dostępu do określonej usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="c86b9-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="c86b9-106">Klasa serwera proxy umożliwia synchronicznie wywoływanie metod usługi sieci Web, gdzie aplikacja czeka na zakończenie funkcji.</span><span class="sxs-lookup"><span data-stu-id="c86b9-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="c86b9-107">Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby ułatwić wywołanie metody asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="c86b9-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="c86b9-108">Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*serwer proxy tworzy podprocedura *NameOfWebServiceFunction,* `Async` zdarzenie *NameOfWebServiceFunction* `Completed` i klasę *NameOfWebServiceFunction.* `CompletedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="c86b9-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="c86b9-109">W tym przykładzie pokazano, jak używać asynchronicznych elementów członkowskich, aby uzyskać dostęp do `getTemp` funkcji usługi sieci Web DemoTemperatureService.</span><span class="sxs-lookup"><span data-stu-id="c86b9-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="c86b9-110">Ten kod nie działa w aplikacjach sieci Web, `My.WebServices` ponieważ ASP.NET nie obsługuje obiektu.</span><span class="sxs-lookup"><span data-stu-id="c86b9-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="c86b9-111">Wywoływanie usługi sieci Web asynchronicznie</span><span class="sxs-lookup"><span data-stu-id="c86b9-111">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="c86b9-112">Odwołanie się do usługi sieci Web `http://www.xmethods.net`Usługi DemoTemperature w .</span><span class="sxs-lookup"><span data-stu-id="c86b9-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="c86b9-113">Adres jest</span><span class="sxs-lookup"><span data-stu-id="c86b9-113">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="c86b9-114">Dodaj program obsługi `getTempCompleted` zdarzeń dla zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="c86b9-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="c86b9-115">Nie można `Handles` użyć instrukcji do skojarzenia `My.WebServices` programu obsługi zdarzeń ze zdarzeniami obiektu.</span><span class="sxs-lookup"><span data-stu-id="c86b9-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="c86b9-116">Dodaj pole do śledzenia, jeśli program obsługi `getTempCompleted` zdarzeń został dodany do zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="c86b9-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="c86b9-117">Dodaj metodę, aby dodać program `getTempCompleted` obsługi zdarzeń do zdarzenia, `getTempAsync` jeśli to konieczne, i wywołać metodę:</span><span class="sxs-lookup"><span data-stu-id="c86b9-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

    ```vb
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

    <span data-ttu-id="c86b9-118">Aby wywołać `getTemp` metodę sieci Web asynchronicznie, należy wywołać `CallGetTempAsync` metodę.</span><span class="sxs-lookup"><span data-stu-id="c86b9-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="c86b9-119">Po zakończeniu metody sieci Web, jego zwracana wartość jest przekazywana do programu obsługi `getTempCompletedHandler` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c86b9-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="c86b9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c86b9-120">See also</span></span>

- [<span data-ttu-id="c86b9-121">Uzyskiwanie dostępu do usług sieci Web aplikacji</span><span class="sxs-lookup"><span data-stu-id="c86b9-121">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="c86b9-122">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="c86b9-122">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
