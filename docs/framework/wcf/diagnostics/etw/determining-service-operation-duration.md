---
title: "Określanie czasu trwania operacji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63a8c92713ee452da2439475ac526229d1e5741c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="determining-service-operation-duration"></a>Określanie czasu trwania operacji usługi
Jeśli włączono śledzenie analityczne w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] łatwo można ustalić czas realizacji dla operacji usługi, sprawdzając dziennik zdarzeń aplikacji.  W tym temacie przedstawiono sposób określania ilości czas do ukończenia operacji usługi.  
  
### <a name="determining-service-operation-execution-duration"></a>Określanie czasu wykonywania operacji usługi  
  
1.  Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.  
  
2.  Jeśli nie włączono śledzenie analityczne, rozwiń węzeł **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji serwera aplikacji** . Wybierz **widoku**, **wyświetlanie analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**. Pozostaw otwarte Podgląd zdarzeń, dzięki czemu można wyświetlać danych śledzenia po uruchomieniu operacji usługi.  
  
3.  Następnie otwórz folder [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikacja, która zawiera projekt usługi i projekt klienta, który współdziała z tej usługi.  Można tworzyć z takich aplikacji, wykonując [Wprowadzenie — samouczek](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Jeśli masz [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zainstalowanych przykładów, możesz otworzyć [wprowadzenie](../../../../../docs/framework/wcf/samples/getting-started-sample.md), zawierającą ukończone projekt utworzony w samouczku.  
  
4.  Wykonanie tych aplikacji serwera, naciskając klawisz **F5**. Uruchom aplikację klienta przez kliknięcie prawym przyciskiem myszy **klienta** projekt i wybierając **debugowania**, **uruchomić nowe wystąpienie**.  
  
5.  W Podglądzie zdarzeń Odśwież dziennika analityczne i posortuj zdarzenia według identyfikatora zdarzenia.  Poszukaj zdarzeń o identyfikatorze zdarzenia [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Te zdarzenia zostaną wyświetlone, jakie operacje zostały wykonane, a czas trwania operacji został.  Następujące zdarzenie zawiera czas trwania operacji dodawania.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
