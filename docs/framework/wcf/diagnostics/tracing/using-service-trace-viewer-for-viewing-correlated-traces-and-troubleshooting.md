---
title: "Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 048ef839db0656340827a5928056a3c063f5aa3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów
W tym temacie opisano format danych śledzenia, jak wyświetlać i metod korzystających z przeglądarki śledzenia usługi Rozwiązywanie problemów z aplikacją.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Za pomocą narzędzia podglądu śledzenia usługi  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Narzędzia podglądu śledzenia usługi pomaga skorelowania dane śledzenia diagnostycznego utworzonego przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] odbiorników można znaleźć katalogu głównego. Przyczyna błędu. Narzędzie pozwala na przeglądanie, grupy i ślady filtru, dzięki czemu można diagnozować, naprawy i sprawdź problemy z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług. Aby uzyskać więcej informacji na temat stosowania tego narzędzia, zobacz [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Ten temat zawiera zrzuty ekranu śladów generowane przez uruchomienie [śledzenie i rejestrowanie komunikatów](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbkowania, podczas wyświetlania przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). W tym temacie przedstawiono sposób śledzenia zawartości, działań i ich korelacji i analizowania dużych ilości danych śledzenia podczas rozwiązywania problemów.  
  
## <a name="viewing-trace-content"></a>Wyświetlanie zawartości śledzenia  
 Zdarzenia śledzenia zawiera następujące najważniejsze informacje:  
  
-   Nazwa działania po ustawieniu.  
  
-   Czas emisji.  
  
-   Poziom śledzenia.  
  
-   Nazwa źródła śledzenia.  
  
-   Nazwa procesu.  
  
-   Identyfikator wątku.  
  
-   Identyfikator unikatowy śledzenia, czyli adres URL, którego obiektem docelowym w Docs firmy Microsoft, z którego można uzyskać więcej informacji dotyczących śledzenia.  
  
 Wszystkie te można wyświetlić w górnym prawym panelu podglądu śledzenia usługi lub w **podstawowe informacje** sekcji w widoku sformatowany panelu prawym dolnym podczas wybierania śledzenia.  
  
> [!NOTE]
>  Jeśli klienta i usługi znajdują się na tym samym komputerze, będzie występować ślady dla obydwu aplikacji. Te można filtrować przy użyciu **nazwa procesu** kolumny.  
  
 Ponadto sformatowany widok zawiera również opis dla śledzenia i dodatkowe szczegółowe informacje po ich udostępnieniu. Drugie mogą obejmować wyjątek typu i wiadomości, stosy wywołań Akcja komunikatu, z/do pól i inne informacje o wyjątku.  
  
 W widoku XML tagi xml przydatne są następujące:  
  
-   \<Podtyp > (poziom śledzenia).  
  
-   \<TimeCreated >.  
  
-   \<Źródło > (nazwa źródła śledzenia).  
  
-   \<Korelacji > (identyfikator działania ustawić podczas emitowania śledzenia).  
  
-   \<Wykonanie > (identyfikator procesu i wątku).  
  
-   \<Komputera >.  
  
-   \<ExtendedData >, w tym \<akcji >, \<MessageID > i \<ActivityId > Ustaw w nagłówku wiadomości przy wysyłaniu wiadomości.  
  
 Jeśli należy zbadać śledzenia "Wysłano wiadomość kanałem", mogą pojawić się następujące zawartości.  
  
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
  
## <a name="servicemodel-e2e-tracing"></a>Śledzenie ServiceModel E2E  
 Gdy `System.ServiceModel` ustawiono źródła śledzenia `switchValue` innych niż wyłączone, i `ActivityTracing`, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] tworzy działania i transferu dla [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] przetwarzania.  
  
 Działanie to jednostka logiczna przetwarzania czy grupy wszystkie ślady dotyczące tej jednostki przetwarzania. Na przykład można zdefiniować jedno działanie dla każdego żądania. Transfery utworzyć przyczynowego między działaniami w obrębie punktów końcowych. Propagowanie identyfikator działania umożliwia odnoszą się działań w obrębie punktów końcowych. Można to zrobić przez ustawienie `propagateActivity` = `true` w konfiguracji w każdym punkcie końcowym. Działań, przesyłania i propagacji umożliwiają wykonywanie błąd korelacji. W ten sposób można znaleźć przyczynę błędu szybciej.  
  
 Na komputerze klienckim co [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] działania jest tworzony dla każdego wywołania modelu obiektu (na przykład otwórz elementu ChannelFactory, Dodaj dzielenia i itd.) Każdy z wywołania operacji są przetwarzane w działaniu "Akcja procesu".  
  
 Na poniższym zrzucie ekranu wyodrębniony z [śledzenie i rejestrowanie komunikatów](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) próbki lewego panelu Wyświetla listę działań utworzonych w procesie klienta, posortowane według czasu utworzenia. Poniżej przedstawiono listę chronologicznej działania:  
  
