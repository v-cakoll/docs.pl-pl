---
title: Zaawansowane filtry
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: 7022384e8abe93f4276eec48785b3243ed926438
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042598"
---
# <a name="advanced-filters"></a>Zaawansowane filtry
Niniejszy przykład pokazuje usługi routingu Windows Communication Foundation (WCF). Usługa routingu jest składnikiem usługi WCF, który ułatwia to dołączenie routerem na podstawie zawartości do aplikacji. W tym przykładzie dostosowuje się standardowej próbki Kalkulator WCF do komunikowania się za pomocą usługi routingu. Niniejszy przykład pokazuje jak zdefiniować oparte na zawartości logiki routingu filtry komunikatów i tabele filtr komunikatu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W poniższej tabeli przedstawiono filtry komunikatów, które są dodawane do tabeli filtr komunikatów usługi routingu.  
  
|Filtr|Reguła|Priorytet|  
|------------|----------|--------------|  
|Jeśli (ma nagłówka)|Zaokrąglenie|2|  
|Jeśli (pokazał na Ep2)|Regularne|1|  
|Jeśli (pokazał z 2)|Zaokrąglenie|1|  
|Jeśli (RoundRobin1)|Regularne|0|  
|Jeśli (RoundRobin2)|Zaokrąglenie|0|  
  
 Filtry komunikatów i tabele filtr komunikatu można tworzyć i konfigurować za pomocą kodu lub w pliku konfiguracyjnym aplikacji. W tym przykładzie można znaleźć filtry komunikatów i komunikat filtrowania tabel zdefiniowane przez kod w pliku RoutingService\routing.cs, lub w pliku konfiguracyjnym aplikacji w pliku RoutingService\App.config. Następuje opisują sposób tworzenia filtrów komunikatów i tabele filtr komunikatu dla tego przykładu, za pomocą kodu.  
  
 Po pierwsze, <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> szuka niestandardowego nagłówka. Należy pamiętać, że <xref:System.ServiceModel.WSHttpBinding> skutkuje wersja schematu envelope przy użyciu protokołu SOAP 1.2, co instrukcja języka XPath jest zdefiniowany w celu używania przestrzeni nazw protokołu SOAP 1.2. Menedżer przestrzeni nazw domyślny dla <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s już definiuje prefiks przestrzeni nazw protokołu SOAP 1.2 /s12, który może być używany. Domyślny Menedżer przestrzeni nazw nie ma jednak niestandardowej przestrzeni nazw, aby zdefiniować rzeczywistej wartości nagłówka, więc musi być zdefiniowany tego prefiksu używanego przez klienta. Każdy komunikat o pojawia się z tym nagłówkiem pasuje do tego filtru.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 Drugi filtr <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, który dopasowuje każdy komunikat, który został odebrany w `calculatorEndpoint`. Nazwa punktu końcowego jest zdefiniowany, gdy tworzony jest obiekt punktu końcowego usługi.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 Trzeci filtr jest <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. Odpowiada to wszystkie komunikaty, które pojawiło się w punkcie końcowym za pomocą adresu, który dopasowuje ciąg prefiksu adresu (lub pierwszej części), pod warunkiem. W tym przykładzie prefiksu adresu jest zdefiniowany jako "http://localhost/routingservice/router/rounding/". Oznacza to, że wiadomości przychodzących, które są skierowane do "http://localhost/routingservice/router/rounding/*" są dopasowane przez ten filtr. W tym przypadku jest wiadomości, które pojawiają się w punkcie końcowym zaokrąglania Kalkulator, który ma adres "http://localhost/routingservice/router/rounding/calculator".  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Ostatnie dwa filtry komunikatów są niestandardowe <xref:System.ServiceModel.Dispatcher.MessageFilter>s. W tym przykładzie jest używany filtr komunikatu "RoundRobin". Ten filtr komunikatu jest tworzony w podanego pliku RoutingService\RoundRobinMessageFilter.cs. Te filtry po ustawieniu tej samej grupie zamiennie raportowania są zgodne wiadomości i że tak nie jest, w taki sposób, że tylko jeden z nich odpowiada `true` w danym momencie.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Następnie wszystkie te komunikaty są dodawane do <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. W ten sposób priorytety są określane w celu wywierania wpływu na kolejność, w którym tabeli filtr komunikatów wykonuje filtry. Wyższy priorytet, tym szybciej filtru jest wykonywana. tym niższy priorytet, później filtru jest wykonywany. Dlatego filtr o priorytecie 2 jest uruchamiany przed filtr priorytetem 1. Domyślny poziom priorytetu, jeśli nie określono to 0. Tabela filtr komunikatów wykonuje wszystkie filtry na poziomie podana wartość priorytetu przed przejściem do następnego najniższy poziom priorytetu. Jeśli zostanie znalezione dopasowanie z określonym priorytetem, następnie tabeli filtr komunikatów nie będzie próby znalezienia dopasowania z niższym priorytetem dalej.  
  
