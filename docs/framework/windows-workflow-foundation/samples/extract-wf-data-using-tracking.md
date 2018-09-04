---
title: Wyodrębnianie danych WF przy użyciu śledzenia
ms.date: 03/30/2017
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
ms.openlocfilehash: ef8118df2c5834e32c40760ef31f75660893d89b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501586"
---
# <a name="extract-wf-data-using-tracking"></a>Wyodrębnianie danych WF przy użyciu śledzenia
Ten przykład pokazuje sposób użycia śledzenia można wyodrębnić zmienne przepływu pracy i argumenty z działań przepływu pracy. Pokazuje także dodawanie adnotacji do śledzenia rekordów i wyodrębnianie ładunku danych w ramach śledzenia niestandardowe rekordów. W przykładzie użyto uczestnika śledzenia Śledzenie zdarzeń dla Windows (ETW), aby wyodrębnić dane z przepływu pracy.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Windows Workflow Foundation (WF) umożliwia śledzenie, aby uzyskać wgląd w wykonywania wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia emituje przepływu pracy śledzenia rekordów podczas wykonywania przepływu pracy. Wraz z rekordów śledzenia przepływu pracy dane w ramach wystąpienie przepływu pracy można wyodrębnić z przepływu pracy. Poniżej przedstawiono szczegółową listę typów danych, które można wyodrębnić z rekordy śledzenia:  
  
1.  Zmienne przepływu pracy w ramach działania i rekordy śledzenia podczas wykonywania działania.  
  
     Aby wyodrębnić zmienne przepływu pracy, zmienne, które ma zostać wyodrębniony są określone w profilu. Zmienne, które ma zostać wyodrębniony można określić tylko z `ActivityStateQueries`. Poniższy przykład kodu pokazuje profil śledzenia służą do wyodrębniania zmiennej przepływu pracy na podstawie działania.  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  Argumenty aktywności i stanu działania śledzenia rekordów.  
  
     Argumenty do definiowania danych sposób przepływów w lub poza nią działania. Argumenty, które można wyodrębnić są określane za pomocą <xref:System.Activities.Tracking.ActivityStateQuery>. Poniższy przykład kodu jest profilu śledzenia, która wyodrębnia `Value` argumentu.  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  Adnotacje są pary klucz/wartość, które można dodać do dowolnego rekordu śledzenia, który jest emitowane.  
  
     Adnotacje służyć jako znakowania mechanizm śledzenia rekordów. Adnotacje są dodawane do śledzenia rekordów za pomocą profilu śledzenia. Adnotacje można dodać do dowolnego typu zapytania śledzenia przepływu pracy. Poniższy przykład kodu jest profilu śledzenia, który pokazuje, jak można dodać adnotacji z rekordem śledzenia.  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  Niestandardowe rekordy śledzenia są emitowane z działań użytkownika.  
  
     Niestandardowe rekordy śledzenia może przenosić dane ładunku zdefiniowany w ramach tego działania. Subskrybowania śledzenia niestandardowe rekordów w profilu śledzenia umożliwia wyodrębnianie ładunku w rekordem śledzenia. Można wyodrębnić śledzenia niestandardowe rekordów za pomocą niestandardowego <xref:System.Activities.Tracking.TrackingQuery>. Poniższy przykład kodu jest profilu śledzenia, która wyodrębnia rekord śledzenia niestandardowego, wraz z jego ładunku.  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 W przykładzie pokazano wyodrębniania zmienne, argumenty, niestandardowych rekordów i dodawanie adnotacji, przy użyciu profilu określony w pliku Web.config. Śledzenia jest włączona na przykład usługi przepływu pracy, dodając `<etwTracking>` element zachowania. Poniższy kod przykładowy umożliwia śledzenie `ExtractWorkflowVariables` profil śledzenia.  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WFStockPriceApplication.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
     Okno przeglądarki otwiera i pokazuje katalog zawierający informacje o aplikacji.  
  
4.  W przeglądarce kliknij przycisk StockPriceService.xamlx.  
  
5.  W przeglądarce pojawi się stronie StockPriceService zawiera usługę lokalnego adresu WSDL. Skopiuj ten adres.  
  
     Poniższy przykład pokazuje adresu lokalnej usługi WSDL. `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Przed wywołaniem usługi, Uruchom Podgląd zdarzeń i upewnij się, czy w dzienniku zdarzeń nasłuchuje dla śledzenia zdarzeń wysyłanego z usługi przepływu pracy.  
  
7.  Z **Start** menu, wybierz opcję **narzędzia administracyjne** i następnie **Podgląd zdarzeń**.  
  
8.  W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, i **Microsoft**. Kliknij prawym przyciskiem myszy **Microsoft** i wybierz **widoku** i następnie **Pokaż analityczne i debugowania dzienniki**.  
  
     Upewnij się, że **Pokaż analityczne i debugowania dzienniki** opcja jest zaznaczona.  
  
9. W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.  
  
10. Za pomocą [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otwórz klienta testowego WCF.  
  
     Testowy klient WCF (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji > \Common7\IDE\ folderu.  
  
     Wartość domyślna [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji to C:\Program Files\Microsoft Visual Studio 10.0.  
  
11. W kliencie testowym WCF, wybierz **Dodaj usługę** z **pliku** menu.  
  
     Dodaj usługę lokalnego adresu WSDL, który został wcześniej skopiowany w polu wejściowym.  
  
12. W kliencie testowym WCF, kliknij dwukrotnie `GetStockPrice`.  
  
     Spowoduje to otwarcie `GetStockPrice` metody. Żądanie przyjmuje jeden parametr. Użyj wartości **Contoso**.  
  
13. Kliknij przycisk **wywołania**.  
  
14. Przejdź z powrotem do programu Podgląd zdarzeń i przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**. Zdarzenia przepływu pracy w zdarzeniu są zakresy identyfikatorów 100 199.  
  
     Zdarzenia zawierać adnotacji, zmienne, argumenty i śledzenia niestandardowe rekordów, które mogą być wyświetlane w zdarzeniu podglądu.  
  
## <a name="cleaning-up-in-the-event-viewer"></a>Czyszczenie w zdarzeniu podglądu  
 Kanał analityczne w dzienniku zdarzeń mogą zostać wyczyszczone w zdarzeniu podglądu, wykonując następujące czynności.  
  
#### <a name="to-clean-up-optional"></a>Aby wyczyścić (opcjonalnie)  
  
1.  Otwórz Podgląd zdarzeń.  
  
2.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączanie dziennika**.  
  
3.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.  
  
     Wybierz **wyczyść** możliwość wyczyszczenia zdarzeń.  
  
## <a name="known-issue"></a>Znany problem  
  
> [!NOTE]
>  Istnieje znany problem w Podglądzie zdarzeń, gdzie może nie zdekodować zdarzenia ETW. Zobaczysz komunikat o błędzie, który wygląda podobnie do poniższego.  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  Jeśli wystąpi ten błąd, kliknij przycisk **Odśwież** w okienku Akcje. Zdarzenia powinny teraz poprawnie dekodowane.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
