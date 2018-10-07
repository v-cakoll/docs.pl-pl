---
title: 'Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: bf109780f26ce2fa4d5dbaa63832e765970b5cb4
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842700"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)
W tym przykładzie dołącza obsługę do zdarzenia asynchronicznej obsługi usługi sieci Web tak, aby możliwe było pobieranie wynik wywołania metody asynchronicznej. W tym przykładzie użyto usługi sieci DemoTemperatureService Web na `http://www.xmethods.net`.  
  
 Gdy odwołujesz usługi sieci Web w projekcie w Visual Studio rozwoju środowiska IDE (Integrated) jest dodawany do `My.WebServices` obiektu oraz środowiska IDE generuje klasę proxy klienta do dostępu do określonej usługi sieci Web  
  
 Klasa proxy umożliwia wywołania metody usługi sieci Web synchronicznie, gdzie aplikacja czeka, aż funkcja do wykonania. Ponadto serwer proxy tworzy dodatkowe elementy członkowskie, aby pomóc asynchronicznie Wywołaj metodę. Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, tworzy serwer proxy *NameOfWebServiceFunction* `Async` podprocedury, *NameOfWebServiceFunction* `Completed` zdarzeń, a *NameOfWebServiceFunction* `CompletedEventArgs` klasy. W tym przykładzie przedstawiono sposób użycia asynchronicznych elementów członkowskich dostęp do `getTemp` funkcji usługi sieci DemoTemperatureService Web.  
  
> [!NOTE]
>  Ten kod nie działa w aplikacjach sieci Web, ponieważ nie obsługuje platformy ASP.NET `My.WebServices` obiektu.  
  
### <a name="to-call-a-web-service-asynchronously"></a>Aby asynchroniczne wywoływanie usługi sieci Web  
  
1.  Odwoływać się do usługi sieci DemoTemperatureService Web na `http://www.xmethods.net`. Adres to  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  Dodawanie obsługi zdarzeń dla `getTempCompleted` zdarzeń:  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  Nie można użyć `Handles` instrukcję, aby skojarzyć program obsługi zdarzeń za pomocą `My.WebServices` zdarzenia obiektu.  
  
3.  Dodaj pole do śledzenia, czy program obsługi zdarzeń została dodana do `getTempCompleted` zdarzeń:  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  Dodaj metodę, aby dodać program obsługi zdarzeń do `getTempCompleted` zdarzeń, jeśli to konieczne oraz wywołanie `getTempAsynch` metody:  
  
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
  
     Aby wywołać `getTemp` asynchronicznie metodę sieci Web, wywołaj `CallGetTempAsync` metody. Po zakończeniu metody sieci Web, jego wartość zwracana jest przekazywany do `getTempCompletedHandler` programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
