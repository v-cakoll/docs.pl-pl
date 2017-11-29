---
title: Zaawansowane filtry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a9d7ce5029e0f5b95b98dd4f44e42f6c07bb8e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-filters"></a>Zaawansowane filtry
W przykładzie pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi routingu. Usługa routingu jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składnik, który ułatwia obejmują routerem na podstawie zawartości w aplikacji. W tym przykładzie dostosowuje standardowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbki Kalkulator do komunikowania się przy użyciu usługi routingu. W tym przykładzie pokazano sposób definiowania opartej na zawartości logiki routingu przy użyciu filtrów wiadomości i tabele filtr komunikatu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W poniższej tabeli przedstawiono filtry komunikatów, które są dodawane do tabeli filtru komunikat usługi routingu.  
  
|Filtr|Reguła|Priorytet|  
|------------|----------|--------------|  
|Jeśli (ma nagłówka)|Zaokrąglanie|2|  
|Jeśli (wykazało na Ep2)|Regularne|1|  
|Jeśli (wykazało z 2)|Zaokrąglanie|1|  
|Jeśli (RoundRobin1)|Regularne|0|  
|Jeśli (RoundRobin2)|Zaokrąglanie|0|  
  
 Filtry komunikatów i tabele filtr komunikatu można tworzyć i skonfigurowany za pomocą kodu lub w pliku konfiguracyjnym aplikacji. Dla tego przykładu można znaleźć filtry komunikatów i tabele filtru komunikat zdefiniowany przez kod w pliku RoutingService\routing.cs lub zdefiniowane w pliku konfiguracyjnym aplikacji w pliku RoutingService\App.config. Następuje opisano sposób tworzenia filtry komunikatów i tabele filtr komunikatu dla tego przykładu za pomocą kodu.  
  
 Najpierw <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> szuka nagłówek niestandardowy. Należy pamiętać, że <xref:System.ServiceModel.WSHttpBinding> powoduje wersja schematu envelope przy użyciu protokołu SOAP 1.2, co instrukcji XPath jest zdefiniowany w celu używania przestrzeni nazw protokołu SOAP 1.2. Domyślnego menedżera przestrzeń nazw dla <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s już definiuje prefiksu dla przestrzeni nazw protokołu SOAP 1.2 /s12, którego można użyć. Jednak domyślnego menedżera przestrzeni nazw nie ma niestandardowej przestrzeni nazw, do którego klient używa do definiowania rzeczywistej wartości nagłówka, więc musi być zdefiniowana tego prefiksu. Wiadomości, które zostaną wyświetlone z tym nagłówkiem spełni warunki tego filtru.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 Drugi filtr <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, który dopasowuje dowolny komunikat, który został odebrany w `calculatorEndpoint`. Nazwa punktu końcowego jest definiowany podczas tworzenia obiektu punktu końcowego usługi.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 Trzeci filtr jest <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. To dopasowuje dowolny komunikat, który na punkt końcowy z adresu, który odpowiada prefiks adresu (lub przedniej części) pod warunkiem. W tym przykładzie prefiks adresu jest zdefiniowany jako "http://localhost/routingservice/router/rounding/". Oznacza to, że komunikaty przychodzące, które są opisane na "http://localhost/routingservice/router/rounding/ *" równoważona tego filtru. W takim przypadku jest komunikatów wyświetlanych w punkcie końcowym zaokrąglania Kalkulator, której adres "http://localhost/routingservice/router/rounding/calculator".  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Ostatnie dwa filtry komunikatów są niestandardowe <xref:System.ServiceModel.Dispatcher.MessageFilter>s. W tym przykładzie jest używany filtr komunikatu "RoundRobin". Ten filtr komunikatu jest tworzony w wybrany plik RoutingService\RoundRobinMessageFilter.cs. Te filtry, gdy ustawiono na tej samej grupie przemian raportowania są zgodne wiadomości i czy nie, w taki sposób, że odpowiada tylko jeden z nich `true` naraz.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Następnie wszystkie te wiadomości są dodawane do <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. W ten sposób priorytety podano do wywierania wpływu na kolejność, w którym tabeli filtru komunikatów wykonuje filtrów. Wyższy priorytet, tym szybciej filtr jest wykonywane; tym niższy priorytet, później filtr jest wykonywana. W związku z tym filtrze priorytetem 2 jest uruchamiany przed filtrem priorytetem 1. Domyślny poziom priorytetu, jeśli nie zostanie określona, to 0. Tabela Filtr komunikatu wykonuje wszystkie filtry na poziomie podana wartość priorytetu przed przejściem do następnego najniższy poziom priorytetu. Jeśli dopasowanie znajduje się na określony priorytet, Tabela Filtr komunikatu nie Kontynuuj próby znalezienia dopasowania niższym priorytetem dalej.  
  
