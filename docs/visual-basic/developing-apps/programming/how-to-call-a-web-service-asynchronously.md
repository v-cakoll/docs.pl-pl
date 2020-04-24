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

Ten przykład dołącza procedurę obsługi do zdarzenia asynchronicznej procedury obsługi usługi sieci Web, aby można było pobrać wynik wywołania metody asynchronicznej. W tym przykładzie użyto usługi sieci Web DemoTemperatureService `http://www.xmethods.net`pod adresem.

Gdy odwołujesz się do usługi sieci Web w projekcie w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, zostanie `My.WebServices` ona dodana do obiektu, a IDE generuje klasę proxy klienta, aby uzyskać dostęp do określonej usługi sieci Web

Klasa proxy umożliwia synchroniczną wywoływanie metod usługi sieci Web, w których aplikacja czeka na zakończenie działania. Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby pomóc w asynchronicznym wywołaniu metody. Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, serwer proxy tworzy podprocedurę *NameOfWebServiceFunction* `Async` , zdarzenie *NameOfWebServiceFunction* `Completed` i klasę *NameOfWebServiceFunction* `CompletedEventArgs` . Ten przykład ilustruje sposób używania asynchronicznych elementów członkowskich do uzyskiwania dostępu `getTemp` do funkcji usługi sieci Web DemoTemperatureService.

> [!NOTE]
> Ten kod nie działa w aplikacjach sieci Web, ponieważ ASP.NET nie obsługuje tego `My.WebServices` obiektu.

## <a name="call-a-web-service-asynchronously"></a>Asynchroniczne wywoływanie usługi sieci Web

1. Odwołuje się do usługi sieci `http://www.xmethods.net`Web DemoTemperatureService. Adres to

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Dodaj program obsługi zdarzeń dla `getTempCompleted` zdarzenia:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Nie można użyć `Handles` instrukcji, aby skojarzyć procedurę obsługi zdarzeń ze zdarzeniami `My.WebServices` obiektu.

3. Dodaj pole do śledzenia, jeśli program obsługi zdarzeń został dodany do `getTempCompleted` zdarzenia:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Dodaj metodę, aby dodać procedurę obsługi zdarzeń do `getTempCompleted` zdarzenia, w razie potrzeby i wywołać `getTempAsync` metodę:

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

    Aby wywołać metodę `getTemp` sieci Web asynchronicznie, wywołaj `CallGetTempAsync` metodę. Po zakończeniu metody sieci Web jej wartość zwracana jest przenoszona do procedury `getTempCompletedHandler` obsługi zdarzeń.

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do usług sieci Web aplikacji](accessing-application-web-services.md)
- [My.WebServices, obiekt](../../language-reference/objects/my-webservices-object.md)
