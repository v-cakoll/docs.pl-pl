---
title: Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: c54585ab8e9d9fc039858b07ab75068e984b78db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594814"
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów
W tym temacie opisano format danych śledzenia, jak wyświetlać i metod, które umożliwiają rozwiązywanie problemów z aplikacji przeglądarki danych śledzenia usługi.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Za pomocą narzędzia podglądu śledzenia usług  
 Narzędzie przeglądarki danych śledzenia usługi Windows Communication Foundation (WCF) ułatwia korelowanie dane śledzenia diagnostycznego produkowane przez odbiorniki WCF, aby znaleźć przyczynę błędu. Narzędzie umożliwia łatwe przeglądanie i grupy, i filtrować dane śledzenia, aby zdiagnozować, napraw i sprawdź problemów w przypadku usług WCF. Aby uzyskać więcej informacji dotyczących używania tego narzędzia, zobacz [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Ten temat zawiera zrzuty ekranu przedstawiające śledzenie wygenerowane przez uruchomienie [śledzenia i rejestrowania komunikatów](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) przykładowy, gdy wyświetlany w przeglądarce [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). W tym temacie przedstawiono zrozumienie zawartości śledzenia, działań i ich korelacji i analizowania dużych ilości danych śledzenia, podczas rozwiązywania problemów.  
  
## <a name="viewing-trace-content"></a>Wyświetlanie zawartości śledzenia  
 Zdarzenia śledzenia zawiera następujące najważniejsze informacje:  
  
-   Nazwa działania po ustawieniu.  
  
-   Czas emisji.  
  
-   Poziom śledzenia.  
  
-   Nazwa źródła śledzenia.  
  
-   Nazwa procesu.  
  
-   Identyfikator wątku.  
  
-   Identyfikator unikatowy śledzenia, czyli adres URL, który wskazuje na lokalizację docelową w Docs firmy Microsoft, z którego można uzyskać więcej informacji dotyczących śledzenia.  
  
 Wszystkie te są widoczne w górnym prawym panelu w podglądzie śledzenia usługi lub **podstawowe informacje** sekcji w widoku sformatowane prawego dolnego panelu po wybraniu śledzenia.  
  
> [!NOTE]
>  Jeśli klienta i usługi znajdują się na tym samym komputerze, danych śledzenia dla obu aplikacji będą obecne. Te można filtrować przy użyciu **nazwy procesu** kolumny.  
  
 Ponadto sformatowane widok zawiera również opis dla śledzenia i dodatkowe informacje szczegółowe, jeśli jest dostępna. One może obejmować wyjątek typu i komunikat stosy wywołań wiadomości działania, od/do pól i inne informacje o wyjątku.  
  
 W widoku XML tagi xml przydatne następujące:  
  
-   `<SubType>` (poziom śledzenia).  
  
-   `<TimeCreated>`.  
  
-   `<Source>` (nazwa źródła śledzenia).  
  
-   `<Correlation>` (identyfikator działania ustawione podczas emitowania śledzenia).  
  
-   `<Execution>` (identyfikator procesu i wątku).  
  
-   `<Computer>`.  
  
-   `<ExtendedData>`, w tym `<Action>`, `<MessageID>` i `<ActivityId>` ustawiony w nagłówku komunikatu podczas wysyłania komunikatu.  
  
 Jeśli możesz zbadać śledzenia "Wysłano wiadomość w kanale", mogą pojawić się następującą zawartością.  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
   <System xmlns="http://schemas.microsoft.com/2004/06/windows/eventlog/system">  
      <EventID>262163</EventID>  
      <Type>3</Type>  
      <SubType Name="Information">0</SubType>  
      <Level>8</Level>  
      <TimeCreated SystemTime="2006-08-04T18:45:30.8491051Z" />  
      <Source Name="System.ServiceModel" />  
       <Correlation ActivityID="{27c6331d-8998-43aa-a382-03239013a6bd}"/>  
       <Execution ProcessName="client" ProcessID="1808" ThreadID="1" />  
       <Channel />  
       <Computer>TEST1</Computer>  
   </System>  
   <ApplicationData>  
       <TraceData>  
          <DataItem>  
             <TraceRecord xmlns="http://schemas.microsoft.com/2004/10/E2ETraceEvent/TraceRecord" Severity="Information">  
                 <TraceIdentifier>http://msdn.microsoft.com/library/System.ServiceModel.Channels.MessageSent.aspx</TraceIdentifier>  
                 <Description>Sent a message over a channel.</Description>  
                 <AppDomain>client.exe</AppDomain>  
                 <Source>System.ServiceModel.Channels.ClientFramingDuplexSessionChannel/35191196</Source>  
                <ExtendedData xmlns="http://schemas.microsoft.com/2006/08/ServiceModel/MessageTransmitTraceRecord">  
  
                  <MessageProperties>  
                     <AllowOutputBatching>False</AllowOutputBatching>  
                  </MessageProperties>  
                  <MessageHeaders>  
                     <Action d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">http://Microsoft.ServiceModel.Samples/ICalculator/Multiply</Action>  
                     <MessageID xmlns="http://www.w3.org/2005/08/addressing">urn:uuid:7c6670d8-4c9c-496e-b6a0-2ceb6db35338</MessageID>  
                     <ActivityId CorrelationId="b02e2189-0816-4387-980c-dd8e306440f5" xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">27c6331d-8998-43aa-a382-03239013a6bd</ActivityId>  
                     <ReplyTo xmlns="http://www.w3.org/2005/08/addressing">  
                        <Address>http://www.w3.org/2005/08/addressing/anonymous</Address>  
                    </ReplyTo>  
                    <To d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">net.tcp://localhost/servicemodelsamples/service</To>  
                  </MessageHeaders>  
                  <RemoteAddress>net.tcp://localhost/servicemodelsamples/service</RemoteAddress>  
                </ExtendedData>  
            </TraceRecord>  
          </DataItem>  
       </TraceData>  
   </ApplicationData>  
</E2ETraceEvent>  
```  
  
## <a name="servicemodel-e2e-tracing"></a>ServiceModel E2E Tracing  
 Gdy `System.ServiceModel` źródła śledzenia została ustawiona za pomocą `switchValue` inny niż wyłączona, i `ActivityTracing`, tworzy WCF, działań i przesyłania do przetwarzania WCF.  
  
 Działanie to jednostka logiczna przetwarzania, czy grupy wszystkie ślady związane z tej jednostki. Na przykład można zdefiniować jedno działanie dla każdego żądania. Transfery Utwórz przyczynowego między działaniami w obrębie punktów końcowych. Propagowanie identyfikator działania umożliwia są ze sobą powiązane działania w obrębie punktów końcowych. Można to zrobić, ustawiając `propagateActivity` = `true` w konfiguracji w każdym punkcie końcowym. Działania, transfery i propagację umożliwiają wykonywanie korelacji błędu. W ten sposób można znaleźć przyczynę błędu szybciej.  
  
 Z poziomu klienta jednym działaniem WCF jest tworzony dla każdego wywołania modelu obiektu (na przykład, otwartego elementu ChannelFactory, Dodaj, dzielenie i itd.) Każdego wywołania operacji są przetwarzane w działaniu "Action procesu".  
  
 Poniższy zrzut ekranu wyodrębnione z [śledzenia i rejestrowania komunikatów](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) przykładowe panelu po lewej stronie wyświetlana jest lista działań utworzonych w procesie klienta, posortowane według czasu utworzenia. Oto chronologiczną listę działań:  
  
-   Tworzona fabryka kanałów (element ClientBase).  
  
-   Otworzyć fabryki kanałów.  
  
-   Przetwarzane Dodaj akcję.  
  
-   Skonfiguruj zabezpieczenia sesji (ta WYSTĄPIŁ na pierwsze żądanie) i infrastruktura przetwarzania trzy zabezpieczeń wiadomości odpowiedzi: RST, RSTR, SCT (proces komunikat 1, 2, 3).  
  
-   Przetworzone odejmowanie, mnożenie i dzielenie żądań.  
  
-   Zamknięte fabryki kanałów i sposób zamknięcia sesji przez bezpieczne i przetwarzane odpowiedź komunikatu zabezpieczeń Anuluj.  
  
 Widzimy komunikatów infrastruktura zabezpieczeń ze względu na powiązanie wsHttpBinding.  
  
> [!NOTE]
>  W programie WCF, pokazujemy wiadomości odpowiedzi początkowo przetwarzanych w oddzielnych działania (proces komunikat) przed możemy skorelować do odpowiadającego im działania akcji procesu, który zawiera komunikat żądania, w ramach transferu. To się dzieje w przypadku infrastruktury komunikatów i żądań asynchronicznych a wynika z faktu, że firma Microsoft musi sprawdzanie wiadomości, odczytać nagłówka activityId i zidentyfikować istniejące działania procesu akcji o takim identyfikatorze skorelować do niego. Dla żądań synchronicznych firma Microsoft blokują dla odpowiedzi, a więc wiedzieć, jaka akcja proces odpowiedzi odnosi się do.  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace4.gif "e2eTrace4")  
Godzina utworzenia (panelu po lewej stronie) i ich zagnieżdżonych działań i ślady (w górnym prawym panelu) na liście działania klienta WCF  
  
 Gdy wybierzemy działania w panelu po lewej stronie widać zagnieżdżonych działań i dane śledzenia w górnym prawym panelu. Dlatego jest obniżona hierarchiczny widok Lista działań związanych z lewej strony, na podstawie wybranej nadrzędnej działania. Ponieważ wybranej akcji procesu Dodaj pierwszego żądania wprowadzone, to działanie zawiera działanie Ustaw się zabezpieczyć sesji (przesyłanie danych do przeniesienia powrót po awarii z) i śledzi w celu przetwarzania rzeczywiste Dodaj akcję.  
  
 Kliknij dwukrotnie działanie procesu działania Dodaj w lewym panelu, widać graficzną reprezentację działania WCF klienta, które są związane z Dodaj. Pierwsze działanie po lewej stronie jest działania głównego (0000), który jest domyślne działanie. Transfery WCF ze otoczenia działania. Jeśli to nie jest zdefiniowany, WCF przesyła poza 0000. W tym miejscu drugiego działania, przetwórz operację dodawania akcji, przesyła poza 0. Wtedy wyświetlone ustawienia zabezpieczenia sesji.  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace5.gif "e2eTrace5")  
Widok wykresu działania klienta WCF: Otoczenia działania (tutaj 0), działanie procesu oraz ustawić się Secure sesję  
  
 W górnym prawym panelu widać wszystkie ślady dotyczące działań Przetwórz operację dodawania akcji. W szczególności firma Microsoft ma wysłała komunikat żądania ("Wysłano wiadomość w kanale") i odebrał odpowiedź ("Odebrano wiadomość w kanale"), w ramach tego samego działania. Jest to pokazane na poniższym wykresie. W celu uściślenia Konfigurowanie aktywność sesji bezpiecznego jest zwinięte na wykresie.  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace6.gif "e2eTrace6")  
Lista śledzenia dla działania procesu akcji: możemy wysłać żądanie i otrzymywać odpowiedzi w ramach tego samego działania.  
  
 W tym miejscu możemy załadować śladów klienta tylko w celu uściślenia, ale śladów usługi (Odebrano komunikat żądania i odpowiedzi wiadomością wysłaną) pojawić się w tym samym działaniu, jeśli one również są ładowane w narzędziu i `propagateActivity` została ustawiona na `true.` przedstawiono na ilustracji nowsze.  
  
 W usłudze modelu działania mapuje do koncepcji usługi WCF w następujący sposób:  
  
1.  Firma Microsoft może utworzyć, a następnie otwórz ServiceHost (może to spowodować kilka działań związanych z hostem, na przykład w przypadku zabezpieczeń).  
  
2.  Tworzymy nasłuchiwania na działanie dla każdego odbiornik elementu ServiceHost (z przesyłania do i z otwartego elementu ServiceHost).  
  
3.  Jeśli odbiornik wykryje żądanie komunikacji zainicjowane przez klienta, przesyłania czynnością "Bajtów otrzymywać" w jakiej są przetwarzane wszystkie bajtów wysłanych z klienta. W przypadku tego działania widać błędów połączenia, które wystąpiło podczas interakcji z usługi klienta.  
  
4.  Dla każdego zestawu bajtów, które zostanie odebrana, umożliwiająca wiadomość możemy przetworzyć tych bajtów w działaniu "Procesu komunikat", gdzie możemy utworzyć obiekt komunikatów WCF. W przypadku tego działania widzimy błędy związane z koperty nieprawidłowy lub uszkodzony komunikat.  
  
5.  Gdy komunikat jest sformułowany, możemy przenieść do działania procesu akcji. Jeśli `propagateActivity` ustawiono `true` na klienta i usługi, to działanie ma ten sam identyfikator jak wartość zdefiniowana w kliencie i opisem w poprzedniej sekcji. Z tego etapu Zaczniemy do korzystania z bezpośrednia korelacja między punktami końcowymi, ponieważ wszystkie dane śledzenia emitowane w programie WCF that are related to żądanie znajdują się w tej samej działania, w tym przetwarzanie komunikatów odpowiedzi.  
  
6.  Dla akcji poza procesem możemy utworzyć aktywności "Wykonywanie kodu użytkownika" do izolowania danych śledzenia emitowane w kodzie użytkownika z tymi emitowane w programie WCF. W poprzednim przykładzie śledzenia "Usługa wysyła odpowiedź Dodaj" w działaniu "Użytkownika wykonaj kod" w aktywności propagowane przez klienta, nie jest emitowane, jeśli ma to zastosowanie.  
  
 Na ilustracji poniżej pierwsze działanie po lewej stronie jest działania głównego (0000), który jest domyślne działanie. Następne trzy działania są można otworzyć elementu ServiceHost. Działanie w kolumnie 5 jest odbiornik i pozostałych działań (od 6 do 8) opisano WCF przetwarzania wiadomości w bajtach przetwarzania aktywację kodu użytkownika.  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace7.gif "e2eTrace7")  
Listę działań usługi WCF  
  
 Poniższy zrzut ekranu przedstawia działania dla klienta i usługi i prezentuje działanie Przetwórz operację dodawania akcji między procesami (kolor pomarańczowy). Strzałki komunikatów żądań i odpowiedzi wysyłane i odbierane przez klienta i usługi są ze sobą powiązane. Ślady działania procesu są rozdzielane między procesami na wykresie, ale widoczne jako część tego samego działania w prawym górnym rogu panelu. W tym panelu widać ślady klienta dla wysłanych komunikatów, następuje śladów usługi odebranych i przetworzonych komunikatów.  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace8.gif "e2eTrace8")  
Widok wykresu obu działań klienta i usługi WCF  
  
 W poniższym scenariuszu błąd błąd i zapisy ostrzeżeń na usługi i klienta są powiązane. Najpierw jest zgłaszany wyjątek w kodzie użytkownika w usłudze (najdalej z prawej strony działania zielony, który obejmuje Ostrzeżenie śledzenia dla wyjątku "Usługa nie może przetworzyć tego żądania, w kodzie użytkownika."). Gdy odpowiedź jest wysyłana do klienta, śledzenia ostrzeżenie ponownie jest emitowany do oznaczania komunikat o błędzie (po lewej stronie różowy działanie). Klient następnie zamyka jego klienta WCF (żółty działanie po stronie lewej dolnej), który przerywa połączenie z usługą. Usługa zgłasza błąd (najdłuższy różowy działanie po prawej stronie).  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Korelowanie błąd usługi i klienta  
  
 Przykładowy służący do generowania ślady te to seria żądań synchronicznych przy użyciu powiązanie wsHttpBinding. Brak odchyleń od tego wykresu dla scenariuszy bez zabezpieczeń lub za pomocą żądań asynchronicznych, gdy działanie procesu akcji obejmuje operacje rozpoczęcia i zakończenia, wchodzących w skład wywołania asynchronicznego i pokazuje transferu dla działania wywołania zwrotnego. Aby uzyskać więcej informacji na temat dodatkowych scenariuszach, zobacz [scenariuszy śledzenia End-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## <a name="troubleshooting-using-the-service-trace-viewer"></a>Rozwiązywanie problemów przy użyciu przeglądarki danych śledzenia usługi  
 Podczas ładowania plików śledzenia w narzędziu Podgląd śledzenia usługi można wybrać wszelkich czerwony threshold lub Yellow threshold działań w panelu po lewej stronie, aby Śledzenie przyczyny problemu w aplikacji. Zazwyczaj 000 działanie ma nieobsługiwany wyjątki, które będą się pojawiać do użytkownika.  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace10.gif "e2eTrace10")  
Wybierając czerwoną threshold lub Yellow threshold działania Znajdź główny problem  
  
 W górnym prawym panelu można sprawdzić ślady działania, które wybrano po lewej stronie. Następnie można badać ślady czerwony threshold lub Yellow Threshold w panelu i zobacz, jak są skorelowane. Na poprzednim wykresie widzimy zapisy ostrzeżeń, zarówno dla klienta i usługi, w tym samym działaniu działania procesu.  
  
 Jeśli ślady te nie zawierają główną przyczynę tego błędu, możesz użyć wykresu przez dwukrotne kliknięcie wybrane działanie w panelu po lewej stronie (tutaj procesu akcji). Następnie jest wyświetlany wykres z powiązanych działań. Powstałą powiązanych działań (klikając znaki "+") można znaleźć pierwszego emitowany śledzenia na czerwono lub powiązana aktywność na żółto. Zachowaj rozszerzania działania, które miały tuż przed czerwony threshold lub Yellow threshold ślad zainteresowaniach, aplikację po przekazaniu powiązanych działań lub przepływów wiadomości między punktami końcowymi, dopóki śledzenie głównej przyczyny problemu.  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Rozwijanie działania śledzenia głównej przyczyny problemu  
  
 Jeśli ServiceModel `ActivityTracing` jest wyłączony, ale ServiceModel śledzenia jest włączona, możesz zobaczyć ServiceModel śledzenia emitowane w działaniu 0000. Jednak wymaga więcej wysiłku w zrozumienie korelację ślady te.  
  
 Po włączeniu rejestrowania komunikatów można użyć karta wiadomość, aby wyświetlić komunikat, który jest wpływ ten błąd. Dwukrotne kliknięcie komunikatu na czerwono lub żółty, możesz zobaczyć w widoku wykresu powiązanych działań. Te działania są najbardziej związane z żądaniem gdzie wystąpił błąd.  
  
 ![Używanie przeglądarki danych śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace11.gif "e2eTrace11")  
Aby rozpocząć rozwiązywanie problemów, możesz również wybierz czerwony threshold lub Yellow threshold komunikat śledzenia i dwukrotnie kliknij go, aby śledzić głównej przyczyny  
  
## <a name="see-also"></a>Zobacz także
- [Scenariusze kompleksowego śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