> [!NOTE]
>  Gdy w tym przykładzie pokazano, jak korzystać z priorytetów filtr komunikatu, ogólnie jest więcej wydajności i lepsze projektu do projektu i skonfigurować filtry w taki sposób, że nie wymagają priorytetyzacji do poprawnego działania.  
  
 Filtr XPath jest pierwszy filtr w celu dodania i jego priorytetu jest równa 2. Jest to pierwszy filtr komunikatu, która wykonuje. W przypadku odnalezienia niestandardowego nagłówka, niezależnie od tego, co może być wyniki inne filtry: wiadomość jest przesyłana do punktu końcowego Kalkulator zaokrąglania.  
  
 Priorytetem 1 zostaną dodane dwa filtry. Ponownie je uruchomić tylko filtr XPath priorytetem 2 jest niezgodna z komunikatu. Te dwa filtry zawierają dwa różne sposoby, aby określić, gdzie komunikat został skierowany po potem. Ponieważ dwa filtry skutecznie Sprawdź, czy wiadomość dotarła do jednego z dwoma punktami końcowymi, mogły być uruchamiane na tym samym poziomie priorytetu ponieważ są one zwracane nie obie `true` w tym samym czasie.  
  
 Na koniec priorytetem 0 (najniższy priorytet) uruchom RoundRobin komunikatów filtrów. Filtry są skonfigurowane z tej samej nazwie, odpowiada tylko jeden z nich w czasie. Ponieważ trasowanych wszystkie komunikaty z niestandardowego nagłówka i wszystkie osoby skierowane do określonych zwirtualizowanych punktów końcowych, komunikaty obsługiwane przez filtry komunikatów RoundRobin są tylko komunikaty, które zostały skierowane do routera domyślny punkt końcowy bez niestandardowego Nagłówek. Ponieważ te komunikaty, Włącz komunikat dla każdego wywołania, połowy Operacje przejdź do punktu końcowego regularne Kalkulator i drugą przejdź do punktu końcowego Kalkulator zaokrąglania.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AdvancedFilters.sln.  
  
2.  Aby otworzyć **Eksploratora rozwiązań**, wybierz pozycję **Eksploratora rozwiązań** z **widoku** menu.  
  
3.  Naciśnij klawisz F5 lub CTRL + SHIFT + B w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Jeśli chcesz automatyczne uruchamianie niezbędne projektów po naciśnięciu klawisza F5 kliknij rozwiązanie prawym przyciskiem myszy i wybierz **właściwości**. Wybierz **projekt startowy** węźle **wspólne właściwości** w okienku po lewej stronie. Wybierz **wiele projektów startowych** przycisk radiowy i ustaw wszystkie projekty, które mają **Start** akcji.  
  
    2.  W przypadku tworzenia projektu z klawiszy CTRL + SHIFT + B, należy uruchomić następujące aplikacje:  
  
        1.  Kalkulator klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Usługa kalkulatora (. / CalculatorService/bin/service.exe)  
  
        3.  Usługa routingu kalkulatora (. / RoundingCalcService/bin/service.exe)  
  
        4.  Obiektu RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  W oknie konsoli klienta Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta. Klient zwraca listę punktów końcowych docelowego do wyboru.  
  
5.  Wybierz docelowy punkt końcowy, wpisując jego odpowiednich list, a następnie naciśnij klawisz ENTER.  
  
6.  Następnie klient pyta, jeśli chcesz dodać niestandardowy nagłówek. Naciśnij t dla tak lub N nie, naciśnij klawisz ENTER.  
  
7.  W zależności od wyborów dokonanych powinny zostać wyświetlone różne wyniki.  
  
    1.  Poniżej przedstawiono dane wyjściowe zwracane, jeśli niestandardowy nagłówek został dodany do wiadomości.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Poniżej przedstawiono dane wyjściowe zwracane, jeśli została wybrana opcja punkt końcowy zaokrąglania Kalkulator bez niestandardowego nagłówka.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  Poniżej przedstawiono dane wyjściowe zwracane, jeśli została wybrana opcja punkt końcowy regularne Kalkulator bez niestandardowego nagłówka.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  Poniżej przedstawiono dane wyjściowe zwracane, jeśli została wybrana opcja Router domyślny punkt końcowy bez niestandardowego nagłówka.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  Kalkulator usługi oraz zaokrąglania Kalkulator również drukowania dziennika operacji wywoływane w celu ich odpowiednich konsoli systemu windows.  
  
9. W oknie konsoli klienta wpisz `quit` i naciśnij klawisz ENTER, aby wyjść.  
  
10. Naciśnij klawisz ENTER w oknach konsoli usług zakończenie usług.  
  
## <a name="configurable-via-code-or-appconfig"></a>Można konfigurować za pomocą kodu lub pliku App.config  
 Jest skonfigurowany do używania pliku App.config do definiowania zachowania routera dostarczany próbki. Można również zmienić nazwę pliku RoutingService\App.config na inny tak, aby nie został rozpoznany i Usuń komentarz wywołanie metody `ConfigureRouterViaCode()` w RoutingService\routing.cs. Każda z tych metod powoduje takie samo zachowanie z routera.  
  
### <a name="scenario"></a>Scenariusz  
 W tym przykładzie przedstawiono router działająca jako router na podstawie zawartości stosowanie wielu typów lub implementacji usług są dostępne za pośrednictwem jeden punkt końcowy.  
  
### <a name="real-world-scenario"></a>Scenariusz rzeczywistych  
 Firma Contoso chce wszystkie ich usługi do udostępnienia tylko jeden punkt końcowy publicznie za pośrednictwem której zapewniają dostęp do wielu różnych typów usług wirtualizacji. W takim przypadku wykorzystania usługi routingu na podstawie zawartości możliwości routingu ustalenie wysyłania żądań przychodzących.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