-   Konstruować fabryki kanałów (obiektu ClientBase).  
  
-   Otworzyć fabryki kanałów.  
  
-   Przetwarzane akcji Dodaj.  
  
-   Skonfiguruj bezpieczną sesję (ten WYSTĄPIŁ na pierwsze żądanie) i przetworzyć trzy wiadomości odpowiedzi infrastruktury zabezpieczeń: RST, odpowiedź RSTR, SCT (proces komunikat 1, 2, 3).  
  
-   Mnożenie przetwarzane Subtract, i dzielenia żądań.  
  
-   Zamknięte fabryki kanałów, a w ten sposób zamknięte bezpiecznej sesji i przetworzyć odpowiedzi na komunikat zabezpieczeń Anuluj.  
  
 Widzimy komunikatów infrastruktury zabezpieczeń z powodu wsHttpBinding.  
  
> [!NOTE]
>  W [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], zostanie przedstawiony wiadomości odpowiedzi początkowo przetwarzanych w oddzielnych działania (proces komunikat) przed możemy skorelowania do odpowiedniego działania działania procesu, który obejmuje komunikat żądania do przeniesienia. To odbywa się w infrastrukturze wiadomości i żądań asynchronicznych, ze względu na fakt, że firma Microsoft musi sprawdzić wiadomości, odczytać nagłówka identyfikatora i zidentyfikować istniejące działanie procesu akcji o takim identyfikatorze służące do skorelowania do niego. Żądań synchronicznych firma Microsoft blokuje odpowiedzi, a więc wiedzieć, jakie działania procesu odpowiedzi odnosi się do.  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace4.gif "e2eTrace4")  
Działania klienta WCF, wymienionych według godzina utworzenia (lewego panelu) i zagnieżdżonych działań i dane śledzenia (w górnym prawym panelu)  
  
 Gdy firma Microsoft wybierz działanie, w lewym panelu, firma Microsoft Zobacz zagnieżdżonych działań i dane śledzenia w górnym prawym panelu. W związku z tym jest to obniżonej hierarchiczny widok listy działań po lewej stronie, na podstawie wybranej nadrzędnej działania. Ponieważ wybranej akcji procesu dodaj to pierwsze żądanie, to działanie zawiera działanie ustawić zapasowej bezpieczną sesję (przesyłanie danych do przeniesienia od) i śledzi rzeczywiste przetwarzanie akcji Dodaj.  
  
 Kliknij dwukrotnie działanie procesu Dodaj działania w lewym panelu, możemy stwierdzić graficzną reprezentację klienta [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] działania związane z Dodaj. Pierwsze działanie po lewej stronie jest działanie główne (0000), która jest domyślne działanie. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]transfery poza działanie otoczenia. Jeśli to nie jest zdefiniowany, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] transferów poza 0000. W tym miejscu drugi działania. Dodaj działania procesu transferu poza 0. Następnie sprawdź ustawienia bezpieczną sesję.  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace5.gif "e2eTrace5")  
Wykres widoku działania klienta WCF: działanie otoczenia (tutaj 0), proces działania i ustawić zapasowej bezpieczną sesję  
  
 W górnym prawym panelu możemy stwierdzić, że wszystkie ślady dotyczące działań dodać działania procesu. W szczególności firma Microsoft ma wysłała komunikat żądania ("Wysłano wiadomość kanałem") i Odebrano odpowiedź ("Odebrano wiadomość kanałem") w tym samym działaniu. To jest wyświetlane na wykresie. Dla uzyskania przejrzystości Skonfiguruj bezpieczną sesję działania jest zwinięte na wykresie.  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace6.gif "e2eTrace6")  
