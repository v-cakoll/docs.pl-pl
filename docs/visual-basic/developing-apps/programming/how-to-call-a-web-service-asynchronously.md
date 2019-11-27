---
title: 'Porady: asynchroniczne wywoływanie usługi sieci Web'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 0eeb358ba38836ba6302f98f9e3e0314b83510f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352120"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)

Ten przykład dołącza procedurę obsługi do zdarzenia asynchronicznej procedury obsługi usługi sieci Web, aby można było pobrać wynik wywołania metody asynchronicznej. W tym przykładzie użyto usługi sieci Web DemoTemperatureService w `http://www.xmethods.net`.

Gdy odwołujesz się do usługi sieci Web w projekcie w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, jest on dodawany do obiektu `My.WebServices`, a IDE generuje klasę proxy klienta w celu uzyskania dostępu do określonej usługi sieci Web

Klasa proxy umożliwia synchroniczną wywoływanie metod usługi sieci Web, w których aplikacja czeka na zakończenie działania. Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby pomóc w asynchronicznym wywołaniu metody. Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, serwer proxy tworzy podprocedurę *NameOfWebServiceFunction*`Async`, zdarzenie *NameOfWebServiceFunction*`Completed` i klasę`CompletedEventArgs` *NameOfWebServiceFunction* . Ten przykład ilustruje sposób używania asynchronicznych elementów członkowskich do uzyskiwania dostępu do funkcji `getTemp` usługi sieci Web DemoTemperatureService.

> [!NOTE]
> Ten kod nie działa w aplikacjach sieci Web, ponieważ ASP.NET nie obsługuje obiektu `My.WebServices`.

### <a name="to-call-a-web-service-asynchronously"></a>Aby asynchronicznie wywołać usługę sieci Web

1. Odwołuje się do usługi sieci Web DemoTemperatureService w `http://www.xmethods.net`. Adres to

    ```
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

- [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
