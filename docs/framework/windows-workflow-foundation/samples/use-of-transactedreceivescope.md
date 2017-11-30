---
title: "Użyj TransactedReceiveScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b01352910c52d117d7ab0adcd94320ff9cf6931d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="use-of-transactedreceivescope"></a>Użyj TransactedReceiveScope
Ten przykład przedstawia sposób uruchomienia przepływu transakcji od klienta do serwera przy użyciu <xref:System.Activities.Statements.TransactionScope> można utworzyć nowej transakcji na komputerze klienckim i <xref:System.ServiceModel.Activities.TransactedReceiveScope> do odbierania wiadomości z przesłanej transakcji i zakres okres istnienia transakcji na serwerze. Przykład zawiera dwa projekty, które pełnienia ról klienta i serwera.  
  
## <a name="client-application"></a>Aplikacja kliencka  
 Aplikacja kliencka uruchamia przepływ pracy, który wyświetla identyfikator transakcji rozproszonej, wysyła wiadomość do serwera, przepływu transakcji, otrzyma odpowiedź, ponownie wyświetla identyfikator transakcji rozproszonej i zakończeniu. Identyfikator transakcji rozproszonej to początkowo odbitek, ma pusty identyfikator GUID, ponieważ transakcja jest nadal tylko lokalnych.  
  
## <a name="server-application"></a>Serwer aplikacji  
 Przypomina Projekt serwera, jednak przepływu pracy znajduje się w <xref:System.ServiceModel.Activities.WorkflowServiceHost> ponieważ go musi nasłuchiwać na punkt końcowy komunikat z klienta. Przepływ pracy skupia się na <xref:System.ServiceModel.Activities.TransactedReceiveScope>, który odbiera przesłanej transakcji od klienta, wyświetla komunikat, który został wysłany, wyświetla identyfikator transakcji rozproszonej i wysyła odpowiedź do klienta. Identyfikator transakcji rozproszonej, jest teraz niepustego identyfikatora GUID, a jeśli działanie obsługujący transakcji został dodany do treści <xref:System.ServiceModel.Activities.TransactedReceiveScope>, jego jest wykonywany w transakcji.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie TransactedReceiveScope.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Skompiluj rozwiązanie, naciśnij kombinację klawiszy CTRL + SHIFT + B lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu.  
  
3.  Gdy kompilacja zakończyła się pomyślnie, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**. W oknie dialogowym wybierz **wiele projektów startowych** i upewnij się, Akcja dla obu projektów jest **Start**.  
  
4.  Naciśnij klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu. Alternatywnie, naciśnij klawisze CTRL + F5 lub wybierz **uruchomić bez debugowania** z **debugowania** menu, aby uruchomić bez debugowania.  
  
    > [!NOTE]
    >  Serwer musi być uruchomiona przed uruchomieniem klienta. Dane wyjściowe z okna konsoli obsługującego usługę wskazuje, kiedy został uruchomiony.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`  
  
## <a name="see-also"></a>Zobacz też