Lista śladów działania procesu akcji: możemy wysłać żądania i odbierania odpowiedzi w tym samym działaniu.  
  
 W tym miejscu możemy załadować śladów klienta tylko dla jasności, ale ślady usługi (Odebrano komunikat żądania i odpowiedzi wiadomość wysłana) są wyświetlane w to samo działanie, jeśli należą również załadowany w narzędziu i `propagateActivity` ustawiono `true.` przedstawiono to w późniejszym ilustracji.  
  
 W usłudze mapuje modelu aktywności [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pojęcia w następujący sposób:  
  
1.  Firma Microsoft może utworzyć, a następnie otwórz ServiceHost (może to spowodować kilku czynności związanych z hosta, na przykład w przypadku zabezpieczeń).  
  
2.  Utworzymy nasłuchiwania na działanie dla każdego odbiornika w ServiceHost (z przesyłania i otwórz ServiceHost).  
  
3.  Odbiornik wykryje żądanie komunikacji inicjowane przez klienta, przesyłania do działania "Odbieranie bajtów", w którym są przetwarzane wszystkich bajtów wysłanych z klienta. W przypadku tego działania możemy Zobacz wszelkie błędy połączenia, które wystąpiły w czasie interakcji usługi klienta.  
  
4.  Dla każdego zestawu bajtów odebranych jest umożliwiająca wiadomości, możemy przetworzyć tych bajtów w działaniu "Proces komunikat", gdzie utworzymy [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] obiekt typu Message. W przypadku tego działania widzimy błędy związane z koperty nieprawidłowy lub uszkodzony komunikat.  
  
5.  Gdy komunikat jest sformułowany, przekazywane do działania procesu akcji. Jeśli `propagateActivity` ma ustawioną wartość `true` na klienta i usługi, to działanie ma ten sam identyfikator jak zdefiniowane na komputerze klienckim i opisanych powyżej. Z tego etapu Rozpoczniemy korzystanie z bezpośredniej korelacji między punktami końcowymi, ponieważ wszystkie ślady emitowanych w [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] powiązanych do żądania znajdują się w tym samym działania, w tym przetwarzanie komunikatu odpowiedzi.  
  
6.  Akcja poza procesem, utworzymy "Wykonanie kodu użytkownika" działanie, aby odizolować śladów wysyłanego w kodzie użytkownika z tymi emitowanych w [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. W powyższym przykładzie śledzenia "Usługa wysyła odpowiedź Dodaj" są emitowane w działaniu "Kod użytkownika Execute" nie znajduje się w działania propagowane przez klienta, jeśli ma to zastosowanie.  
  
 Na ilustracji poniżej pierwsze działanie po lewej stronie będzie działanie główne (0000), która jest domyślne działanie. Trzech kolejnych działań są otworzyć ServiceHost. Działania w kolumnie 5 jest odbiornika, a pozostałych działań (od 6 do 8) opisano przetwarzania WCF wiadomość z bajtów przetwarzania aktywację kodu użytkownika.  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace7.gif "e2eTrace7")  
Lista działań usługi WCF  
  
 Poniższy zrzut ekranu przedstawia działania klienta i usługi i prezentuje działanie procesu Akcja dodanie między procesami (kolor pomarańczowy). Strzałki dotyczą żądań i odpowiedzi wiadomości wysyłanych i odbieranych przez klienta i usługi. Ślady procesu akcji są rozdzielone przez procesy na wykresie, ale wyświetlany jako część tego samego działania w prawym górnym panelu. W tym panelu możemy Zobacz ślady klienta dla wysłanych komunikatów następuje ślady usługi odebranej i przetwarzanie komunikatów.  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace8.gif "e2eTrace8")  
