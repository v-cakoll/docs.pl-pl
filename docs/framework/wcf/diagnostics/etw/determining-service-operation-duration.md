---
title: Określanie czasu trwania operacji usługi
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: fd7dec5784f50a0613b574822a31202a859b34c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999461"
---
# <a name="determining-service-operation-duration"></a>Określanie czasu trwania operacji usługi
Włączenie śledzenia danych analitycznych w aplikacji Windows Communication Foundation (WCF), czas trwania wykonywania operacji usługi łatwo można ustalić, sprawdzając dziennik zdarzeń.  W tym temacie pokazano, jak określić ilość czasu potrzebnego do ukończenia w operacji usługi.  
  
### <a name="determining-service-operation-execution-duration"></a>Określanie czasu trwania wykonywania operacji usługi  
  
1. Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.  
  
2. Jeśli nie zostały włączone śledzenie danych analitycznych, rozwiń **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacje serwera aplikacji** . Wybierz **widoku**, **Pokaż analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**. Pozostaw otwarte Podgląd zdarzeń, dzięki czemu mogą być wyświetlane dane śledzenia, po uruchomieniu operacji usługi.  
  
3. Następnie otwórz aplikację WCF, która zawiera projekt usługi i projekt klienta, który współdziała z tej usługi.  Taką aplikację można utworzyć, wykonując [Samouczek wprowadzający](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Jeśli masz zainstalowanych przykładów WCF, możesz otworzyć [wprowadzenie](../../../../../docs/framework/wcf/samples/getting-started-sample.md), zawierającą ukończone projekt utworzony w tym samouczku.  
  
4. Uruchom aplikację serwera, naciskając klawisz **F5**. Wykonywanie aplikacji klienckiej, klikając prawym przyciskiem myszy **klienta** projektu i wybierając polecenie **debugowania**, **Uruchom nowe wystąpienie**.  
  
5. W Podglądzie zdarzeń Odśwież dziennik analityczny i posortuj zdarzenia według identyfikatora zdarzenia.  Wyszukaj zdarzenia o identyfikatorze zdarzenia [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Te zdarzenia pokaże, operacje, zostały wykonane, a jaki był czas trwania operacji.  Poniższe zdarzenie zawiera czas trwania operacji dodawania.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
