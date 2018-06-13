---
title: Określanie czasu trwania operacji usługi
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 8c86ccc09979071e0678be792f4937d526e23fa7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804966"
---
# <a name="determining-service-operation-duration"></a>Określanie czasu trwania operacji usługi
Śledzenie analityczne włączenie w aplikacji Windows Communication Foundation (WCF) czas realizacji dla operacji usługi można łatwo ustalić, sprawdzając dziennik zdarzeń.  W tym temacie przedstawiono sposób określania ilości czas do ukończenia operacji usługi.  
  
### <a name="determining-service-operation-execution-duration"></a>Określanie czasu wykonywania operacji usługi  
  
1.  Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.  
  
2.  Jeśli nie włączono śledzenie analityczne, rozwiń węzeł **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji serwera aplikacji** . Wybierz **widoku**, **wyświetlanie analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**. Pozostaw otwarte Podgląd zdarzeń, dzięki czemu można wyświetlać danych śledzenia po uruchomieniu operacji usługi.  
  
3.  Następnie otwórz folder aplikacji WCF, która zawiera projekt usługi i projekt klienta, który współdziała z tej usługi.  Można tworzyć z takich aplikacji, wykonując [Wprowadzenie — samouczek](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Jeśli masz zainstalowanych przykładów WCF, możesz otworzyć [wprowadzenie](../../../../../docs/framework/wcf/samples/getting-started-sample.md), zawierającą ukończone projekt utworzony w samouczku.  
  
4.  Wykonanie tych aplikacji serwera, naciskając klawisz **F5**. Uruchom aplikację klienta przez kliknięcie prawym przyciskiem myszy **klienta** projekt i wybierając **debugowania**, **uruchomić nowe wystąpienie**.  
  
5.  W Podglądzie zdarzeń Odśwież dziennika analityczne i posortuj zdarzenia według identyfikatora zdarzenia.  Poszukaj zdarzeń o identyfikatorze zdarzenia [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Te zdarzenia zostaną wyświetlone, jakie operacje zostały wykonane, a czas trwania operacji został.  Następujące zdarzenie zawiera czas trwania operacji dodawania.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
