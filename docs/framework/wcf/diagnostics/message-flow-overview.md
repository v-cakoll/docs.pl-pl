---
title: Przegląd przepływu komunikatu
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: aea0ca4c5a8574f6039cd055561ce7da0099841b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809797"
---
# <a name="message-flow-overview"></a>Przegląd przepływu komunikatu
W systemie rozproszonej zawierający połączonych usług jest niezbędne do określenia przyczynowy relacje między usługami. Ważne jest, aby poznać różne składniki, które były częścią przepływu żądania do obsługi krytycznych scenariuszy, takich jak kondycja monitorowanie, rozwiązywanie problemów i głównego przyczynę problemu. Aby włączyć korelacja śladów różnych usług w .NET Framework 4 dodano obsługę następujących funkcji:  
  
-   Śledzenie analityczne: wysokiej wydajności i niski poziom szczegółowości śledzenia funkcję za pomocą zdarzenia śledzenia dla systemu Windows (ETW).  
  
-   Działanie end-to-end modelu dla usług WCF/WF: Ta funkcja obsługuje korelacji śladów generowane przez <xref:System.ServiceModel> i <xref:System.Workflow.ComponentModel> przestrzeni nazw.  
  
-   Śledzenie WF ETW: funkcja ta używa śledzenie rekordów generowanych przez usługi WF, aby zapewnić wgląd w bieżący stan i postęp przepływu pracy.  
  
 Błędy zalogowany śledzenia lub rekord śledzenia można znaleźć defektów kodu lub niepoprawnie uformowane wiadomości. Właściwość identyfikatora węzła korelacji w nagłówku komunikatu zdarzenia można ustalić aktywność źle działający. Aby włączyć śledzenie przepływu wiadomości przez identyfikator działania, zobacz [Konfigurowanie śledzenia przepływu komunikatów](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). W tym temacie przedstawiono sposób włączania śledzenia przepływu komunikatów w projekcie utworzonej w samouczku wprowadzenie.  
  
### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Aby włączyć śledzenie przepływu wiadomości w samouczku wprowadzenie  
  
1.  Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.  
  
2.  Jeśli nie włączono śledzenie analityczne, rozwiń węzeł **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji serwera aplikacji** . Wybierz **widoku**, **wyświetlanie analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**. Pozostaw otwarte Podgląd zdarzeń, dzięki czemu można wyświetlać danych śledzenia.  
  
3.  Otwórz przykładowe utworzone w [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md) w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. Należy pamiętać, że trzeba uruchomić [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] jako administrator, dzięki czemu można utworzyć usługi. Jeśli masz zainstalowanych przykładów WCF, możesz otworzyć [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), zawierającą ukończone projekt utworzony w samouczku.  
  
4.  Kliknij prawym przyciskiem myszy **usługi** projekt i wybierz **Dodaj**, **nowy element**. Wybierz **pliku konfiguracji aplikacji** i kliknij przycisk **OK**.  
  
5.  Dodaj następujący kod do pliku App.Config utworzony w poprzednim kroku.  
  
    ```xml  
    <system.serviceModel>  
      <diagnostics>  
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
      </diagnostics>  
    </system.serviceModel>  
    ```  
  
6.  Uruchom aplikację serwera bez debugowania, naciskając klawisze CTRL + F5. Wykonanie projektu klienta, klikając prawym przyciskiem myszy **klienta** projekt i wybierając **debugowania**, **uruchomić nowe wystąpienie**.  
  
7.  Śledzenie zdarzeń z klienta do serwera, dodaj następującą wartość do pliku konfiguracji aplikacji w projekcie klienta.  
  
    ```xml  
    <diagnostics>  
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
    </diagnostics>  
    ```  
  
8.  W pliku Program.cs w kliencie Dodaj następującą instrukcję Using.  
  
    ```  
    using System.Diagnostics;  
    ```  
  
9. W metodzie główne w pliku program.cs w projekcie klienta należy ustawić wartość GUID śledzenia propagację w dzienniku zdarzeń.  
  
    ```  
    Guid guid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = guid;  
    ```  
  
10. Odśwież i sprawdź, czy **analityczne** dziennika.  Poszukaj zdarzenia 220 identyfikator zdarzenia.  Wybierz zdarzenie, a następnie kliknij przycisk **szczegóły** w okienku podglądu. To zdarzenie będzie zawierać identyfikator korelacji dla działania wywołania.  
  
    ```xml  
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />  
    ```  
  
    > [!NOTE]
    >  Wszystkie zdarzenia o tym samym identyfikatorze GUID w identyfikator odnoszą się do jednego żądania. Może być używany do skorelowania wiadomości z określonego klienta do określonej usługi. Jeśli klient wywołuje innej usługi, ten sam klient może być identyfikowany przez identyfikator działania.  
  
11. W niektórych przypadkach identyfikator można zmienić z oryginalnego identyfikatora GUID na nowy identyfikator działania. W takim przypadku jest emitowany transferuje zdarzenie. Ten identyfikator zdarzenia jest 499, a zdarzenie będzie zawierać następujące dane w nagłówku.  
  
    ```xml  
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">  
        <System>  
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />   
            <EventID>499</EventID>   
            ...  
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />   
            ...  
       </System>  
    </Event>  
    ```  
  
    > [!NOTE]
    >  Zdarzenia transferu rejestruje zmiany active ActivityID z GUID określony jako identyfikator zgodnie z identyfikatorem GUID podany jako RelatedActivityID. Po wysyłanego transferuje zdarzenie wszystkich zdarzeń będzie zawierać nowego identyfikatora GUID jako identyfikator.
