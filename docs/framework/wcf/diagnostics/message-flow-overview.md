---
title: Przegląd przepływu komunikatu
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: d75a535a601612196ef66151a4685723e048848f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797489"
---
# <a name="message-flow-overview"></a>Przegląd przepływu komunikatu
W rozproszonym systemie zawierający wzajemnie połączonych usług należy określić przyczynowego relacje między usługami. Jest ważne poznać różne składniki, które były częścią przepływu żądania w celu obsługi scenariuszy o kluczowym znaczeniu, takich jak kondycja, monitorowanie, rozwiązywanie problemów i główny ustalić przyczynę problemu. Aby włączyć korelacja różnych usług w programie .NET Framework 4 ślady Dodaliśmy obsługę funkcji za pomocą następujących funkcji:

- Śledzenie analityczne: Wysoka wydajność i funkcję śledzenia niski poziom szczegółowości przy użyciu śledzenie zdarzeń dla Windows (ETW).

- Model działania end-to-end dla usług WCF/WF: Ta funkcja obsługuje korelacji śledzenia generowane przez <xref:System.ServiceModel> i <xref:System.Workflow.ComponentModel> przestrzeni nazw.

- ETW śledzenia dla WF: Ta funkcja używa rekordów śledzenia generowanych przez usługi WF, aby zapewnić wgląd w bieżący stan i postęp przepływu pracy.

 Błędy zalogowany śledzenia i śledzenia rekordów może służyć do znalezienia usterek kodu lub niepoprawnie uformowane wiadomości. Właściwość Identyfikator korelacji węzła w nagłówku komunikatu zdarzenia może służyć do określenia łagodne działanie. Aby włączyć śledzenia przepływu komunikatów za pomocą Identyfikatora działania, zobacz [Konfigurowanie śledzenia przepływu komunikatów](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). W tym temacie pokazano, jak włączyć śledzenie przepływu wiadomości w projekcie, utworzone w ramach samouczka Wprowadzenie.

### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Aby włączyć śledzenia przepływu komunikatów w ramach samouczka Wprowadzenie

1. Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.

2. Jeśli nie zostały włączone śledzenie danych analitycznych, rozwiń **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacje serwera aplikacji** . Wybierz **widoku**, **Pokaż analityczne i debugowania dzienniki**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**. Pozostaw otwarte Podgląd zdarzeń, dzięki czemu można wyświetlić ślady.

3. Otwórz plik, który został utworzony w [Samouczek wprowadzający](../../../../docs/framework/wcf/getting-started-tutorial.md) w programie Visual Studio 2012. Należy pamiętać, że należy uruchomić program Visual Studio 2012 jako administrator, aby tworzyć usługi. Jeśli masz zainstalowanych przykładów WCF, możesz otworzyć [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), zawierającą ukończone projekt utworzony w tym samouczku.

4. Kliknij prawym przyciskiem myszy **usługi** projektu, a następnie wybierz **Dodaj**, **nowy element**. Wybierz **pliku konfiguracji aplikacji** i kliknij przycisk **OK**.

5. Dodaj następujący kod do pliku App.Config utworzonego w poprzednim kroku.

    ```xml
    <system.serviceModel>
      <diagnostics>
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
      </diagnostics>
    </system.serviceModel>
    ```

6. Wykonywanie aplikacji serwera bez debugowania, naciskając klawisze CTRL + F5. Wykonaj projekt klienta, klikając prawym przyciskiem myszy **klienta** projektu i wybierając polecenie **debugowania**, **Uruchom nowe wystąpienie**.

7. Aby śledzić zdarzenia od klienta do serwera, Dodaj następujący element do pliku konfiguracji aplikacji w projekcie klienta.

    ```xml
    <diagnostics>
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
    </diagnostics>
    ```

8. W pliku Program.cs w kliencie Dodaj następującą instrukcję Using.

    ```csharp
    using System.Diagnostics;
    ```

9. W ramach metody Main w pliku program.cs w projekcie klienta należy ustawić GUID śledzenia i propagowane w dzienniku zdarzeń.

    ```csharp
    Guid guid = Guid.NewGuid();
    Trace.CorrelationManager.ActivityId = guid;
    ```

10. Odśwież i zbadać **analityczne** dziennika.  Wyszukaj zdarzenia z 220 identyfikator zdarzenia.  Wybierz zdarzenie, a następnie kliknij przycisk **szczegóły** tab w okienku podglądu. To zdarzenie będzie zawierać identyfikator korelacji dla działania wywołania.

    ```xml
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />
    ```

    > [!NOTE]
    >  Wszystkie zdarzenia z tego samego identyfikatora GUID w identyfikator odnoszą się do jednego żądania. To może służyć do skorelowania wiadomości z określonego klienta do określonej usługi. Jeśli klient wywołuje inną usługę, ten sam klient może być identyfikowany przez identyfikator działania.

11. W niektórych przypadkach identyfikator można zmienić z oryginalnego identyfikatora GUID na nowy identyfikator działania. W takiej sytuacji jest emitowane transferuje zdarzenie. Ten identyfikator zdarzenia jest 499 i zdarzenie będzie zawierać następujące dane w nagłówku.

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
    >  Zdarzenia transferu rejestruje zmiany active ActivityID z identyfikatorem GUID określony jako identyfikator działania zgodnie z identyfikatorem GUID określony jako RelatedActivityID. Po transferuje zdarzenie jest emitowane, wszystkie zdarzenia będą zawierały nowy identyfikator GUID, jako identyfikator działania.