Widok wykresu zarówno działań klienta i usługi WCF  
  
 W poniższym scenariuszu błąd błąd i ostrzeżenie ślady na usługi i klienta są powiązane. Najpierw jest zgłaszany wyjątek w kodzie użytkownika w usłudze (zielony działania prawej krawędzi, który obejmuje Ostrzeżenie śledzenia dla wyjątku "Usługa nie może przetworzyć tego żądania w kodzie użytkownika."). Po wysłaniu odpowiedzi do klienta śledzenia ostrzeżenie jest ponownie wysyłanego do oznaczania komunikat o błędzie (po lewej stronie różowym działanie). Klient następnie zamyka jego klienta WCF (żółty działanie po stronie lewej dolnej), która przerywa połączenie z usługą. Usługa zgłasza błąd (najdłuższym różowym działanie po prawej stronie).  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Błąd korelacji między usługą i klienta  
  
 Przykładowy służący do generowania te operacje śledzenia jest szereg żądań synchronicznych przy użyciu klasy wsHttpBinding. Brak odchylenia od tego wykresu dla scenariuszy bez zabezpieczeń lub z żądań asynchronicznych, której działanie procesu akcji obejmuje operacje rozpoczęcia i zakończenia, które tworzą wywołania asynchronicznego oraz przedstawia transferu do działania wywołania zwrotnego. Aby uzyskać więcej informacji o dodatkowych scenariuszach, zobacz [scenariusze śledzenia End-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## <a name="troubleshooting-using-the-service-trace-viewer"></a>Rozwiązywanie problemów przy użyciu przeglądarki śledzenia usługi  
 Podczas ładowania plików śledzenia w narzędziu Podgląd śledzenia usługi można wybrać żadnych czerwony lub żółty aktywności w lewym panelu śledzić przyczyna problemu w aplikacji. Zazwyczaj działanie 000 ma nieobsługiwane wyjątki, które propagują do użytkownika.  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace10.gif "e2eTrace10")  
Zaznaczenie działania czerwony lub żółty Znajdź główny problem  
  
 W górnym prawym panelu należy zbadać śledzenia dla działania, którego wybrano po lewej stronie. Można zbadać czerwony lub żółty dane śledzenia w panelu i zobacz, jak są skorelowane. Na poprzednim wykresie przedstawiono zapisy ostrzeżeń zarówno dla klienta i usługi, w tym samym działaniu działania procesu.  
  
 Jeśli te operacje śledzenia nie zawierają przyczynę błędu, może korzystać z wykresu, klikając dwukrotnie wybrane działanie w lewym panelu (tutaj Akcja procesu). Następnie zostanie wyświetlony wykres z powiązanych z nimi działań. Następnie można rozwinąć pokrewne działania (klikając znaki "+") można znaleźć pierwszego śledzenia emitowany na czerwono lub żółty, pokrewne działania. Zachowaj rozwijanie działań, które wystąpiły tuż przed śledzenia czerwony lub żółty zainteresowania po przekazaniu pokrewne działania lub przepływów wiadomości między punktami końcowymi, dopóki śledzić główną przyczynę problemu.  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Rozszerzanie działania śledzenia głównej przyczyny problemu  
  
 Jeśli ServiceModel `ActivityTracing` jest wyłączone, ale ServiceModel śledzenie jest włączone, widać wysyłanego w działaniu 0000 śladów ServiceModel. Jednak wymaga więcej wysiłku, aby zrozumieć korelację te operacje śledzenia.  
  
 Po włączeniu rejestrowania komunikatów służy karcie wiadomość aby zobaczyć, których komunikat jest wpływ błędu. Dwukrotne kliknięcie komunikatu na czerwono lub żółty, jest widoczny w widoku wykresu powiązanych działań. Te działania są pokazane najlepiej powiązanych do żądania, w którym wystąpił błąd.  
  
 ![Przy użyciu przeglądarki śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace11.gif "e2eTrace11")  
Zacząć Rozwiązywanie problemów można również pobranie śladu czerwony lub żółty wiadomości i dwukrotnie kliknij go, aby śledzić głównej przyczyny  
  
## <a name="see-also"></a>Zobacz też  
 [Scenariusze śledzenia end-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Narzędzie podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
