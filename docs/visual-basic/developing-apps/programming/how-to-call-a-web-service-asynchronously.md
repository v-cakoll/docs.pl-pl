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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Porady: asynchroniczne wywoływanie usługi sieci Web (Visual Basic)
W tym przykładzie dołącza program obsługi do Zdarzenie asynchroniczne obsługi usługi sieci Web, dzięki czemu można pobrać wyniku asynchroniczne wywołanie metody. W tym przykładzie użyto usługi sieci DemoTemperatureService Web na http://www.xmethods.net.  
  
 Usługi sieci Web w przypadku odwołania do projektu w programie Visual Studio programowanie środowiska IDE (Integrated), jest ona dodawana do `My.WebServices` obiekt i IDE generuje klasy serwera proxy klienta do dostępu do określonej usługi sieci Web  
  
 Klasy serwera proxy można wywołać metody usługi sieci Web synchronicznie, gdy aplikacja oczekuje na funkcja do wykonania. Ponadto serwer proxy tworzy dodatkowych członków, aby wywołać metodę asynchronicznie. Dla każdej funkcji usługi sieci Web *NameOfWebServiceFunction*, tworzy serwer proxy *NameOfWebServiceFunction* `Async` podprocedury, *NameOfWebServiceFunction* `Completed` zdarzeń, a *NameOfWebServiceFunction* `CompletedEventArgs` klasy. W tym przykładzie pokazano, jak uzyskiwać dostęp do członków asynchroniczne `getTemp` funkcji usługi sieci DemoTemperatureService Web.  
  
> [!NOTE]
>  Ten kod nie działa w aplikacji sieci Web, ponieważ nie obsługuje platformy ASP.NET `My.WebServices` obiektu.  
  
### <a name="to-call-a-web-service-asynchronously"></a>Aby asynchroniczne wywoływanie usługi sieci Web  
  
1.  Odwołanie do usługi sieci DemoTemperatureService Web na http://www.xmethods.net. Adres jest  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  Dodaj program obsługi zdarzeń dla `getTempCompleted` zdarzeń:  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  Nie można użyć `Handles` instrukcji do skojarzenia z obsługi zdarzeń `My.WebServices` zdarzenia obiektu.  
  
3.  Dodawanie pola do śledzenia, jeśli program obsługi zdarzeń został dodany do `getTempCompleted` zdarzeń:  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  Dodaj metodę Dodaj program obsługi zdarzeń do `getTempCompleted` zdarzeń, jeśli to konieczne oraz wywołanie `getTempAsynch` metody:  
  
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
  
     Aby wywołać `getTemp` sieci Web metody asynchronicznie, wywołaj `CallGetTempAsync` metody. Po zakończeniu działania metody sieci Web, jego wartości zwracanej są przekazywane do `getTempCompletedHandler` obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do usług sieci Web aplikacji](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)  
 [My.WebServices, obiekt](../../../visual-basic/language-reference/objects/my-webservices-object.md)