> [!NOTE]
>  Chociaż w tym przykładzie pokazano, jak używać priorytety filtr komunikatów, ogólnie rzecz biorąc jest wydajniej i lepsze projektu do projektu i skonfigurować filtry w taki sposób, że nie wymagają priorytetów do poprawnego działania.  
  
 Pierwszy filtr w celu dodania jest filtr XPath i jego priorytet jest równa 2. Jest to pierwszy filtr komunikatów, który jest wykonywany. Jeśli znajdzie niestandardowy nagłówek, niezależnie od tego, jakie wyniki inne filtry byłyby, komunikat jest kierowany do endpoint zaokrąglania Kalkulator.  
  
 Priorytetem 1 są dodawane dwa filtry. Ponownie je uruchomić tylko filtr XPath o priorytecie 2 jest niezgodna z wiadomości. Te dwa filtry pokazano dwa różne sposoby, aby określić, gdzie komunikat został skierowany, gdy zostało wyświetlone. Ponieważ dwa filtry skutecznie Sprawdź, czy wiadomość dotarła do jednego z dwóch punktów końcowych, mogły być uruchamiane na tym samym poziomie priorytetu ponieważ robią nie oba zwrócenia `true` w tym samym czasie.  
  
 Na koniec priorytetem 0 (najniższy priorytet) uruchom RoundRobin komunikatu filtrów. Filtry są skonfigurowane przy użyciu tej samej nazwy grupy, tylko jeden z nich odpowiada w danym momencie. Ponieważ trasowanych wszystkie komunikaty z niestandardowego nagłówka, a wszystkie te skierowane do określonych zwirtualizowanych punktów końcowych, komunikaty obsługiwane przez filtry komunikatów RoundRobin są tylko komunikaty, które zostały opisane na domyślny punkt końcowy routera bez niestandardowego Nagłówek. Ponieważ te komunikaty przełączyć się na wiadomości dla każdego wywołania, połowę operacji, przejdź do punktu końcowego kalkulatora regularne a druga połowa do punktu końcowego zaokrąglania Kalkulator.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AdvancedFilters.sln.  
  
2.  Aby otworzyć **Eksploratora rozwiązań**, wybierz opcję **Eksploratora rozwiązań** z **widoku** menu.  
  
3.  W programie Visual Studio naciśnij klawisz F5 lub CTRL + SHIFT + B.  
  
    1.  Jeśli chcesz automatycznie uruchomić projektów konieczne po naciśnięciu klawisza F5, kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz **właściwości**. Wybierz **projekt startowy** węźle **wspólne właściwości** w okienku po lewej stronie. Wybierz **wiele projektów startowych** przycisk radiowy, a następnie ustaw wszystkie projekty, które mają **Start** akcji.  
  
    2.  Jeśli tworzysz projekt za pomocą klawiszy CTRL + SHIFT + B, należy uruchomić następujące aplikacje:  
  
        1.  Kalkulator klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Kalkulator usługi (. / CalculatorService/bin/service.exe)  
  
        3.  Usługa routingu Kalkulator (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  W oknie konsoli klienta Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta. Klient zwraca listę docelowych punktów końcowych do wyboru.  
  
5.  Wybierz docelowy punkt końcowy, wpisując jego odpowiedniego literą, a następnie naciśnij klawisz ENTER.  
  
6.  Następnie klient pyta, czy chcesz dodać niestandardowy nagłówek. Naciśnij klawisz Y dla tak lub N nie, naciśnij klawisz ENTER.  
  
7.  W zależności od dokonanych wyborów powinien zostać wyświetlony różnych danych wyjściowych.  
  
    1.  Poniżej przedstawiono, że dane wyjściowe zwrócone, jeśli nagłówka niestandardowego jest dodawany do wiadomości.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Poniżej przedstawiono, że dane wyjściowe zwrócone, jeśli została wybrana opcja punkt końcowy zaokrąglania Kalkulator, bez nagłówka niestandardowego.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  Poniżej przedstawiono, że dane wyjściowe zwrócone, jeśli została wybrana opcja punkt końcowy kalkulatora regularne bez nagłówka niestandardowego.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  Poniżej przedstawiono, że dane wyjściowe zwrócone, jeśli wybrano domyślny routera punkt końcowy bez nagłówka niestandardowego.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  Kalkulator usługi i zaokrąglania Kalkulator również drukowania dziennika operacji wywoływane w celu ich odpowiedniej konsoli systemu windows.  
  
9. W oknie konsoli klienta wpisz `quit` i naciśnij klawisz ENTER, aby zakończyć.  
  
10. Naciśnij klawisz ENTER w oknach konsoli usług do zakończenia usługi.  
  
## <a name="configurable-via-code-or-appconfig"></a>Można konfigurować za pomocą kodu lub pliku App.config  
 Dostarczany próbki, skonfigurowany do używania pliku App.config do definiowania zachowania routera. Możesz również zmienić nazwę pliku RoutingService\App.config się czymś innym, tak, aby nie został rozpoznany i usuń znaczniki komentarza wywołania metody, które ma `ConfigureRouterViaCode()` w RoutingService\routing.cs. Każda z tych metod powoduje takie samo zachowanie z routera.  
  
### <a name="scenario"></a>Scenariusz  
 Niniejszy przykład demonstruje routerze działającego jako router opartego na zawartości, dzięki czemu wielu typów lub implementacji usług są dostępne za pośrednictwem punktów końcowych.  
  
### <a name="real-world-scenario"></a>Scenariusz rzeczywistych  
 Firma Contoso chce wszystkich swoich usług, aby uwidocznić tylko jeden punkt końcowy publicznie za pomocą którego oferują dostęp do wielu różnych typów usług wirtualizacji. W tym przypadku skorzystają z usługą routingu opartego na zawartości możliwości routingu w celu określenia, gdzie mają być wysyłane żądania przychodzące.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
