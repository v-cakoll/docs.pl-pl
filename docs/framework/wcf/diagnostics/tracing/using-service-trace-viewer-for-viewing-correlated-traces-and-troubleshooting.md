---
title: Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: e1cd1443e96e7195127cb95e7ef1b2c4d6d9c176
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587758"
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów

W tym temacie opisano format danych śledzenia, sposób ich wyświetlania oraz podejścia do rozwiązywania problemów z aplikacją przy użyciu przeglądarki śledzenia usługi.

## <a name="using-the-service-trace-viewer-tool"></a>Korzystanie z narzędzia Podgląd śledzenia usług

Narzędzie Podgląd śledzenia usługi Windows Communication Foundation (WCF) ułatwia skorelowanie śladów diagnostycznych generowanych przez odbiorniki WCF w celu zlokalizowania głównej przyczyny błędu. Narzędzie umożliwia łatwe wyświetlanie, grupowanie i filtrowanie śladów, co umożliwia diagnozowanie, naprawianie i weryfikowanie problemów z usługami WCF. Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [narzędzie Podgląd śledzenia usług (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md).

Ten temat zawiera zrzuty ekranu przedstawiające ślady generowane przez uruchomienie [śledzenia i przykładowego rejestrowania komunikatów](../../samples/tracing-and-message-logging.md) , gdy jest wyświetlany za pomocą [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md). W tym temacie pokazano, jak zrozumieć zawartość śledzenia, działania i ich korelację oraz jak analizować dużą liczbę śladów podczas rozwiązywania problemów.

## <a name="viewing-trace-content"></a>Wyświetlanie zawartości śledzenia

Zdarzenie śledzenia zawiera następujące najbardziej znaczące informacje:

- Nazwa działania po ustawieniu.

- Czas emisji.

- Poziom śledzenia.

- Nazwa źródła śledzenia.

- Nazwa procesu.

- Identyfikator wątku.

- Unikatowy identyfikator śledzenia, który jest adresem URL wskazującym miejsce docelowe w Microsoft Docs, z którego można uzyskać więcej informacji dotyczących śledzenia.

 Wszystkie te informacje mogą być widoczne w prawym górnym panelu w podglądzie śledzenia usług lub w sekcji **Informacje podstawowe** w formacie widoku w prawym dolnym rogu w przypadku wybrania śledzenia.

> [!NOTE]
> Jeśli klient i usługa znajdują się na tym samym komputerze, będą widoczne ślady obu aplikacji. Można je filtrować przy użyciu kolumny **Nazwa procesu** .

Ponadto sformatowany widok zawiera również opis śledzenia i dodatkowe szczegółowe informacje, jeśli są dostępne. Ten ostatni może obejmować typ wyjątku i komunikat, stosy wywołań, akcję komunikatu, od/do pól oraz inne informacje o wyjątku.

W widoku XML przydatne są następujące tagi XML:

- `<SubType>`(poziom śledzenia).

- `<TimeCreated>`.

- `<Source>`(nazwa źródła śledzenia).

- `<Correlation>`(identyfikator działania ustawiany podczas emitowania śladu).

- `<Execution>`(proces i identyfikator wątku).

- `<Computer>`.

- `<ExtendedData>`, `<Action>` w tym `<MessageID>` i `<ActivityId>` zestaw w nagłówku wiadomości podczas wysyłania komunikatu.

Jeśli przebadasz ślad "wysłano komunikat za pośrednictwem kanału", zobaczysz poniższą zawartość.

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

## <a name="servicemodel-e2e-tracing"></a>E2E — śledzenie

Gdy `System.ServiceModel` Źródło śledzenia jest ustawione na wartość `switchValue` inne niż wyłączone, a `ActivityTracing` program WCF tworzy działania i transfery do przetwarzania WCF.

Działanie jest jednostką logiczną przetwarzania, która grupuje wszystkie ślady związane z tą jednostką przetwarzania. Na przykład można zdefiniować jedno działanie dla każdego żądania. Transfery tworzą związek przyczyn między działaniami w punktach końcowych. Propagowanie identyfikatora działania pozwala powiązać działania między punktami końcowymi. Można to zrobić, ustawiając `propagateActivity` = `true` konfigurację w każdym punkcie końcowym. Działania, transfery i Propagacja umożliwiają przeprowadzenie korelacji błędów. W ten sposób można szybciej znaleźć główną przyczynę błędu.

Na kliencie jedno działanie WCF jest tworzone dla każdego wywołania modelu obiektu (na przykład Otwórz element ChannelFactory, Dodaj, Podziel itd.) Każde wywołanie operacji jest przetwarzane w działaniu "proces działania".

Na poniższym zrzucie ekranu wyodrębnionym z przykładu [śledzenie i rejestrowanie komunikatów](../../samples/tracing-and-message-logging.md) w lewym panelu wyświetla listę działań utworzonych w procesie klienta posortowanych według czasu utworzenia. Poniżej znajduje się lista działań chronologicznych:

- Konstruowanie fabryki kanałów (ClientBase).

- Otwarto fabrykę kanałów.

- Przetworzono akcję Dodaj.

- Skonfiguruj bezpieczną sesję (podczas pierwszego żądania) i przetworzono trzy komunikaty odpowiedzi infrastruktury zabezpieczeń: RST, RSTR, SCT (proces Message 1, 2, 3).

- Przetworzono żądania odejmowania, mnożenia i dzielenia.

- Zamknięto fabrykę kanałów i spowoduje to zamknięcie bezpiecznej sesji i przetworzenie odpowiedzi na komunikat zabezpieczeń.

 W związku z wsHttpBinding widzimy komunikaty infrastruktury zabezpieczeń.

> [!NOTE]
> W programie WCF pokazujemy, że komunikaty odpowiedzi są przetwarzane początkowo w oddzielnym działaniu (komunikat procesu), zanim zostaną skorelowane z odpowiednimi działaniami akcji procesu, które obejmują komunikat żądania, za pomocą transferu. Dzieje się tak w przypadku komunikatów infrastruktury i żądań asynchronicznych. jest to spowodowane faktem, że musimy sprawdzić komunikat, odczytać nagłówek activityId i zidentyfikować istniejące działanie akcji procesu z tym identyfikatorem w celu skorelowania z nim. W przypadku żądań synchronicznych blokujemy odpowiedź i w związku z tym wiesz, z jaką akcją procesu odnosi się odpowiedź.

Na poniższej ilustracji przedstawiono działania klienta WCF wymienione według czasu utworzenia (lewy panel) i ich zagnieżdżone działania i ślady (prawy panel):

![Zrzut ekranu przedstawiający działania klienta WCF wymienione przez czas utworzenia.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-activities-creation-time.gif)

Po wybraniu działania w lewym panelu zobaczymy działania zagnieżdżone i ślady w prawym górnym panelu. W związku z tym jest to skrócony hierarchiczny widok listy działań po lewej stronie w oparciu o wybrane działanie nadrzędne. Ponieważ wybrana akcja procesu Dodaj to pierwsze żądanie, to działanie zawiera konfigurację bezpiecznego działania sesji (transfer do, transfer z powrotem z) i ślady dla rzeczywistego przetwarzania akcji Dodaj.

Po dwukrotnym kliknięciu akcji proces Dodaj działanie w lewym panelu zobaczysz graficzną reprezentację działań WCF klienta związanych z dodawaniem. Pierwsze działanie po lewej stronie to działanie główne (0000), które jest działaniem domyślnym. Usługa WCF transferuje poza działanie otoczenia. Jeśli ta funkcja nie jest zdefiniowana, usługa WCF transferuje z 0000. W tym miejscu druga aktywność, proces działania procesu, transfer wyniesie z 0. Następnie zostanie wyświetlona bezpieczna sesja Instalatora.

Na poniższej ilustracji przedstawiono widok wykresu działań klienta WCF, w tym tutaj działanie otoczenia (0), akcję procesu i konfigurację bezpiecznej sesji:

![Wykres w podglądzie śledzenia przedstawiający działanie otoczenia i działania procesu.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-activities-graph-ambient-process.gif)

W prawym górnym panelu można zobaczyć wszystkie ślady związane z akcją proces Dodaj działanie. W odniesieniu do tego samego działania wysłaliśmy komunikat z żądaniem ("wysłano wiadomość w kanale") i odebrano odpowiedź ("Odebrano wiadomość kanałem"). Jest to pokazane na poniższym wykresie. Dla jasności działanie Skonfiguruj bezpieczną sesję jest zwinięte na wykresie.

Na poniższej ilustracji przedstawiono listę śladów działania procesu działania. Wysyłamy żądanie i odbieramy odpowiedź w tym samym działaniu.

![Zrzut ekranu podglądu śledzenia przedstawiający listę śladów działania procesu działania](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/process-action-traces.gif)

W tym miejscu ładujemy dane śledzenia klienta tylko do przejrzystości, ale ślady usługi (odebrany komunikat żądania i wysłano komunikat odpowiedzi) pojawiają się w tym samym działaniu, jeśli są one również załadowane w narzędziu i `propagateActivity` zostały ustawione na `true.` w dalszej części rysunku.

W usłudze Model aktywności jest mapowany na koncepcje programu WCF w następujący sposób:

1. Tworzymy i otwieramy ServiceHost (może to spowodować utworzenie kilku działań związanych z hostem, na przykład w przypadku zabezpieczeń).

2. Tworzymy nasłuchiwanie działania dla każdego odbiornika w ServiceHost (z transferami z i z otwartego ServiceHost).

3. Gdy odbiornik wykryje żądanie komunikacji zainicjowane przez klienta, przesyła do działania "odbierane bajty", w którym są przetwarzane wszystkie bajty wysłane z klienta. W tym działaniu można zobaczyć wszystkie błędy połączeń, które wystąpiły podczas interakcji klienta.

4. Dla każdego zestawu odebranych bajtów, który odpowiada komunikatowi, przetwarzamy te bajty w działaniu "Przetwarzaj komunikat", gdzie tworzymy obiekt wiadomości WCF. W tym działaniu są wyświetlane błędy związane z złą kopertą lub źle sformułowaną wiadomością.

5. Po utworzeniu komunikatu przesyłamy do działania procesu działania. Jeśli `propagateActivity` jest ustawiona na `true` zarówno dla klienta, jak i usługi, to działanie ma ten sam identyfikator jak zdefiniowany w kliencie i został opisany wcześniej. Z tego etapu zaczniemy korzystać z bezpośredniej korelacji między punktami końcowymi, ponieważ wszystkie ślady emitowane w programie WCF, które są powiązane z żądaniem, są w tym samym działaniu, w tym przetwarzanie komunikatów odpowiedzi.

6. W przypadku akcji poza procesem tworzymy działanie "wykonaj kod użytkownika", aby odizolować ślady emitowane w kodzie użytkownika od tych, które są emitowane w programie WCF. W poprzednim przykładzie ślad "usługa wysyła Dodawanie odpowiedzi" jest emitowany w działaniu "wykonaj kod użytkownika" nie w działaniu rozmnożonym przez klienta, jeśli ma zastosowanie.

Na poniższej ilustracji pierwsze działanie po lewej stronie to działanie główne (0000), które jest działaniem domyślnym. Następne trzy działania to otwarcie ServiceHost. Działanie w kolumnie 5 jest odbiornikiem, a pozostałe działania (od 6 do 8) opisują przetwarzanie komunikatów przez funkcję WCF, od przetwarzania bajtów do aktywacji kodu użytkownika.

Na poniższej ilustracji przedstawiono widok grafu działań usługi WCF:

![Zrzut ekranu podglądu śledzenia przedstawiający listę działań usługi WCF](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-service-activities.gif)

Na poniższym zrzucie ekranu przedstawiono działania zarówno dla klienta, jak i usługi, a następnie wyróżniono akcję proces Dodaj działanie między procesami (pomarańczowy). Strzałki odnoszą się do komunikatów żądań i odpowiedzi wysyłanych i odbieranych przez klienta i usługę. Ślady akcji procesu są oddzielane między procesami na grafie, ale wyświetlane jako część tego samego działania w prawym górnym panelu. Na tym panelu można zobaczyć ślady klientów dla wysłanych komunikatów, a następnie ślady usługi dla odebranych i przetworzonych komunikatów.

Na poniższych ilustracjach przedstawiono widok wykresu działań klienta i usługi WCF.

![Program Graph z podglądu śledzenia, który pokazuje działania klienta i usługi programu WCF.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-service-activities.gif)

W poniższym scenariuszu błędu dane śledzenia błędów i ostrzeżeń są powiązane z usługą i klientem. Wyjątek jest najpierw generowany w kodzie użytkownika w usłudze (najbardziej zielonym działaniem zawierającym ostrzeżenie śledzenia wyjątku "usługa nie może przetworzyć tego żądania w kodzie użytkownika"). Gdy odpowiedź jest wysyłana do klienta, śledzenie ostrzeżeń jest ponownie emitowane w celu określenia komunikatu o błędzie (lewe różowe działanie). Następnie klient zamknie klienta WCF (żółte działanie w lewej dolnej części), które przerywa połączenie z usługą. Usługa zgłasza błąd (najdłuższe różowe działanie po prawej stronie).

![Korzystanie z podglądu śledzenia](media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")

Korelacja błędów w ramach usługi i klienta

Przykładem używanym do generowania tych śladów jest seria żądań synchronicznych używających wsHttpBinding. Istnieją odchylenia od tego grafu dla scenariuszy bez zabezpieczeń lub żądań asynchronicznych, gdzie działanie działania procesu obejmuje operacje BEGIN i End, które stanowią wywołanie asynchroniczne, i pokazuje transfery do działania wywołania zwrotnego. Aby uzyskać więcej informacji na temat dodatkowych scenariuszy, zobacz [kompleksowe scenariusze śledzenia](end-to-end-tracing-scenarios.md).

## <a name="troubleshooting-using-the-service-trace-viewer"></a>Rozwiązywanie problemów przy użyciu przeglądarki śledzenia usługi

Podczas ładowania plików śledzenia w narzędziu Podgląd śledzenia usług można wybrać dowolne działanie czerwone lub żółte na lewym panelu, aby śledzić przyczynę problemu w aplikacji. W przypadku działania 1000 zazwyczaj istnieją Nieobsłużone wyjątki, które są bąbelkowe do użytkownika.

Na poniższej ilustracji przedstawiono sposób wybierania działania czerwonego lub żółtego w celu zlokalizowania katalogu głównego problemu.
![Zrzut ekranu działań czerwonych lub żółtych służących do lokalizowania katalogu głównego problemu.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/service-trace-viewer.gif)

W prawym górnym panelu można przeanalizować ślady dla działania wybranego po lewej stronie. Następnie możesz sprawdzić czerwone lub żółte ślady w tym panelu i zobaczyć, jak są skorelowane. Na poprzednim wykresie zobaczysz ostrzeżenie śledzenia zarówno dla klienta, jak i usługi w tym samym działaniu działania.

Jeśli te ślady nie zapewniają głównej przyczyny błędu, można użyć wykresu przez dwukrotne kliknięcie wybranego działania w lewym panelu (czynność procesowa). Zostanie wyświetlony wykres z powiązanymi działaniami. Następnie można rozwinąć powiązane działania (klikając znaki "+"), aby znaleźć pierwszy emitowany ślad w kolorze czerwonym lub żółtym w powiązanym działaniu. Kontynuuj rozszerzanie działań, które wystąpiły tuż przed czerwonym lub żółtym śladem zainteresowania, po przeniesieniu do powiązanych działań lub przepływów komunikatów między punktami końcowymi, aż do momentu śledzenia głównej przyczyny problemu.

![Korzystanie z podglądu śledzenia](media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")

Rozwijanie działań w celu śledzenia głównej przyczyny problemu

Jeśli element ServiceModel `ActivityTracing` jest wyłączony, ale śledzenie ServiceModel jest włączone, można zobaczyć ślady ServiceModel emitowane w działaniu 0000. Jednak wymaga to większego wysiłku, aby zrozumieć korelację tych śladów.

Jeśli rejestrowanie komunikatów jest włączone, możesz użyć karty wiadomość, aby sprawdzić, na jakim komunikacie występuje błąd. Dwukrotne kliknięcie komunikatu w kolorze czerwonym lub żółtym pozwala zobaczyć widok grafu powiązanych działań. Te działania są najbardziej blisko powiązane z żądaniem, w którym wystąpił błąd.

![Zrzut ekranu podglądu śledzenia z włączonym rejestrowaniem komunikatów.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/message-logging-enabled.gif)

Aby rozpocząć rozwiązywanie problemów, możesz również wybrać czerwony lub żółty ślad komunikatów i kliknąć go dwukrotnie, aby śledzić główną przyczynę.

## <a name="see-also"></a>Zobacz też

- [Scenariusze kompleksowego śledzenia](end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
- [Śledzenie](index.md)
