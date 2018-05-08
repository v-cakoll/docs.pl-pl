---
title: Element TransactionScope można zagnieżdżać w ramach usługi
ms.date: 03/30/2017
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
ms.openlocfilehash: 9c556df417548ab348d1dd5bc642928ae68d8878
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nesting-of-transactionscope-within-a-service"></a>Element TransactionScope można zagnieżdżać w ramach usługi
W tym przykładzie składa się z dwóch scenariuszy uruchomienia przedstawiający sposób obsługi <xref:System.Activities.Statements.TransactionScope> wystąpienia działania w ramach usługi. Najpierw transakcja jest inicjowana przy użyciu <xref:System.Activities.Statements.TransactionScope> działanie, aby utworzyć nową transakcję na kliencie i <xref:System.ServiceModel.Activities.TransactedReceiveScope> otrzymywanie i zakres okres istnienia transakcji na serwerze. Pierwszego scenariusza, w ramach usługi uruchamia dodatkowej <xref:System.Activities.Statements.TransactionScope> działania, aby zademonstrować zagnieżdżanie <xref:System.Activities.Statements.TransactionScope> działań w ramach usługi. Drugi scenariusz pokazuje, jak są przestrzegane limitów czasu w zagnieżdżonych <xref:System.Activities.Statements.TransactionScope> działań.  
  
## <a name="client-application"></a>Aplikacja kliencka  
 Aplikacja kliencka uruchamia przepływ pracy, który rozpoczyna się <xref:System.Activities.Statements.TransactionScope> działania, wyświetla identyfikator transakcji rozproszonej, wysyła wiadomość do serwera, przepływu transakcji, otrzyma odpowiedź, ponownie wyświetla identyfikator transakcji rozproszonej i zakończeniu. Jest to jeden raz dla każdego scenariusza usługi.  
  
## <a name="server-application"></a>Serwer aplikacji  
 Projekt serwera znajduje się w <xref:System.ServiceModel.Activities.WorkflowServiceHost>, która tworzy punkt końcowy do nasłuchiwania komunikat z klienta. Przepływ pracy skupia się na <xref:System.ServiceModel.Activities.TransactedReceiveScope>, który odbiera przesłanej transakcji od klienta, wyświetla identyfikator transakcji rozproszonej, a następnie wykonuje drugi <xref:System.Activities.Statements.TransactionScope> działania. W pierwszym scenariuszu transakcji zostało ukończone pomyślnie. W drugim scenariuszu treści <xref:System.Activities.Statements.TransactionScope> działania jest pięciu sekund opóźnienia i limit czasu dla transakcji jest ustawiony na dwóch sekund. Gdy transakcja wygaśnie transakcja została przerwana.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie TransactionServiceExample.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**. W oknie dialogowym wybierz **wiele projektów startowych** i upewnij się, Akcja dla obu projektów jest **Start**.  
  
4.  Naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Alternatywnie, naciśnij klawisze CTRL + F5 lub wybierz **uruchomić bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
