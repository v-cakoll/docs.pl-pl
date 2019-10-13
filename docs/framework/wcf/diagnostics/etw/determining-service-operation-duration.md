---
title: Określanie czasu trwania operacji usługi
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 06a4c2da7b702fa4fbc1469576c118b790803339
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291422"
---
# <a name="determining-service-operation-duration"></a>Określanie czasu trwania operacji usługi
Jeśli śledzenie analityczne jest włączone w aplikacji Windows Communication Foundation (WCF), czas wykonywania operacji na usłudze można łatwo określić, sprawdzając dziennik zdarzeń.  W tym temacie pokazano, jak określić czas trwania operacji usługi.  
  
### <a name="determining-service-operation-execution-duration"></a>Określanie czasu trwania wykonywania operacji usługi  
  
1. Otwórz Podgląd zdarzeń, klikając przycisk **Start**, **uruchom**i wprowadzając `eventvwr.exe`.  
  
2. Jeśli nie włączono śledzenia analitycznego, rozwiń węzeł **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **serwer aplikacji-aplikacje**. Wybierz **Widok**, **Pokaż dzienniki analityczne i debugowania**. Kliknij prawym przyciskiem myszy pozycję **analityczne** i wybierz pozycję **Włącz dziennik**. Pozostaw Podgląd zdarzeń otwarty, aby można było wyświetlić ślady po uruchomieniu operacji usługi.  
  
3. Następnie otwórz aplikację WCF, która zawiera projekt usługi i projekt klienta, który współdziała z tą usługą.  Taką aplikację można utworzyć, wykonując czynności opisane w [samouczku wprowadzenie](../../getting-started-tutorial.md).  Jeśli masz zainstalowane przykłady WCF, możesz otworzyć [wprowadzenie](../../samples/getting-started-sample.md), która zawiera ukończony projekt utworzony w samouczku.  
  
4. Uruchom aplikację serwera, naciskając klawisz **F5**. Aby wykonać aplikację kliencką, kliknij prawym przyciskiem myszy projekt **klienta** i wybierz polecenie **Debuguj**, **Uruchom nowe wystąpienie**.  
  
5. W Podgląd zdarzeń Odśwież dziennik analityczny i posortuj zdarzenia według identyfikatora zdarzenia.  Poszukaj zdarzeń o IDENTYFIKATORze zdarzenia [214-OperationCompleted](214-operationcompleted.md).  Te zdarzenia będą wskazywać, które operacje zostały zakończone, oraz czas trwania operacji.  Poniższe zdarzenie pokazuje czas trwania operacji dodawania.  
  
    ```output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
