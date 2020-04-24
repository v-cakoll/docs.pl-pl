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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="5aacf-102">Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aacf-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="5aacf-103">Ten przykład dołącza procedurę obsługi do zdarzenia asynchronicznej procedury obsługi usługi sieci Web, aby można było pobrać wynik wywołania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="5aacf-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="5aacf-104">W tym przykładzie użyto usługi sieci Web DemoTemperatureService `http://www.xmethods.net`pod adresem.</span><span class="sxs-lookup"><span data-stu-id="5aacf-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="5aacf-105">Gdy odwołujesz się do usługi sieci Web w projekcie w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, zostanie `My.WebServices` ona dodana do obiektu, a IDE generuje klasę proxy klienta, aby uzyskać dostęp do określonej usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="5aacf-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="5aacf-106">Klasa proxy umożliwia synchroniczną wywoływanie metod usługi sieci Web, w których aplikacja czeka na zakończenie działania.</span><span class="sxs-lookup"><span data-stu-id="5aacf-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="5aacf-107">Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby pomóc w asynchronicznym wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="5aacf-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="5aacf-108">Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, serwer proxy tworzy podprocedurę *NameOfWebServiceFunction* `Async` , zdarzenie *NameOfWebServiceFunction* `Completed` i klasę *NameOfWebServiceFunction* `CompletedEventArgs` .</span><span class="sxs-lookup"><span data-stu-id="5aacf-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="5aacf-109">Ten przykład ilustruje sposób używania asynchronicznych elementów członkowskich do uzyskiwania dostępu `getTemp` do funkcji usługi sieci Web DemoTemperatureService.</span><span class="sxs-lookup"><span data-stu-id="5aacf-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="5aacf-110">Ten kod nie działa w aplikacjach sieci Web, ponieważ ASP.NET nie obsługuje tego `My.WebServices` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5aacf-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="5aacf-111">Asynchroniczne wywoływanie usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="5aacf-111">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="5aacf-112">Odwołuje się do usługi sieci `http://www.xmethods.net`Web DemoTemperatureService.</span><span class="sxs-lookup"><span data-stu-id="5aacf-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="5aacf-113">Adres to</span><span class="sxs-lookup"><span data-stu-id="5aacf-113">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="5aacf-114">Dodaj program obsługi zdarzeń dla `getTempCompleted` zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="5aacf-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="5aacf-115">Nie można użyć `Handles` instrukcji, aby skojarzyć procedurę obsługi zdarzeń ze zdarzeniami `My.WebServices` obiektu.</span><span class="sxs-lookup"><span data-stu-id="5aacf-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="5aacf-116">Dodaj pole do śledzenia, jeśli program obsługi zdarzeń został dodany do `getTempCompleted` zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="5aacf-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="5aacf-117">Dodaj metodę, aby dodać procedurę obsługi zdarzeń do `getTempCompleted` zdarzenia, w razie potrzeby i wywołać `getTempAsync` metodę:</span><span class="sxs-lookup"><span data-stu-id="5aacf-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="5aacf-118">Aby wywołać metodę `getTemp` sieci Web asynchronicznie, wywołaj `CallGetTempAsync` metodę.</span><span class="sxs-lookup"><span data-stu-id="5aacf-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="5aacf-119">Po zakończeniu metody sieci Web jej wartość zwracana jest przenoszona do procedury `getTempCompletedHandler` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5aacf-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="5aacf-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5aacf-120">See also</span></span>

- [<span data-ttu-id="5aacf-121">Uzyskiwanie dostępu do usług sieci Web aplikacji</span><span class="sxs-lookup"><span data-stu-id="5aacf-121">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="5aacf-122">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="5aacf-122">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
