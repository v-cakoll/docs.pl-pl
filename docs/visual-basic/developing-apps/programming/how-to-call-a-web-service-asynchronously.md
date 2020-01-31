---
title: 'Porady: asynchroniczne wywoływanie usługi sieci Web'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: d288cc1f2991a8f504dc9f1b206bba76fa378b75
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794563"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)

Ten przykład dołącza procedurę obsługi do zdarzenia asynchronicznej procedury obsługi usługi sieci Web, aby można było pobrać wynik wywołania metody asynchronicznej. W tym przykładzie użyto usługi sieci Web DemoTemperatureService w `http://www.xmethods.net`.

Gdy odwołujesz się do usługi sieci Web w projekcie w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, jest on dodawany do obiektu `My.WebServices`, a IDE generuje klasę proxy klienta w celu uzyskania dostępu do określonej usługi sieci Web

Klasa proxy umożliwia synchroniczną wywoływanie metod usługi sieci Web, w których aplikacja czeka na zakończenie działania. Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby pomóc w asynchronicznym wywołaniu metody. Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, serwer proxy tworzy podprocedurę *NameOfWebServiceFunction*`Async`, zdarzenie *NameOfWebServiceFunction*`Completed` i klasę`CompletedEventArgs` *NameOfWebServiceFunction* . Ten przykład ilustruje sposób używania asynchronicznych elementów członkowskich do uzyskiwania dostępu do funkcji `getTemp` usługi sieci Web DemoTemperatureService.

> [!NOTE]
> Ten kod nie działa w aplikacjach sieci Web, ponieważ ASP.NET nie obsługuje obiektu `My.WebServices`.

## <a name="call-a-web-service-asynchronously"></a>Asynchroniczne wywoływanie usługi sieci Web

1. Odwołuje się do usługi sieci Web DemoTemperatureService w `http://www.xmethods.net`. Adres to

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Dodaj program obsługi zdarzeń dla zdarzenia `getTempCompleted`:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Nie można użyć instrukcji `Handles`, aby skojarzyć procedurę obsługi zdarzeń ze zdarzeniami obiektu `My.WebServices`.

3. Dodaj pole do śledzenia, jeśli program obsługi zdarzeń został dodany do zdarzenia `getTempCompleted`:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Dodaj metodę, aby dodać procedurę obsługi zdarzeń do zdarzenia `getTempCompleted`, w razie potrzeby, i wywołać metodę `getTempAsync`:

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

    Aby wywołać metodę sieci Web `getTemp` asynchronicznie, wywołaj metodę `CallGetTempAsync`. Po zakończeniu metody sieci Web jej wartość zwracana jest przenoszona do procedury obsługi zdarzeń `getTempCompletedHandler`.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do usług sieci Web aplikacji](accessing-application-web-services.md)
- [My.WebServices, obiekt](../../language-reference/objects/my-webservices-object.md)
