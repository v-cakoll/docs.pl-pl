---
title: Omówienie architektury transferu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: 83fd5ab1cfe7f48999dd2765405f58543eeb743a
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882217"
---
# <a name="data-transfer-architectural-overview"></a>Omówienie architektury transferu danych
Windows Communication Foundation (WCF) mogą być uważane za to infrastruktura obsługi komunikatów. Może odbierać komunikaty, je przetworzyć i wysyłać je do kodu użytkownika wykonywać dalszych akcji lub można skonstruować wiadomości z dane podane przez kod użytkownika i dostarczania ich do miejsca docelowego. W tym temacie, który jest przeznaczony dla zaawansowanych deweloperów, w tym artykule opisano architekturę do obsługi wiadomości i zawartymi danymi. Prostsze, zorientowane na zadania widoku sposób wysyłania i odbierania danych, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
>  W tym temacie omówiono szczegóły implementacji usługi WCF, które nie są widoczne, sprawdzając modelu obiektu programu WCF. Są dwa wyrazy Uwaga w kolejności, w odniesieniu do szczegółów implementacji udokumentowane. Po pierwsze opisy są uproszczone; rzeczywiste wdrożenie może być bardziej skomplikowane, ze względu na optymalizacje lub z innych powodów. Po drugie, nigdy nie należy polegać na potrzeby szczegółów konkretnej implementacji, nawet udokumentowane, ponieważ te mogą ulec zmianie bez powiadomienia z wersji do wersji lub nawet w przypadku obsługi wersji.  
  
## <a name="basic-architecture"></a>Podstawowa architektura  
 Podstawowe możliwości obsługi komunikatów WCF jest <xref:System.ServiceModel.Channels.Message> klasy, która jest szczegółowo opisane w [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md). Składniki środowiska wykonawczego WCF można podzielić na dwie główne części: stos kanału i struktura usługi za pomocą <xref:System.ServiceModel.Channels.Message> klasy jest punkt połączenia.  
  
 Stos kanał jest odpowiedzialny za konwersji między prawidłową <xref:System.ServiceModel.Channels.Message> wystąpienie i pewne akcje, które odnosi się do wysyłania i odbierania danych komunikatu. Po stronie wysyłającej stosu kanał ma prawidłową <xref:System.ServiceModel.Channels.Message> wystąpienia, a po przetworzenie, wykonuje pewne akcje, które logicznie odnosi się do wysyłania wiadomości. Akcja może wysyłać pakietów protokołu TCP lub HTTP usługi kolejkowania komunikatów w usłudze kolejkowania zapisu komunikatu do bazy danych, zapisanie go do udziału plików lub innych działań, w zależności od implementacji. Najbardziej typowych akcji wysyła wiadomość za pomocą protokołu sieciowego. Po stronie odbierającej się dzieje przeciwieństwo — wykryto akcję (która może być TCP lub HTTP pakiety przychodzące lub innych działań), a po zakończeniu przetwarzania stosu kanału konwertuje tę akcję prawidłową <xref:System.ServiceModel.Channels.Message> wystąpienia.  
  
 Można użyć programu WCF za pomocą <xref:System.ServiceModel.Channels.Message> klasy i kanał stosu bezpośrednio. Jednak wykonanie tej tak jest trudny i czasochłonny proces. Ponadto <xref:System.ServiceModel.Channels.Message> obiekt nie obsługuje metadanych, więc nie można wygenerować silnie typizowaną klienci WCF, jeśli używasz usługi WCF w ten sposób.  
  
 W związku z tym, usługi WCF zawiera struktura usługi, która zapewnia łatwy w użyciu model programowania, który służy do konstruowania i otrzymywać `Message` obiektów. Struktura usługi mapy usługi do typów programu .NET Framework za pomocą pojęcie kontraktów usług i komunikaty będą rozsyłane do operacji użytkownika, które są po prostu .NET Framework metody oznaczone atrybutami <xref:System.ServiceModel.OperationContractAttribute> atrybutu (Aby uzyskać więcej informacji, zobacz [ Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)). Te metody mogą mieć parametry i zwracać wartości. Na stronie usługi struktura usługi konwertuje przychodzące <xref:System.ServiceModel.Channels.Message> wystąpień do parametrów i konwertuje zwracane wartości na wychodzące <xref:System.ServiceModel.Channels.Message> wystąpień. Po stronie klienta jest przeciwieństwem. Na przykład, rozważmy `FindAirfare` operacji poniżej.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Załóżmy, że `FindAirfare` jest wywoływana na kliencie. Struktura usługi na komputerze klienckim konwertuje `FromCity` i `ToCity` parametrów w wychodzący <xref:System.ServiceModel.Channels.Message> wystąpienia i przekazuje je do stosu kanału do wysłania.  
  
 Po stronie usługi gdy <xref:System.ServiceModel.Channels.Message> wystąpienia nadejściu ze stosu kanału, struktura usługi wyodrębnia istotne dane z wiadomości, aby wypełnić `FromCity` i `ToCity` parametrów, a następnie wywołania po stronie usługi `FindAirfare` Metoda. Gdy metoda zwróci wartość, struktura usługi przyjmuje wartość zwrócona liczba całkowita i `IsDirectFlight` parametr wyjściowy, a następnie tworzy <xref:System.ServiceModel.Channels.Message> wystąpienie obiektu, który zawiera te informacje. Następnie przekazuje `Message` wystąpienia stosu kanału do wysłania do klienta.  
  
 Po stronie klienta <xref:System.ServiceModel.Channels.Message> wystąpienia, które zawiera komunikat odpowiedzi wynika ze stosu kanału. Struktura usługi wyodrębnia wartość zwracaną i `IsDirectFlight` wartości i zwraca je do obiektu wywołującego klienta.  
  
