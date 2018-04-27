---
title: Wyodrębnianie danych WF przy użyciu śledzenia
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44e49aa0c9b3b9b53b921fe90838875ab34b7772
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="extract-wf-data-using-tracking"></a>Wyodrębnianie danych WF przy użyciu śledzenia
W tym przykładzie przedstawiono sposób użycia śledzenia można wyodrębnić zmienne przepływu pracy i argumenty z działań przepływu pracy. Przedstawia on także dodawanie adnotacji do śledzenia rekordów i wyodrębniania danych ładunku w rekordach śledzenia niestandardowych. W przykładzie użyto uczestnika śledzenia zdarzeń śledzenia dla systemu Windows (ETW) do wyodrębniania danych z przepływu pracy.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Windows Workflow Foundation (WF) umożliwia śledzenie wgląd we wykonywania wystąpienia przepływu pracy. Środowisko uruchomieniowe śledzenia emituje przepływu pracy śledzenia rekordów podczas wykonywania przepływu pracy. Wraz z przepływu pracy śledzenia rekordy można wyodrębnić danych w wystąpieniu przepływu pracy z przepływu pracy. Poniżej przedstawiono szczegóły typów danych, który może zostać wyodrębniony z śledzenie rekordów:  
  
1.  Zmienne przepływu pracy w ramach działania i śledzenie rekordów podczas wykonywania działania.  
  
     Aby wyodrębnić zmienne przepływu pracy, zmienne, które mają zostać wyodrębnione są określone w profilu. Zmienne, które mają zostać wyodrębnione można określić tylko w przypadku `ActivityStateQueries`. Poniższy przykład kodu pokazuje profil śledzenia używany do wyodrębnienia zmiennej przepływu pracy z działania.  
  
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
  
2.  Argumentów działania i stan działania śledzenia rekordów.  
  
     Argumenty zdefiniować dane sposób przepływów do lub z działania. Argumenty do wyodrębnienia są określane za pomocą <xref:System.Activities.Tracking.ActivityStateQuery>. Poniższy przykładowy kod jest profilu śledzenia, która wyodrębnia `Value` argumentu.  
  
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
  
3.  Adnotacje są pary klucz wartość, które mogą zostać dodane do dowolnego rekordu śledzenia emitowanego.  
  
     Adnotacje służyć jako mechanizmu tagowania śledzenia rekordów. Adnotacje są dodawane do śledzenia rekordów za pomocą profilu śledzenia. Można dodać adnotacje do dowolnego typu zapytania śledzenia przepływu pracy. Poniższy przykładowy kod jest profil śledzenia, który pokazuje, jak można dodać adnotacji do rekordu śledzenia.  
  
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
  
4.  Śledzenie niestandardowych rekordów są emitowane z działań użytkownika.  
  
     Niestandardowe śledzenie rekordów może przenosić dane ładunku zdefiniowane w obrębie tego działania. Subskrypcja dla śledzenia niestandardowych rekordów w profilu śledzenia umożliwia wyodrębnianie ładunku w rekordzie śledzenia. Rejestruje śledzenia niestandardowych można wyodrębnić z niestandardowego <xref:System.Activities.Tracking.TrackingQuery>. Poniższy przykładowy kod jest profilu śledzenia, która wyodrębnia rekord śledzenia niestandardowych wraz z jego ładunku.  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 W przykładzie pokazano wyodrębniania zmiennych, argumenty, niestandardowych rekordów i dodawanie adnotacji przy użyciu profilu określony w pliku Web.config. Włączono śledzenie na przykład usługi przepływu pracy, dodając `<etwTracking>` element zachowania. Poniższy kod umożliwia przykład śledzenie `ExtractWorkflowVariables` profilu śledzenia.  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania WFStockPriceApplication.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
     Oknie przeglądarki zostanie otwarty i zawiera katalog zawierający informacje o aplikacji.  
  
4.  W przeglądarce kliknij przycisk StockPriceService.xamlx.  
  
5.  W przeglądarce pojawi się stronie StockPriceService zawiera Usługa lokalna adres WSDL. Skopiuj ten adres.  
  
     W poniższym przykładzie przedstawiono adres WSDL Usługa lokalna. `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Przed wywołaniem usługi, należy uruchomić Podgląd zdarzeń i upewnij się, że dziennik zdarzeń nasłuchuje śledzenia zdarzeń wyemitowanego z usługi przepływu pracy.  
  
7.  Z **Start** menu, wybierz opcję **narzędzia administracyjne** , a następnie **Podgląd zdarzeń**.  
  
8.  W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, i **Microsoft**. Kliknij prawym przyciskiem myszy **Microsoft** i wybierz **widoku** , a następnie **dzienniki Pokaż analityczne i debugowania**.  
  
     Upewnij się, że **dzienniki Pokaż analityczne i debugowania** zaznaczenia pola wyboru.  
  
9. W widoku drzewa w Podglądzie zdarzeń, przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Włącz dziennik**.  
  
10. Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], otwórz klienta testowego WCF.  
  
     Klienta testowego WCF (WcfTestClient.exe) znajduje się w \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji > \Common7\IDE\ folderu.  
  
     Wartość domyślna [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder instalacji to C:\Program Files\Microsoft Visual Studio 10.0.  
  
11. W kliencie testowym WCF, wybierz **Dodaj usługę** z **pliku** menu.  
  
     Dodaj usługę lokalny adres WSDL, które wcześniej zostały skopiowane w odpowiednim polu.  
  
12. W kliencie testowym WCF, kliknij dwukrotnie `GetStockPrice`.  
  
     Spowoduje to otwarcie `GetStockPrice` metody. Żądanie przyjmuje jeden parametr. Użyj wartości **Contoso**.  
  
13. Kliknij przycisk **wywołania**.  
  
14. Wrócić do podglądu zdarzeń, a następnie przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**,  **Aplikacje serwera aplikacji**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Odśwież**. Identyfikator zakresu 100 – 199 zdarzeń są zdarzenia przepływu pracy.  
  
     Zdarzenia zawierają adnotacje, zmienne, argumentów i śledzenia niestandardowych rekordów, które mogą być wyświetlane w zdarzeniu podglądu.  
  
## <a name="cleaning-up-in-the-event-viewer"></a>Czyszczenie zdarzeń podglądu  
 Kanał danych analitycznych w dzienniku zdarzeń mogą zostać wyczyszczone zdarzeń podglądu w następujący sposób.  
  
#### <a name="to-clean-up-optional"></a>Aby wyczyścić (opcjonalnie)  
  
1.  Otwórz Podgląd zdarzeń.  
  
2.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **wyłączyć dziennika**.  
  
3.  Przejdź do **Podgląd zdarzeń**, **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji Aplikacje serwera**. Kliknij prawym przyciskiem myszy **analityczne** i wybierz **Wyczyść dziennik**.  
  
     Wybierz **wyczyść** opcję, aby wyczyścić zdarzenia.  
  
## <a name="known-issue"></a>Znany problem  
  
> [!NOTE]
>  Istnieje znany problem w Podglądzie zdarzeń, jeżeli nie może zdekodować zdarzenia ETW. Może zostać wyświetlony komunikat błędu, który wygląda następująco.  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  Jeśli wystąpi ten błąd, kliknij przycisk **Odśwież** w okienku Akcje. Zdarzenia powinny teraz dekodowania poprawnie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady monitorowania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
