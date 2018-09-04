---
title: Używanie elementu transactedreceivescope
ms.date: 03/30/2017
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
ms.openlocfilehash: bc1c418f3fa116f5e1c1647af3543a38122842f5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501645"
---
# <a name="use-of-transactedreceivescope"></a>Używanie elementu transactedreceivescope
W tym przykładzie przedstawiono sposób przepływu transakcji od klienta do serwera przy użyciu <xref:System.Activities.Statements.TransactionScope> do utworzenia nowej transakcji na komputerze klienckim i <xref:System.ServiceModel.Activities.TransactedReceiveScope> do odbierania wiadomości z transakcji i zakres okres istnienia transakcji na serwerze. Przykład obejmuje dwa projekty, które wypełniają role klienta i serwera.  
  
## <a name="client-application"></a>Aplikacja kliencka  
 Aplikacja kliencka uruchamia przepływ pracy, który wyświetla identyfikator transakcji rozproszonych, wysyła wiadomość do serwera, przepływy transakcji, odbiera odpowiedź, ponownie wyświetla identyfikator transakcji rozproszonych i kończy. Identyfikator transakcja rozproszona jest początkowo drukuje, jest pustym identyfikatorem GUID jako transakcja jest nadal tylko lokalne.  
  
## <a name="server-application"></a>Aplikacja serwera  
 Projekt serwera jest podobny, jednak przepływ pracy znajduje się w <xref:System.ServiceModel.Activities.WorkflowServiceHost> , ponieważ jego musi nasłuchiwać w punkcie końcowym komunikat z klienta. Przepływ pracy będzie wspomagał <xref:System.ServiceModel.Activities.TransactedReceiveScope>, który odbiera transakcji od klienta, wyświetla komunikat, który został wysłany, wyświetla identyfikator transakcji rozproszonych i wysyła odpowiedź do klienta. Identyfikator transakcji rozproszonych jest teraz niepustym identyfikatorem GUID i jeśli działanie obsługujących transakcji został dodany do treści <xref:System.ServiceModel.Activities.TransactedReceiveScope>, może on wykonać w ramach transakcji.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie TransactedReceiveScope.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B, lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**. W oknie dialogowym wybierz **wiele projektów startowych** i upewnić się jest działanie w obu projektach **Start**.  
  
4.  Naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Alternatywnie, naciśnij klawisze CTRL + F5 lub wybierz **Rozpocznij bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
    > [!NOTE]
    >  Na serwerze muszą działać przed rozpoczęciem klienta. Dane wyjściowe z okna konsoli, obsługujący usługę wskazuje, kiedy została uruchomiona.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`