## <a name="message-class"></a>Message — klasa  
 <xref:System.ServiceModel.Channels.Message> Klasa jest przeznaczona do abstrakcyjną reprezentację komunikatu, ale jego zamysłem zdecydowanie jest powiązany z komunikatu protokołu SOAP. Element <xref:System.ServiceModel.Channels.Message> zawiera trzy główne informacje: treść wiadomości, nagłówki komunikatów i właściwości komunikatu.  
  
## <a name="message-body"></a>Treść komunikatu  
 Treść komunikatu jest przeznaczona do reprezentowania rzeczywistych danych ładunku komunikatu. Treść wiadomości, zawsze jest przedstawiana jako zestaw informacji XML. Nie oznacza to, że wszystkie komunikaty utworzone lub odebrane w usłudze WCF musi być w formacie XML. Jest stos kanału do określania, jak interpretować treść komunikatu. Może emitować go jako kod XML, przekonwertuj go na innym formacie lub nawet do całkowicie pominąć. Oczywiście z większością wyczerpania WCF powiązania, treść komunikatu jest przedstawiana jako zawartość XML w sekcji treści koperty protokołu SOAP.  
  
 Ważne jest, aby należy pamiętać, że `Message` klasy nie musi zawierać buforu z danymi XML reprezentujący treść. Logicznie `Message` zawiera zestaw informacji XML, ale ten zestaw informacji mogą być dynamicznie zbudowane i nigdy nie fizycznie może istnieć w pamięci.  
  
### <a name="putting-data-into-the-message-body"></a>Umieszczenie danych w treści komunikatu  
 Nie ma jednolitego mechanizmu do dane umieszczane w treści wiadomości. <xref:System.ServiceModel.Channels.Message> Klasa zawiera metody abstrakcyjnej, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, która przyjmuje <xref:System.Xml.XmlDictionaryWriter>. Każda podklasa <xref:System.ServiceModel.Channels.Message> klasy jest odpowiedzialny za przesłaniania tej metody i wypisywanie własnej zawartości. Treść wiadomości zawiera logicznie zestaw informacji XML, `OnWriteBodyContent` tworzy. Na przykład, należy wziąć pod uwagę następujące `Message` podklasę.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fizycznie `AirfareRequestMessage` wystąpienie zawiera tylko dwa parametry ("fromCity" i "toCity"). Jednak logicznie wiadomość zawiera następujący zestaw informacji XML:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Oczywiście należy zwykle nie utworzyć wiadomości w ten sposób, ponieważ struktura usługi można użyć, aby utworzyć komunikat podobny do poprzedniego, z operacji kontraktu parametry. Ponadto <xref:System.ServiceModel.Channels.Message> klasa ma statyczne `CreateMessage` metody, które można użyć do utworzenia komunikatów z często spotykanych rodzajów zawartości: pustego komunikatu, komunikat, który zawiera obiekt serializacji XML przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>, wiadomość, która zawiera protokołu SOAP błędów komunikat, który zawiera kod XML, reprezentowane przez <xref:System.Xml.XmlReader>i tak dalej.  
  
### <a name="getting-data-from-a-message-body"></a>Pobieranie danych z treści wiadomości  
 Można wyodrębnić dane przechowywane w treści komunikatu w dwa sposoby:  
  
- Treść cały komunikat w tym samym czasie można uzyskać przez wywołanie metody <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> metody i przekazywanie w edytora XML. Pełna treść jest zapisywany do tego składnika zapisywania. W tym samym czasie pobierania treści cały komunikat jest również nazywany *zapisania komunikatu*. Podczas wysyłania komunikatów pisania odbywa się przede wszystkim przez stos kanału — część stosu kanał będzie zwykle uzyskują dostęp do treści cały komunikat, Zakoduj je i wyślij ją.  
  
- Innym sposobem, aby uzyskać informacje z treści wiadomości jest wywołanie <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> i Uzyskaj odczytujący XML. Treść komunikatu może zostać oceniony następnie sekwencyjnie, zgodnie z potrzebami przez wywołanie metody w czytniku. Wprowadzenie wiadomości treści —-eliminujemy jest również nazywany *czytania wiadomości*. Odczytanie komunikatu o jest używany głównie przez platformę usługi podczas odbierania komunikatów. Na przykład, gdy <xref:System.Runtime.Serialization.DataContractSerializer> jest używany, struktura usługi zostanie uzyskiwanie odczytującego XML treści i przekazać go do silnika deserializacji, który rozpocznie odczytywanie wiadomości —-elementów i utworzenie odpowiedniego wykresu obiektu.  
  
 Treść wiadomości mogą być pobierane tylko raz. Dzięki temu można pracować ze strumieniami tylko do przodu. Na przykład można napisać <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> zastąpienia, która odczytuje z <xref:System.IO.FileStream> i zwraca wyniki w postaci zestaw informacji XML. Nigdy nie należy do "tyłu" na początku pliku.  
  
 `WriteBodyContents` i `GetReaderAtBodyContents` metody po prostu zaznacz nigdy nie ma zostały pobrane przed treści wiadomości, a następnie wywołaj `OnWriteBodyContents` lub `OnGetReaderAtBodyContents`, odpowiednio.  
  
