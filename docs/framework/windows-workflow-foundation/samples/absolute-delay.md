---
title: Opóźnienie bezwzględne
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 30719a4340b738a7462584c4dca00f6d5d90ac72
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486105"
---
# <a name="absolute-delay"></a>Opóźnienie bezwzględne
Główne scenariusz, w tym przykładzie jest opóźnienie do określonego <xref:System.DateTime> pomocą timerów trwałe w aplikacji przepływu pracy. To różni się od przy użyciu wbudowanych <xref:System.Activities.Statements.Delay> działania, ponieważ tylko umożliwi opóźnienia, zanim danego <xref:System.TimeSpan> (lub liczba minut i sekund).  
  
 Niektóre rzeczywistych scenariuszy, w których warto takiego rozróżnienia, obejmują następujące elementy:  
  
1.  Chcesz Opóźnij wysyłanie wiadomości przez 30 sekund upewnić się, że zostało zgłoszone przez Ciebie wszelkie błędy.  
  
2.  Jesteś przeciążonego i ma być opóźnienie wszystkie swoje wiadomości e-mail do normalnego godzinach (na przykład 8: 00).  
  
## <a name="demonstrates"></a>Demonstracje  
  
1.  <xref:System.Activities.Statements.DurableTimerExtension> implementowania opóźnienie bezwzględne  
  
2.  Konfigurowanie trwałości za pomocą <xref:System.Activities.WorkflowApplication> dla trwałego czasomierzy  
  
3.  Korzystanie z <xref:System.Activities.NativeActivity%601> z punktów rozszerzeń  
  
4.  Korzystanie z <xref:System.Activities.CodeActivity%601> w działaniu SendEmail  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  Tylko do XAML przepływu pracy  
  
 W tym przykładzie pokazano, jak utworzyć niestandardowe działanie, które pobiera <xref:System.DateTime> i używa czasomierzy trwałe, aby zarejestrować czas trwania opóźnienia. Korzystając z czasomierzy trwałe, należy użyć <xref:System.Activities.NativeActivity> utworzyć zakładki, ponieważ będzie potrzebny do zarejestrowania tego zakładki z rozszerzeniem czasomierza. W tym przykładzie, po upływie okresu działania czasomierza trwałe `OnTimerExpired` metoda zostanie wywołana. Upewnij się, którego dodajesz rozszerzenie czasomierza w <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> zdarzenie, aby upewnić się, udostępniasz środowisko uruchomieniowe z tymi informacjami. Tylko inne szczegółowo opisuje implementacja jest, musisz zaimplementować logikę do konwersji z <xref:System.DateTime> do <xref:System.TimeSpan>, ponieważ czasomierze trwałe tylko <xref:System.DateTime>. Należy pamiętać, że wygaśnięcie małych dokładność wykonując  
  
> [!NOTE]
>  Istnieje mały utratą dokładności przez konwersję z <xref:System.DateTime> do <xref:System.TimeSpan>.  
  
 Ten przykład pokazuje również, jak włączanie stanów trwałych dla <xref:System.Activities.WorkflowApplication>. Dla tego konkretnego przykładu użyjemy czasomierzy trwałe, w których danych przepływu pracy zostanie usunięty w bazie danych trwałości w czasie bezczynności podczas oczekiwania na czasomierz wygaśnie. Ta implementacja można również dla innych akcji trwałości. Niniejszy przykład pokazuje, jak skonfigurować stan trwały parametry połączenia z programem SQL Server oraz sposób tworzenia magazynu wystąpienia w celu utrwalenia danych dla wystąpienia przepływu pracy. Logika znajduje się na temat sposobu wznowić przepływ pracy, gdy zdarzenie jest zgłaszane, co sprawia, że wystąpienie przepływu pracy jest możliwy do uruchomienia.  
  
 Podczas wykonywania kroków za pośrednictwem tego przykładu, zobaczysz, że czas, w którym wbudowane opóźnienie rozpoczyna się i kończy, który z kolei spowoduje, że wiadomość e-mail do wysłania. W efekcie działania AbsoluteDelay zatrzyma się aż do określonej <xref:System.DateTime> (lub 0 (w sekundach) Jeśli <xref:System.DateTime> wygasła) co z kolei spowoduje wysłanie wiadomość e-mail po upływie. Spowoduje to wyświetlenie dwóch różnych zastosowań wbudowanych <xref:System.Activities.Statements.Delay> funkcjonalność w porównaniu z użyciem AbsoluteDelay działania.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że program SQL Server Express (lub nowszy) zainstalowane na tym komputerze  
  
2.  Uruchom plik setup.cmd (z programu WF/Basic/Services/AbsoluteDelay/CS) [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia, aby utworzyć bazę danych AbsoluteDelaySampleDB, tworzony jest schemat trwałości i tworzenie logiki trwałości.  
  
3.  Otwórz rozwiązanie w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Określ czas trwania w działaniu opóźnienia.  
  
5.  Określ czas wygaśnięcia w działaniu AbsoluteDelay.  
  
6.  Zaktualizuj pola SendMailTo, SendMailFrom, SendMailSubject, SendMailBody i SmtpHost w działaniu SendMail.  
  
    > [!NOTE]
    >  Jeśli nie zostanie wprowadzony nieprawidłowy host SMTP, aplikacji spowoduje zgłoszenie wyjątku SMTP.  
  
7.  Skompiluj rozwiązanie, wybierając **kompilacji**, **Kompiluj rozwiązanie**.  
  
8.  Uruchom rozwiązanie, naciskając klawisz **F5**.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
