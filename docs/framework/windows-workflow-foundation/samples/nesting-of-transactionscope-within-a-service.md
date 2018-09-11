---
title: Zagnieżdżanie elementu TransactionScope w ramach usługi
ms.date: 03/30/2017
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
ms.openlocfilehash: cf73c0c2d061f1c997a8ade5d7b2bf61887915ca
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266430"
---
# <a name="nesting-of-transactionscope-within-a-service"></a>Zagnieżdżanie elementu TransactionScope w ramach usługi
W tym przykładzie składa się z dwóch scenariuszy uruchamianą przedstawiający sposób obsługi <xref:System.Activities.Statements.TransactionScope> wystąpienia działania w ramach usługi. Najpierw transakcji jest inicjowane z użyciem <xref:System.Activities.Statements.TransactionScope> działanie, aby utworzyć nową transakcję na komputerze klienckim i <xref:System.ServiceModel.Activities.TransactedReceiveScope> do odbierania i zakres okres istnienia transakcji na serwerze. Pierwszego scenariusza, w ramach usługi uruchamia pomocniczy <xref:System.Activities.Statements.TransactionScope> działania, aby zademonstrować zagnieżdżania <xref:System.Activities.Statements.TransactionScope> działań w ramach usługi. Drugi scenariusz pokazuje, jak są przestrzegane przekroczeń limitu czasu w ramach zagnieżdżonej <xref:System.Activities.Statements.TransactionScope> działań.  
  
## <a name="client-application"></a>Aplikacja kliencka  
 Aplikacja kliencka uruchamia przepływ pracy, który rozpoczyna się <xref:System.Activities.Statements.TransactionScope> działania, wyświetla identyfikator transakcji rozproszonych, wysyła wiadomość do serwera, przepływy transakcji, odbiera odpowiedź, ponownie wyświetla identyfikator transakcji rozproszonych i kończy. Odbywa się to raz w każdym scenariuszu usługi.  
  
## <a name="server-application"></a>Aplikacja serwera  
 Projekt serwera znajduje się w <xref:System.ServiceModel.Activities.WorkflowServiceHost>, co powoduje utworzenie punktu końcowego do nasłuchiwania wiadomości od klienta. Przepływ pracy będzie wspomagał <xref:System.ServiceModel.Activities.TransactedReceiveScope>, który odbiera transakcji od klienta, wyświetla identyfikator transakcji rozproszonych, a następnie wykonuje sekundy <xref:System.Activities.Statements.TransactionScope> działania. W pierwszym scenariuszu transakcji zakończyło się powodzeniem. W drugim scenariuszu treści <xref:System.Activities.Statements.TransactionScope> działanie jest pięć sekund opóźnienia i limit czasu dla transakcji jest ustawiony na dwóch sekund. Gdy transakcja upłynie limit transakcji zostało przerwane.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie TransactionServiceExample.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B, lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**. W oknie dialogowym wybierz **wiele projektów startowych** i upewnić się jest działanie w obu projektach **Start**.  
  
4.  Naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Alternatywnie, naciśnij klawisze CTRL + F5 lub wybierz **Rozpocznij bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
