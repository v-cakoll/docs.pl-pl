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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)

W tym przykładzie dołącza program obsługi do zdarzenia asynchroniczne obsługi usługi sieci Web, dzięki czemu można pobrać wynik wywołania metody asynchroniczne. W tym przykładzie użyto usługi sieci `http://www.xmethods.net`Web Usługi DemoTemperature w .

Podczas odwoływania się do usługi sieci Web w projekcie w programie Visual `My.WebServices` Studio Integrated Development Environment (IDE) jest ona dodawana do obiektu, a IDE generuje klasę serwera proxy klienta w celu uzyskania dostępu do określonej usługi sieci Web

Klasa serwera proxy umożliwia synchronicznie wywoływanie metod usługi sieci Web, gdzie aplikacja czeka na zakończenie funkcji. Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby ułatwić wywołanie metody asynchronicznie. Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*serwer proxy tworzy podprocedura *NameOfWebServiceFunction,* `Async` zdarzenie *NameOfWebServiceFunction* `Completed` i klasę *NameOfWebServiceFunction.* `CompletedEventArgs` W tym przykładzie pokazano, jak używać asynchronicznych elementów członkowskich, aby uzyskać dostęp do `getTemp` funkcji usługi sieci Web DemoTemperatureService.

> [!NOTE]
> Ten kod nie działa w aplikacjach sieci Web, `My.WebServices` ponieważ ASP.NET nie obsługuje obiektu.

## <a name="call-a-web-service-asynchronously"></a>Wywoływanie usługi sieci Web asynchronicznie

1. Odwołanie się do usługi sieci Web `http://www.xmethods.net`Usługi DemoTemperature w . Adres jest

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Dodaj program obsługi `getTempCompleted` zdarzeń dla zdarzenia:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Nie można `Handles` użyć instrukcji do skojarzenia `My.WebServices` programu obsługi zdarzeń ze zdarzeniami obiektu.

3. Dodaj pole do śledzenia, jeśli program obsługi `getTempCompleted` zdarzeń został dodany do zdarzenia:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Dodaj metodę, aby dodać program `getTempCompleted` obsługi zdarzeń do zdarzenia, `getTempAsync` jeśli to konieczne, i wywołać metodę:

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

    Aby wywołać `getTemp` metodę sieci Web asynchronicznie, należy wywołać `CallGetTempAsync` metodę. Po zakończeniu metody sieci Web, jego zwracana wartość jest przekazywana do programu obsługi `getTempCompletedHandler` zdarzeń.

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do usług sieci Web aplikacji](accessing-application-web-services.md)
- [My.WebServices, obiekt](../../language-reference/objects/my-webservices-object.md)