## <a name="message-usage-in-wcf"></a>Użycie komunikatów w programie WCF  
 Większość komunikaty mogą być klasyfikowane jako *wychodzących* (te, które są tworzone przez platformę usługi do wysłania przez stos channel) lub *przychodzących* (te, które są odbierane z kanału stosu i są interpretowane przez platformę service). Ponadto stosu kanału może działać w trybie buforowanego lub przesyłania strumieniowego. Struktura usługi również może narazić przesyłane strumieniowo lub nonstreamed model programowania. Prowadzi to do przypadków wymienionych w poniższej tabeli, wraz ze szczegółami uproszczone ich implementacji.  
  
|Typ komunikatu|Treść danych w komunikacie|Wpisz implementację (OnWriteBodyContents)|Implementacja odczytu (OnGetReaderAtBodyContents)|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Wychodzące, utworzone na podstawie nonstreamed model programowania|Dane potrzebne do zapisu komunikatu (na przykład obiekt i <xref:System.Runtime.Serialization.DataContractSerializer> wystąpienia potrzebne do serializacji go) *|Logikę niestandardową, aby zapisać wiadomość na podstawie przechowywanych danych (na przykład wywołać `WriteObject` na `DataContractSerializer` jeżeli jest to element serializujący używany) *|Wywołaj `OnWriteBodyContents`, buforować wyniki, zwracać odczytującego XML w buforze|  
|Wychodzące, utworzone na podstawie przesyłanej strumieniowo w modelu programowania|`Stream` z danymi, które ma zostać zapisany *|Zapisać dane z przechowywanych strumienia z wykorzystaniem <xref:System.Xml.IStreamProvider> mechanizm *|Wywołaj `OnWriteBodyContents`, buforować wyniki, zwracać odczytującego XML w buforze|  
|Przychodzące z przesyłania strumieniowego stosu kanału|A `Stream` obiekt, który reprezentuje dane zostaną dodane w za pośrednictwem sieci <xref:System.Xml.XmlReader> nad nią|Zapisać zawartość z przechowywanej `XmlReader` przy użyciu `WriteNode`|Zwraca przechowywaną `XmlReader`|  
|Przychodzące z kanału nonstreaming stosu|Buforu, który zawiera dane treści z `XmlReader` nad nią|Zapisuje jej zawartość z przechowywanej `XmlReader` przy użyciu `WriteNode`|Zwraca przechowywaną lang|  
  
 \* Te elementy nie są implementowane bezpośrednio w `Message` podklasy, ale w podklasy <xref:System.ServiceModel.Channels.BodyWriter> klasy. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.BodyWriter>, zobacz [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-headers"></a>Nagłówki wiadomości  
 Wiadomość może zawierać nagłówki. Nagłówek logicznie składa się zestaw informacji XML, który jest skojarzony z nazwą przestrzeni nazw i kilka innych właściwości. Nagłówki wiadomości są dostępne przy użyciu `Headers` właściwość <xref:System.ServiceModel.Channels.Message>. Każdy nagłówek jest reprezentowany przez <xref:System.ServiceModel.Channels.MessageHeader> klasy. Zwykle nagłówki wiadomości są mapowane na nagłówki wiadomości protokołu SOAP, przy użyciu stosu channel skonfigurowanymi do współdziałania z komunikaty protokołu SOAP.  
  
 Wprowadzanie informacji w nagłówku komunikatu i wyodrębnianie informacji z niego jest podobne do treści wiadomości. Proces nieco jest uproszczone, ponieważ przesyłania strumieniowego nie jest obsługiwany. Istnieje możliwość dostępu do zawartości tego samego nagłówka w więcej niż jeden raz i nagłówków można uzyskiwać w kolejności dowolnego, wymuszając nagłówki, aby zawsze być buforowane. Nie istnieje mechanizm ogólnego przeznaczenia umożliwia skorzystanie z czytnika XML przez nagłówek, ale ma `MessageHeader` podklasy wewnętrzne WCF, reprezentujący można odczytać nagłówka z taką funkcję. Tego rodzaju `MessageHeader` jest tworzony przez stos kanał, po przejściu do trybu wiadomości z aplikacji niestandardowych nagłówków. Umożliwia to struktura usługi za pomocą aparatu deserializacji, takich jak <xref:System.Runtime.Serialization.DataContractSerializer>, aby zinterpretować tych nagłówków.  
  
 Aby uzyskać więcej informacji, zobacz [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-properties"></a>Właściwości komunikatu  
 Wiadomość może zawierać właściwości. A *właściwość* jest dowolny obiekt .NET Framework, który jest skojarzony z nazwy ciągu. Właściwości są dostępne za pośrednictwem `Properties` właściwość `Message`.  
  
 W odróżnieniu od treści komunikatu i nagłówków wiadomości, (które zwykle mapowania treści protokołu SOAP i nagłówków protokołu SOAP, odpowiednio) właściwości wiadomości są zwykle nie wysłanego lub odebranego wraz z komunikatów. Właściwości komunikatu istnieje przede wszystkim jako mechanizm przekazywania informacji do przekazania danych dotyczących wiadomości między różnych kanałów w stosie channel oraz między stos kanału i modelu usługi.  
  
 Na przykład kanał transportu HTTP, które są dołączone jako część usługi WCF jest w stanie tworzenie różnych kodów stanu HTTP, takich jak "404 (nie znaleziono)" i "500 (wewnętrzny błąd serwera)," podczas wysyłania odpowiedzi do klientów. Przed wysłaniem komunikat odpowiedzi, sprawdza, czy `Properties` z `Message` zawiera właściwość o nazwie "httpResponse", która zawiera obiekt typu <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>. Jeśli takiej właściwości zostanie znaleziony, zostanie przedstawiony <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> właściwości i użyć tego kodu stanu. Jeśli go nie zostanie znaleziony, wartość domyślna "200 (OK)" Kod jest używany.  
  
 Aby uzyskać więcej informacji, zobacz [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Komunikatu całościowo  
 Do tej pory Omówiliśmy metod dostępu do różnych części wiadomości w izolacji. Jednak <xref:System.ServiceModel.Channels.Message> klasa udostępnia także metody do pracy z cały komunikat jako całości. Na przykład `WriteMessage` metoda zapisuje się cały komunikat do usługi składnika zapisywania XML.  
  
 Aby było to możliwe, należy zdefiniować mapowanie między całą `Message` wystąpienie i zestaw informacji XML. Takie mapowanie istnieje już w rzeczywistości: Usługi WCF używa standardowego protokołu SOAP do definiowania tego mapowania. Gdy `Message` wystąpienia jest zapisywany jako zestaw informacji XML, wynikowy zestaw informacji jest prawidłowy kopercie SOAP, która zawiera komunikat. W efekcie `WriteMessage` zwykle wykona następujące czynności:  
  
1. Napisz tagu początkowego elementu koperty protokołu SOAP.  
  
2. Zapisać element nagłówek SOAP tagu początkowego, zapisać wszystkie nagłówki, a następnie Zamknij element nagłówka.  
  
3. Zapis elementu treści protokołu SOAP tagu początkowego.  
  
4. Wywołaj `WriteBodyContents` lub metodę równoważną zapisać treści.  
  
5. Zamknij elementów treści i schematu envelope.  
  
 Poprzednie kroki są ściśle powiązane ze standardem protokołu SOAP. Jest to skomplikowane faktem, że wiele wersji protokołu SOAP istnieje, na przykład nie można poprawnie zapisać element koperty protokołu SOAP nie wiedząc o tym wersję protokołu SOAP. Ponadto w niektórych przypadkach może być pożądane, aby wyłączyć to złożone SOAP specyficzne dla mapowania całkowicie.  
  
 Do tych celów `Version` właściwość znajduje się na `Message`. Może zostać ustawiony na wersję protokołu SOAP do użycia podczas zapisywania na poziomie komunikatu lub może być ustawiona `None` zapobiegające mapowań specyficzne dla protokołu SOAP. Jeśli `Version` właściwość jest ustawiona na `None`, metody, współpracujących z act cały komunikat, tak, jakby komunikat obejmowało tylko jego treść na przykład `WriteMessage` po prostu wywoła `WriteBodyContents` zamiast wykonywania wielu kroków wymienionych powyżej. Oczekuje się, że dla wiadomości przychodzących, `Version` zostaną automatycznie wykryte i poprawnie.  
  
## <a name="the-channel-stack"></a>Stos kanału  
  
### <a name="channels"></a>Kanały  
 Opisany przed stosu kanał jest odpowiedzialny za konwertowanie wychodzące <xref:System.ServiceModel.Channels.Message> wystąpień do określonej akcji (na przykład wysyłanie pakietów przez sieć) lub przekształcania określonej akcji (na przykład odbierania pakietów sieciowych) w przychodzących `Message` wystąpienia.  
  
 Stos kanału składa się z co najmniej jednego kanału uporządkowane w kolejności. Wychodzący `Message` wystąpienia jest przekazywany do pierwszego kanału w stosie (nazywane również *kanałowi*), która przekazuje go do następnego kanału w dół w stosie i tak dalej. Komunikat kończy się w ostatniej kanału, które jest wywoływane *kanał transportowy*. Komunikaty przychodzące pochodzą kanał transportu i są przekazywane kanałów w górę stosu. Z najwyższego poziomu kanału wiadomości są zazwyczaj przekazywane w ramach usługi. Choć zwyczajowego wzorca dla komunikatów aplikacji, niektórych kanałów mogą działać inaczej, na przykład może wysyłają wiadomości do infrastruktury bez przekazywana wiadomości z kanału powyżej.  
  
 Kanały może działać w komunikacie na różne sposoby, przekazywanego w ramach stosu. Najbardziej typowych operacji jest dodanie nagłówka do wysyłanej wiadomości i odczytywania nagłówków w wiadomości przychodzącej. Na przykład kanału może obliczyć podpisu cyfrowego komunikatu i dodaj go jako nagłówek. Kanał może również sprawdzać tego pliku nagłówkowego podpis cyfrowy na komunikaty przychodzące i blokowanie wiadomości, które nie mają prawidłowego podpisu z wprowadzania swój sposób w górę stosu kanału. Kanały często Ustaw lub sprawdź właściwości komunikatu. Treść komunikatu jest zazwyczaj nie został zmodyfikowany, mimo że jest to dozwolone, na przykład kanału zabezpieczeń programu WCF można zaszyfrować treść komunikatu.  
  
### <a name="transport-channels-and-message-encoders"></a>Kanały transportu i koderów wiadomości  
 Znajdujących się najniżej kanału w stosie jest odpowiedzialny za faktycznie Przekształcanie wychodzący <xref:System.ServiceModel.Channels.Message>, ponieważ zmodyfikowane przez inne kanały do określonej akcji. Po stronie odbierającej to kanał, który konwertuje niektóre akcje do `Message` czy inne kanały procesu.  
  
 Jak wspomniano wcześniej, działania mogą być zróżnicowane: wysyłania lub odbierania pakietów sieciowych za pośrednictwem różnych protokołów, odczytu lub zapisu komunikatu w bazie danych lub usługi kolejkowania wiadomości lub usuwania z kolejki komunikatów w kolejki usługi kolejkowania komunikatów, aby zapewnić, ale kilka przykładów. Wszystkie te działania mają jedną wspólną: potrzebują transformacji między WCF`Message` wystąpienia i rzeczywiste grupy bajtów, które mogą być wysyłane, odbierane, odczytu, zapisywane, umieszczane w kolejce lub usuniętych z kolejki. Proces konwersji `Message` do grupy b nosi nazwę *kodowanie*i procesu tworzenia `Message` jest wywoływana z grupy bajtów *dekodowanie*.  
  
 Większość kanały transportu używanie składników, które wywołuje *komunikatu koderów* celu kodowania i dekodowania pracy. Koder komunikatów jest podklasą <xref:System.ServiceModel.Channels.MessageEncoder> klasy. `MessageEncoder` zawiera różne `ReadMessage` i `WriteMessage` przeciążenia metody, aby wykonać konwersję między `Message` i grup w bajtach.  
  
 Po stronie wysyłającej przekazuje buforowania kanał transportowy `Message` obiekt, który otrzymał z kanału powyżej `WriteMessage`. Ponownie pobiera tablicę bajtów, które następnie używa do wykonania akcji, jej (np. pakowania tych bajtów jako prawidłowy pakiety TCP i wysyła je do odpowiedniego miejsca docelowego). Najpierw tworzy przesyłania strumieniowego kanał transportowy `Stream` (na przykład za pośrednictwem wychodzące połączenie TCP), a następnie przekazuje zarówno `Stream` i `Message` potrzebny do wysłania do odpowiedniego `WriteMessage` przeciążenia, które zapisuje się komunikat .  
  
 Po stronie odbierającej buforowania kanał transportowy wyodrębnia Bajty przychodzące (na przykład z pakiety przychodzące TCP) do tablicy i wywołania `ReadMessage` można pobrać `Message` obiektu, że można przekazać dodatkowe stosu kanału. Tworzy przesyłania strumieniowego kanał transportowy `Stream` obiektu (na przykład strumień sieci za pośrednictwem połączenia przychodzące TCP), a następnie przekazuje ją do `ReadMessage` odzyskać `Message` obiektu.  
  
 Rozdzielenie kanały transportu i koder komunikatów nie jest obowiązkowa. istnieje możliwość zapisać kanał transportu, która nie korzysta z kodera komunikatów. Jednak zaletą ta separacja jest łatwość tworzenia. Tak długo, jak kanał transportowy używa tylko podstawowy <xref:System.ServiceModel.Channels.MessageEncoder>, może współpracować z dowolnej usługi WCF koder komunikatów innych firm. Podobnie ten sam kodera zwykle może służyć za pośrednictwem kanałów innych transportu.  
  
### <a name="message-encoder-operation"></a>Operacja kodera komunikatów  
 Aby opisać typowych operacji kodera, warto należy wziąć pod uwagę następujące cztery przypadków.  
  
|Operacja|Komentarz|  
|---------------|-------------|  
|Kodowanie, buforowane|W tryb buforowany kodera zazwyczaj tworzy buforu zmiennym rozmiarze i następnie tworzy moduł zapisujący XML nad nim. Następnie wywołuje <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> w komunikacie zakodowany, który zapisuje nagłówki i następnie do treści przy użyciu <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, zgodnie z opisem w poprzedniej sekcji o `Message` w tym temacie. Zawartość buforu (reprezentowana jako tablicę bajtów) są następnie zwracane dla kanał transportu do użycia.|  
|Kodowanie, przesyłane strumieniowo|W trybie przesyłane strumieniowo operacja jest podobny do powyższego, jednak prostsze. Nie ma potrzeby dla buforu. Modułu zapisujący XML zwykle jest tworzone w strumieniu i <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> jest wywoływana w `Message` zapisać go na ten moduł zapisujący.|  
|Dekodowanie, buforowane|Podczas dekodowania w tryb buforowany specjalny `Message` podklasy, który zawiera buforowane dane zwykle jest tworzone. Odczytaniu nagłówków wiadomości i utworzeniu odczytującego XML umieszczony na treść wiadomości. Jest to czytnika, które będą zwracane z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Dekodowanie, przesyłane strumieniowo|Dekodowanie w trybie przesyłane strumieniowo, specjalne podklasy komunikat normalnie zostanie utworzona. Strumień jest zaawansowane, aby odczytać te nagłówki i umieść ją w treści wiadomości. Czytnik XML jest tworzona w strumieniu. Jest to czytnika, które będą zwracane z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Kodery można wykonywać oraz innych funkcji. Kodery może na przykład utworzyć pulę XML czytników i składników zapisywania. Jest kosztowne utworzyć nowego czytnika XML lub moduł zapisujący za każdym razem, gdy jest ono wymagane. W związku z tym koderów zwykle Obsługa puli czytników i pulę modułów zapisujących, można skonfigurować rozmiaru. W opisach kodera operacji opisanych powyżej zawsze, gdy frazę "Tworzenie czytnika/składnika zapisywania XML" jest używana, zwykle oznacza to "Przystąp do jednego z puli, lub utworzyć nowe, jeśli nie jest dostępny." Koder (i `Message` podklasy tworzy podczas dekodowania) zawierają logikę do zwrócenia czytników i składników zapisywania do pul, gdy nie są już potrzebne (na przykład, gdy `Message` jest zamknięty).  
  
 Usługi WCF zawiera trzy koderów wiadomości, chociaż istnieje możliwość tworzenia dodatkowych typów niestandardowych. Podane typy nie są typu Text, plik binarny i komunikat transmisji optymalizacji mechanizm (MTOM). Te ustawienia są opisane szczegółowo w temacie [Wybieranie kodera komunikatów](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>Interfejs element IStreamProvider  
 Podczas zapisywania wysyłanej wiadomości zawiera treść przesyłane strumieniowo do usługi składnika zapisywania XML, <xref:System.ServiceModel.Channels.Message> używa sekwencję wywołań, podobnie do poniższego w jego <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> implementacji:  
  
- Należy zapisać wszystkie informacje niezbędne poprzedzających strumienia (na przykład otwierający XML tag).  
  
- Napisz strumienia.  
  
- Napisz żadnych informacji po strumienia (na przykład zamykający XML tag).  
  
 Działa to również efektywnie integrowana z kodowania, które są podobne do tekstową Kodowanie XML. Jednak niektóre kodowania nie należy umieszczać informacje zestaw informacji XML (na przykład znaczników początkowych i końcowych elementów XML) wraz z danych zawartych w elementy. Na przykład kodowanie MTOM komunikat jest podzielony na wiele części. Jedną z części zawiera zestaw informacji XML, który może zawierać odwołania do innych części dla elementu rzeczywistej zawartości. Zestaw informacji XML jest zwykle mały w porównaniu do zawartości przesyłanej strumieniowo, dobrym pomysłem będzie buforować zestaw informacji, zapisać go, a następnie wpisz zawartość w taki sposób, w strumieniu. Oznacza to, że do czasu zamknięcia tagu elementu są zapisywane, strumień powinna nie został napisany jeszcze.  
  
 W tym celu <xref:System.Xml.IStreamProvider> używany jest interfejs. Interfejs ma <xref:System.Xml.IStreamProvider.GetStream> metodę, która zwraca strumień do zapisania. Poprawny sposób zapisać treść komunikatu przesyłanej strumieniowo w <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> jest następująca:  
  
1. Należy zapisać wszystkie informacje niezbędne poprzedzających strumienia (na przykład otwierający XML tag).  
  
2. Wywołaj `WriteValue` przeciążenia na <xref:System.Xml.XmlDictionaryWriter> przyjmującej <xref:System.Xml.IStreamProvider>, za pomocą `IStreamProvider` implementację, która zwraca strumień do zapisania.  
  
3. Napisz żadnych informacji po strumienia (na przykład zamykający XML tag).  
  
 W przypadku tej metody, moduł zapisujący XML może wybrać kiedy wywołać metodę <xref:System.Xml.IStreamProvider.GetStream> i zapisać dane przesyłane strumieniowo. Na przykład autorzy XML pomocy tekstowych i binarnych wywołać ją od razu i zapisać zawartości przesyłanej strumieniowo umieszczone między tagiem początkowym i końcowym. Moduł zapisujący MTOM może podjąć <xref:System.Xml.IStreamProvider.GetStream> później, gdy wszystko będzie gotowe do zapisu w odpowiedniej części wiadomości.  
  
## <a name="representing-data-in-the-service-framework"></a>Efektywna reprezentacja danych w ramach usługi  
 Jak wspomniano w sekcji "Podstawowa architektura" tego tematu, struktura usługi jest częścią usługi WCF, między innymi, jest odpowiedzialny za konwersji między przyjazny dla użytkownika modelu programowania dla danych komunikatu i rzeczywiste `Message` wystąpień. Zwykle wymiany komunikatów jest przedstawiona w ramach usługi w postaci .NET Framework metoda oznaczona za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu. Metoda może zająć kilka parametrów i może zwrócić wartość zwracaną lub na zewnątrz (lub obu). Po stronie usługi parametry wejściowe reprezentują wiadomości przychodzącej i wartość zwracaną i parametrów out reprezentują komunikatu wychodzącego. Po stronie klienta odwrotna ma wartość true. Model programowania do opisywania komunikatów za pomocą parametrów i wartości zwracanej jest szczegółowo opisane w [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Jednakże ta sekcja zawiera krótkie omówienie.  
  
## <a name="programming-models"></a>Modele programowania  
 Struktura usługi WCF obsługuje pięciu różnych modeli programowania do opisywania wiadomości:  
  
### <a name="1-the-empty-message"></a>1. Pusty komunikat  
 Jest to najprostsza. Aby opisać pustego komunikatu przychodzącego, nie należy używać parametrów wejściowych.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Aby opisać pustego komunikatu wychodzącego, użyj pustą wartość zwracaną i nie używaj żadnego z parametrów out:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Należy zwrócić uwagę na to, że to różni się od kontraktu jednokierunkowego operacji:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 W `SetDesiredTemperature` przykład wymiany komunikatów dwukierunkowe został opisany. Komunikat jest zwrócony przez operację, ale jest on pusty. Istnieje możliwość zwrócić błąd operacji. W tym przykładzie "Ustaw żarówka" wymiany komunikatów jest jednokierunkowe, więc nie ma wychodzących do opisu. Usługa nie może komunikować się dowolny stan z powrotem do klienta w tym przypadku.  
  
### <a name="2-using-the-message-class-directly"></a>2. Używanie klasy Message bezpośrednio  
 Istnieje możliwość użycia <xref:System.ServiceModel.Channels.Message> klasy (lub jednej z jej podklas) bezpośrednio w kontrakt operacji. W takim przypadku po prostu przekazuje struktura usługi `Message` operacji stosu kanału i na odwrót, żadne dalsze przetwarzanie.  
  
 Istnieją dwa przypadki użycia głównego przy użyciu `Message` bezpośrednio. Umożliwia to w przypadku zaawansowanych scenariuszy, gdy żaden z innymi modelami programowania umożliwia dostateczną elastyczność, aby opisać wiadomości. Na przykład można użyć pliki na dysku do opisania wiadomości, za pomocą właściwości pliku, staje się nagłówki komunikatów i jego zawartość staje się treść komunikatu. Następnie można utworzyć coś podobnego do następującego.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 Drugi typowe na użytek `Message` w kontrakt operacji jest kiedy usługa obchodzi, na temat określonego komunikatu o zawartości i działa w komunikacie na czarne pole. Na przykład może być usługa, która przekazuje komunikaty do wielu innych odbiorców. Kontrakt może być napisana w następujący sposób.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Akcja = "*" wiersz skutecznie wyłącza funkcję wysyłania komunikatów i gwarantuje, że wszystkie komunikaty wysyłane do `IForwardingService` kontraktu wprowadzić swoją drogę do `ForwardMessage` operacji. (Zazwyczaj Dyspozytor zbada nagłówek "Action" wiadomości w celu określenia operacji, który jest przeznaczony dla. Akcja = "\*" oznacza "wszystkie możliwe wartości nagłówka Action".) Kombinacja Akcja = "\*" i przy użyciu komunikatu jako parametr nosi nazwę "zamówienie uniwersalnym", ponieważ jest w stanie wszystkie komunikaty możliwe. Aby móc wysyłać wszystkie możliwe wiadomości, użyj wiadomości jako wartość zwracaną i ustaw `ReplyAction` do "\*". Struktura usługi uniemożliwi Dodawanie nagłówka własnej akcji, dzięki któremu można sterować za pomocą tego nagłówka `Message` obiektu, należy zwrócić.  
  
### <a name="3-message-contracts"></a>3. Kontrakty komunikatów  
 WCF oferuje deklaratywny model programowania do opisywania wiadomości, nazywane *kontrakt komunikatu*. Ten model jest szczegółowo opisane w [za pomocą kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Zasadniczo cały komunikat jest reprezentowane przez jeden typ .NET Framework, który używa atrybutów, takich jak <xref:System.ServiceModel.MessageBodyMemberAttribute> i <xref:System.ServiceModel.MessageHeaderAttribute> do opisania części klasy kontraktu komunikatu, które powinny być mapowane do której części wiadomości.  
  
 Kontrakty komunikatów zapewniają szczegółową kontrolę nad wynikowy `Message` wystąpienia (chociaż oczywiście nie poziom kontroli, jak przy użyciu `Message` bezpośrednio klasy). Na przykład treści wiadomości często składają się z wielu rodzajów informacji, każdy jest reprezentowany przez własną — element XML. Te elementy mogą mieć miejsce, bezpośrednio w treści (*bez* tryb) lub może być *opakowane* w tym elemencie XML. Za pomocą kontraktu komunikatu, model programowania umożliwia podjęcie decyzji bez a opakowana i nazwa przestrzeni nazw i nazwa otoki formantu.  
  
 Poniższy przykład kodu kontraktu komunikatu demonstruje te funkcje.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Elementy oznaczone serializacji (przy użyciu <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, lub innych powiązanych atrybutów) musi być możliwy do serializacji, aby uczestniczyć w kontraktu komunikatu. Aby uzyskać więcej informacji zobacz sekcję "Serializacji" w dalszej części tego tematu.  
  
### <a name="4-parameters"></a>4. Parametry  
 Często deweloperem i potrzebujesz do opisania operacją, która działa na wielu fragmentów danych nie potrzebuje stopień kontroli, które zapewniają kontrakty komunikatów. Na przykład podczas tworzenia nowych usług, jeden zazwyczaj chcesz decyzji bez a opakowana i podjąć decyzję w sprawie element otoki. Podejmowanie tych decyzji często wymaga dogłębnej wiedzy na temat usług sieci Web i protokołu SOAP.  
  
 Struktura usługi WCF automatycznie wybrać najlepszy i najbardziej zgodną reprezentacji protokołu SOAP do wysyłania i odbierania wielu powiązanych rodzajów informacji, bez wymuszania tych opcji na użytkownika. To jest realizowane poprzez opisanie po prostu tych rodzajów informacji jako parametry lub zwracane wartości kontrakt operacji. Na przykład należy wziąć pod uwagę następujące kontrakt operacji.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Struktura usługi automatycznie decyduje się na umieszczenie wszystkich trzech rodzajów informacji (`customerID`, `item`, i `quantity`) do treści komunikatu i zawijania je w element otoki o nazwie `SubmitOrderRequest`.  
  
 Opisujący informacje, które mają być wysyłane lub odbierane prostą listę parametrów kontrakt operacji jest zalecane podejście, o ile nie istnieją specjalne powody, aby przejść do kontraktu komunikatu bardziej złożonych lub `Message`— na podstawie modeli programowania.  
  
### <a name="5-stream"></a>5. Strumień  
 Za pomocą `Stream` lub jednej z jej podklasach w kontrakt operacji lub jako część treści jedyny komunikat w kontraktu komunikatu jest uznawana za osobne modelu programowania z opisane powyżej. Za pomocą `Stream` w ten sposób jest jedynym sposobem zagwarantowania, że Twoja Umowa będzie można używać w sposób przesyłane strumieniowo, ograniczony pisania własnych przesyłania strumieniowego zgodnym z `Message` podklasę. Aby uzyskać więcej informacji, zobacz [duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Gdy `Stream` lub jedna z jej podklasach jest używana w ten sposób, nie jest wywoływany przez element serializujący. Dla wiadomości wychodzących specjalne przesyłania strumieniowego `Message` podklasy zostanie utworzony i strumień jest zapisywany na zewnątrz zgodnie z opisem w sekcji na <xref:System.Xml.IStreamProvider> interfejsu. Dla wiadomości przychodzących, tworzy struktura usługi `Stream` podklasy za pośrednictwem wiadomości przychodzące i przekazuje go do operacji.  
  
## <a name="programming-model-restrictions"></a>Ograniczenia dotyczące modelu programowania  
 Modele programowania opisanych powyżej arbitralnie nelze kombinovat. Na przykład jeśli operacja akceptuje typ kontraktu komunikatu, kontraktu komunikatu musi być jej tylko parametr wejściowy. Ponadto operacja musi, a następnie zwrócenia pustego komunikatu (typ zwracany void) lub innego komunikatu kontraktu. Ograniczenia te programowania modelu są opisane w tematach dotyczących każdego określonego modelu programowania: [Używanie kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md), [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md), i [duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Elementy formatujące komunikaty  
 Modele programowania opisanych powyżej są obsługiwane przez podłączenie w składnikach o nazwie *komunikatu elementy formatujące* w ramach usługi. Elementy formatujące komunikaty są typy, które implementują <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> lub <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsu lub zarówno potrzeby klientów i klienci WCF service, odpowiednio.  
  
 Elementy formatujące komunikaty są zwykle podłączone przez zachowania. Na przykład <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> podłącza kontraktu danych formatującego. Odbywa się po stronie usługi, ustawiając <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> na poprawny element formatujący w <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> metody, lub po stronie klienta, ustawiając <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> na poprawny element formatujący w <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> metody.  
  
 W następującej tabeli wymieniono metody, które mogą implementować programu formatującego.  
  
|Interface|Metoda|Akcja|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Konwertuje przychodzące `Message` parametry operacji|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Tworzy wychodzący `Message` wartość zwracana z operacji/out parametrów|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Tworzy wychodzący `Message` z parametrami operacji|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Konwertuje przychodzące `Message` do wartości zwracanej/parametrów out|  
  
## <a name="serialization"></a>Serializacja  
 Zawsze, gdy używasz kontrakty komunikatów lub parametry, aby opisać treść wiadomości, musi być konwertowanie typów programu .NET Framework i zestaw informacji XML reprezentacja serializacji. Serializacji jest używany w innych miejscach w WCF — na przykład <xref:System.ServiceModel.Channels.Message> ma ogólny <xref:System.ServiceModel.Channels.Message.GetBody%2A> metodę, która służy do odczytać całej treści komunikatu deserializacji obiektu.  
  
 Usługi WCF obsługuje dwie technologie serializacji "fabrycznej" do serializacji i deserializacji parametrów i części wiadomości: <xref:System.Runtime.Serialization.DataContractSerializer> i `XmlSerializer`. Ponadto można napisać niestandardowy serializatory. Jednak inne części WCF (takie jak typowa `GetBody` metody lub protokołu SOAP błędów serializacji) mogą być zmuszeni do używania tylko <xref:System.Runtime.Serialization.XmlObjectSerializer> podklasy (<xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer>, ale nie <xref:System.Xml.Serialization.XmlSerializer>), lub nawet mogą być zakodowane używana będzie tylko <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 `XmlSerializer` Jest mechanizm serializacji, używane w usługach sieci Web platformy ASP.NET. `DataContractSerializer` Jest nowy mechanizm serializacji, która obsługuje nowy model programowania kontraktu danych. `DataContractSerializer` wybór domyślny i wybór do użycia `XmlSerializer` mogą być wykonane na podstawę dla operacji przy użyciu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> atrybutu.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> odpowiedzialność podłączeniem elementy formatujące komunikaty dla zachowania operacji `DataContractSerializer` i `XmlSerializer`, odpowiednio. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Zachowanie faktycznie mogą pracować z dowolnego serializator, która pochodzi od klasy <xref:System.Runtime.Serialization.XmlObjectSerializer>, w tym <xref:System.Runtime.Serialization.NetDataContractSerializer> (opisanych szczegółowo w temacie przy użyciu autonomicznego serializacji). Jedną z wywołuje `CreateSerializer` przeciążenia metody wirtualnej można uzyskać z serializatora. Monit o podłączenie innego serializatora, Utwórz nową <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> podklasy i zastąpienie `CreateSerializer` przeciążenia.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
