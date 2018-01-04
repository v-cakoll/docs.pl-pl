---
title: "Opóźnienie bezwzględne"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6974c7bb281aa6685725b65edd06bb40a907559
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="absolute-delay"></a>Opóźnienie bezwzględne
Główne scenariusz dla tego przykładu jest opóźnienia do określonej <xref:System.DateTime> przy użyciu czasomierze trwałe w aplikacji przepływu pracy. To jest inny niż przy użyciu wbudowanych <xref:System.Activities.Statements.Delay> działania, jak to tylko umożliwi to opóźnienie dla danego <xref:System.TimeSpan> (lub liczba minut i sekund).  
  
 Niektóre scenariusze rzeczywistych, w których warto utworzyć tę różnicę, są następujące:  
  
1.  Chcesz Opóźnij wysyłanie wiadomości przez 30 sekund, upewnij się, że wszystkie błędy nie zostały wprowadzone.  
  
2.  Czy działa zbyt długo i opóźnić wszystkie Twoje wysyła pocztę do normalnego godzinami pracy (na przykład 8 am).  
  
## <a name="demonstrates"></a>Demonstracje  
  
1.  <xref:System.Activities.Statements.DurableTimerExtension>Bezwzględny opóźnienie wykonywania  
  
2.  Konfigurowanie przy użyciu trwałości <xref:System.Activities.WorkflowApplication> dla trwałego czasomierze  
  
3.  Użycie <xref:System.Activities.NativeActivity%601> z punktów rozszerzalności  
  
4.  Użycie <xref:System.Activities.CodeActivity%601> w działaniu SendEmail  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  Tylko do XAML przepływu pracy  
  
 Ten przykład przedstawia sposób tworzenia działań niestandardowych, który przyjmuje <xref:System.DateTime> i używa czasomierze trwałe, aby zarejestrować czas trwania opóźnienia. Korzystając z czasomierze trwałe, należy użyć <xref:System.Activities.NativeActivity> utworzyć zakładki, ponieważ będzie on potrzebny do zarejestrowania tego zakładki z rozszerzeniem czasomierza. W tym przykładzie, po wygaśnięciu czasomierza trwałe `OnTimerExpired` metoda zostanie wywołana. Upewnij się, że dodawania rozszerzenia czasomierza <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> zdarzenia w celu zapewnienia udostępniasz środowiska uruchomieniowego z tymi informacjami. Tylko innych implementacji szczegółów jest należy wdrożyć logikę do przekonwertowania z <xref:System.DateTime> do <xref:System.TimeSpan>, ponieważ czasomierze trwałe tylko <xref:System.DateTime>. Należy pamiętać, że małych wygasną dokładności za pomocą ćwiczeń  
  
> [!NOTE]
>  Brak małych utratę dokładności poprzez konwersję z <xref:System.DateTime> do <xref:System.TimeSpan>.  
  
 W tym przykładzie również pokazano, jak włączyć trwałości dla <xref:System.Activities.WorkflowApplication>. Dla tego konkretnego przykładu użyjemy czasomierze trwałe, w których dane przepływu pracy zostanie usunięty w bazie danych trwałości w czasie bezczynności podczas oczekiwania na czasomierz wygaśnie. Ta implementacja można również dla innych akcji trwałości. W tym przykładzie pokazano, jak skonfigurować trwałości parametry połączenia z programem SQL Server oraz sposobu tworzenia w magazynie wystąpień w celu utrwalenia danych dla wystąpienia przepływu pracy. Logika znajduje się na temat sposobu wznowienie działania przepływu pracy, gdy zdarzenie jest zgłaszane, co sprawia, że wystąpienie przepływu pracy do uruchomienia.  
  
 Podczas wykonywania kroków za pomocą tego przykładu, pojawi się, że czas, w którym wbudowane opóźnienie rozpoczyna się i zakończeniu, który z kolei spowoduje wysłanie wiadomości e-mail. Z tego miejsca, działanie AbsoluteDelay spowoduje zatrzymanie do określonej <xref:System.DateTime> (lub 0 sekund, jeśli <xref:System.DateTime> wygasł) który z kolei spowoduje wysłanie wiadomości e-mail po wygaśnięciu. Wyświetli dwóch różnych zastosowań wbudowanych <xref:System.Activities.Statements.Delay> funkcjonalność w porównaniu z użyciem działania AbsoluteDelay.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że program SQL Server Express (lub nowszej) zainstalowane na tym komputerze  
  
2.  Uruchom setup.cmd (z WF/Basic/Services/AbsoluteDelay/CS) [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia, aby utworzyć bazę danych AbsoluteDelaySampleDB, tworzony jest schemat trwałości i tworzenia logiki trwałości.  
  
3.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Określ czas trwania w działaniu Delay.  
  
5.  Określ ExpirationTime w działaniu AbsoluteDelay.  
  
6.  Zaktualizuj pola SendMailTo, SendMailFrom SendMailSubject, SendMailBody i SmtpHost w działaniu SendMail.  
  
    > [!NOTE]
    >  Jeśli nie podasz prawidłowego hosta SMTP aplikacji spowoduje zgłoszenie wyjątku SMTP.  
  
7.  Skompiluj rozwiązanie, wybierając **kompilacji**, **Kompiluj rozwiązanie**.  
  
8.  Uruchom rozwiązanie, naciskając klawisz **F5**.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
