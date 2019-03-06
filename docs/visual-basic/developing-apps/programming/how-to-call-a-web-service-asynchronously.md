---
title: 'Instrukcje: Asynchroniczne wywoływanie usługi sieci Web (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: 01d2fad6be94f23457ba37cbb15521765e0bea17
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376211"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Instrukcje: Asynchroniczne wywoływanie usługi sieci Web (Visual Basic)

W tym przykładzie dołącza obsługę do zdarzenia asynchronicznej obsługi usługi sieci Web tak, aby możliwe było pobieranie wynik wywołania metody asynchronicznej. W tym przykładzie użyto usługi sieci DemoTemperatureService Web na `http://www.xmethods.net`.

Gdy odwołujesz usługi sieci Web w projekcie w Visual Studio rozwoju środowiska IDE (Integrated) jest dodawany do `My.WebServices` obiektu oraz środowiska IDE generuje klasę proxy klienta do dostępu do określonej usługi sieci Web

Klasa proxy umożliwia wywołania metody usługi sieci Web synchronicznie, gdzie aplikacja czeka, aż funkcja do wykonania. Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby pomóc asynchronicznie Wywołaj metodę. Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, tworzy serwer proxy *NameOfWebServiceFunction* `Async` podprocedury, *NameOfWebServiceFunction* `Completed` zdarzeń, a *NameOfWebServiceFunction* `CompletedEventArgs` klasy. W tym przykładzie przedstawiono sposób użycia asynchronicznych elementów członkowskich dostęp do `getTemp` funkcji usługi sieci DemoTemperatureService Web.

> [!NOTE]
> Ten kod nie działa w aplikacjach sieci Web, ponieważ nie obsługuje platformy ASP.NET `My.WebServices` obiektu.

### <a name="to-call-a-web-service-asynchronously"></a>Aby asynchroniczne wywoływanie usługi sieci Web

1. Odwoływać się do usługi sieci DemoTemperatureService Web na `http://www.xmethods.net`. Adres to

    ```
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Dodawanie obsługi zdarzeń dla `getTempCompleted` zdarzeń:

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Nie można użyć `Handles` instrukcję, aby skojarzyć program obsługi zdarzeń za pomocą `My.WebServices` zdarzenia obiektu.

3. Dodaj pole do śledzenia, czy program obsługi zdarzeń została dodana do `getTempCompleted` zdarzeń:

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Dodaj metodę, aby dodać program obsługi zdarzeń do `getTempCompleted` zdarzeń, jeśli to konieczne oraz wywołanie `getTempAsync` metody:

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

    Aby wywołać `getTemp` asynchronicznie metodę sieci Web, wywołaj `CallGetTempAsync` metody. Po zakończeniu metody sieci Web, jego wartość zwracana jest przekazywany do `getTempCompletedHandler` programu obsługi zdarzeń.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
- [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
