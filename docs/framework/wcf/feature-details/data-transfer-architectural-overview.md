---
title: "Omówienie architektury transferu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a2adbc1e281e978c1f579d1e7b0cc0cf75cd36a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="data-transfer-architectural-overview"></a>Omówienie architektury transferu danych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]można traktować jako infrastruktury obsługi wiadomości. Można odbierać komunikaty, ich przetwarzania i wysyłania ich do kodu użytkownika dla dalszego działania lub można utworzyć wiadomości z danych przez kod użytkownika i dostarczania ich do miejsca docelowego. W tym temacie, który jest przeznaczony dla zaawansowanych programistów, w tym artykule opisano architekturę obsługi wiadomości i danych zawartych w niej. Dla widoku prostszy, zorientowane na zadania sposobu wysyłania i odbierania danych, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
>  W tym temacie omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szczegóły implementacji, które nie są widoczne, sprawdzając [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu modelu. Są dwa wyrazy ostrożność w kolejności, w odniesieniu do szczegóły implementacji udokumentowane. Po pierwsze opisy są uproszczone; Rzeczywista implementacja może być bardziej złożone z powodu optymalizacji lub z innych powodów. Po drugie, nigdy nie będą miały szczegóły konkretnej implementacji, nawet udokumentowane, ponieważ te może ulec zmianie bez uprzedzenia z wersji do wersji lub nawet w przypadku obsługi wersji.  
  
## <a name="basic-architecture"></a>Podstawowa architektura  
 Stanowiącej podstawę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] możliwości obsługi wiadomości jest <xref:System.ServiceModel.Channels.Message> klasy, która jest opisane szczegółowo w temacie [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md). Składniki wykonawcze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] można podzielić na dwie główne części: stosu kanału i struktura usługi z <xref:System.ServiceModel.Channels.Message> klasy trwa punktu połączenia.  
  
 Stos kanał jest odpowiedzialny za konwertowanie prawidłową <xref:System.ServiceModel.Channels.Message> wystąpienia i niektóre akcje, umożliwiająca wysyłanie i odbieranie wiadomości danych. Po stronie wysyłającej stosu kanału ma prawidłową <xref:System.ServiceModel.Channels.Message> wystąpienia, a po zakończeniu niektórych przetwarzania wykonuje niektóre akcje logicznie umożliwiająca wysyłanie komunikatu. Akcja może wysyłać pakietów TCP lub HTTP usługi kolejkowania komunikatów w usłudze kolejkowania zapisu komunikatu do bazy danych, zapisać go do udziału plików lub innych działań, w zależności od implementacji. Najbardziej typowych akcji wysyła wiadomość za pośrednictwem protokołu sieciowego. Po stronie odbierania sytuacji przeciwieństwem — wykrycia akcję (która może być TCP lub HTTP pakiety przychodzące lub innych działań), a po zakończeniu przetwarzania stosu kanału konwertuje tej akcji na prawidłową <xref:System.ServiceModel.Channels.Message> wystąpienia.  
  
 Można użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przy użyciu <xref:System.ServiceModel.Channels.Message> klasy i kanał stosu bezpośrednio. Jednak jest to zrobić. Ponadto <xref:System.ServiceModel.Channels.Message> obiektu nie zapewnia metadanych obsługi, więc nie można wygenerować jednoznacznie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, jeśli używasz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w ten sposób.  
  
 W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera struktura usługi, która zapewnia model programowania łatwy w użyciu, który służy do tworzenia i odbierania `Message` obiektów. Struktura usługi mapy usług [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types za pośrednictwem pojęcie kontraktów usług i komunikaty będą rozsyłane do operacji użytkownika, które są po prostu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody oznaczone atrybutami <xref:System.ServiceModel.OperationContractAttribute> atrybutu (Aby uzyskać więcej informacji, zobacz [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)). Te metody mogą mieć parametrów i zwraca wartości. Na stronie usługi w ramach usługi konwertuje przychodzące <xref:System.ServiceModel.Channels.Message> wystąpień do parametrów i konwertuje wartości są zwracane do wychodzące <xref:System.ServiceModel.Channels.Message> wystąpień. Po stronie klienta jest przeciwieństwem. Rozważmy na przykład `FindAirfare` operacji poniżej.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Załóżmy, że `FindAirfare` jest wywoływana na kliencie. Konwertuje w ramach usługi na kliencie `FromCity` i `ToCity` parametrów w wychodzący <xref:System.ServiceModel.Channels.Message> wystąpienia i przekazuje je do stosu kanału na wysłanie.  
  
 Na stronie usługi podczas <xref:System.ServiceModel.Channels.Message> wystąpienia dociera ze stosu kanału, struktura usługi wyodrębnia odpowiednie dane z komunikat, aby wypełnić `FromCity` i `ToCity` parametry, a następnie wywołania po stronie serwera `FindAirfare` Metoda. Gdy metoda zwróci wartość, w ramach usługi przyjmuje wartość całkowitą zwrócony i `IsDirectFlight` parametru wyjściowego i tworzy <xref:System.ServiceModel.Channels.Message> wystąpienie obiektu, który zawiera te informacje. Następnie przekazuje `Message` wystąpienia stos kanału do wysłania do klienta.  
  
 Po stronie klienta <xref:System.ServiceModel.Channels.Message> wystąpienia, które zawiera komunikat odpowiedzi wynika ze stosu kanału. Struktura usługi wyodrębnia wartości zwracanej i `IsDirectFlight` wartości i zwraca je do obiektu wywołującego klienta.  
  
## <a name="message-class"></a>Klasy wiadomości  
 <xref:System.ServiceModel.Channels.Message> Klasa ma być abstrakcyjna reprezentację komunikatu, ale jego projektowania zdecydowanie jest powiązany z komunikatu protokołu SOAP. A <xref:System.ServiceModel.Channels.Message> zawiera trzy główne informacje: treść wiadomości, nagłówki komunikatów i właściwości wiadomości.  
  
## <a name="message-body"></a>Treść wiadomości  
 Treść komunikatu jest przeznaczony do reprezentowania danych rzeczywistych ładunku komunikatu. Treść komunikatu zawsze jest reprezentowany jako obiekt typu Infoset XML. Nie oznacza to, że wszystkie komunikaty utworzony lub odebrano w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] musi być w formacie XML. Jest stos kanału, aby określić sposób interpretowania treść komunikatu. Może Emituj go jako XML, przekonwertuj go do jakiegoś innego formatu lub nawet pominąć całkowicie. Oczywiście z większością powiązania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dostaw, treść komunikatu jest reprezentowany jako zawartości XML w sekcji treści koperty protokołu SOAP.  
  
 Ważne jest, aby należy pamiętać, że `Message` klasy nie musi zawierać buforu z danych XML reprezentujący treść. Logicznie `Message` zawiera XML typu infoset sprawdzonych, ale ten obiekt typu Infoset dynamicznie zbudowany i nigdy nie fizycznie może istnieć w pamięci.  
  
### <a name="putting-data-into-the-message-body"></a>Wprowadzanie danych do treści wiadomości  
 Nie istnieje mechanizm uniform umieszczać dane w treści wiadomości. <xref:System.ServiceModel.Channels.Message> Klasa zawiera metody abstrakcyjnej <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, która przyjmuje <xref:System.Xml.XmlDictionaryWriter>. Każdy podklasą klasy <xref:System.ServiceModel.Channels.Message> klasy jest odpowiedzialny za przesłaniania tej metody i zapisywanie poza własną zawartość. Treść wiadomości zawiera logicznie XML typu infoset sprawdzonych który `OnWriteBodyContent` tworzy. Na przykład, należy wziąć pod uwagę następujące `Message` podklasy.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fizycznie `AirfareRequestMessage` wystąpienie zawiera tylko dwa ciągi ("fromCity" i "toCity"). Jednak logicznie komunikat zawiera następujące XML typu infoset sprawdzonych:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Oczywiście należy zwykle nie utworzyć wiadomości w ten sposób, ponieważ struktura usługi umożliwia tworzenie kontraktu parametry komunikat podobny do poprzedniej operacji. Ponadto <xref:System.ServiceModel.Channels.Message> klasa ma statyczną `CreateMessage` metody używane do tworzenia komunikatów o najczęściej spotykane typy zawartości: pusty, komunikat, który zawiera seryjnych do pliku XML z obiekt <xref:System.Runtime.Serialization.DataContractSerializer>, wiadomość zawierającą SOAP odporność komunikat, który zawiera kod XML reprezentowany przez <xref:System.Xml.XmlReader>i tak dalej.  
  
### <a name="getting-data-from-a-message-body"></a>Pobieranie danych z treści wiadomości  
 Można wyodrębnić danych przechowywanych w treści wiadomości, przede wszystkim na dwa sposoby:  
  
-   Treść komunikatu cały w tym samym czasie można uzyskać przez wywołanie metody <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> — metoda i przekazywanie edytora XML. Pełna treść jest zapisywany do ten moduł zapisujący. W tym samym czasie pobieranie treści cały komunikat jest również nazywany *pisanie wiadomości*. Zapisywanie odbywa się głównie przez stos kanału podczas wysyłania wiadomości — część stosu kanału będzie zwykle uzyskać dostęp do treści cały komunikat, kodować je i wysyłać je.  
  
-   Inny sposób, aby uzyskać informacje o treści wiadomości jest wywołać <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> i uzyskać modułu odczytującego XML. Treść komunikatu mają dostęp sekwencyjnie, zgodnie z potrzebami przez wywołanie metody w module. Pobieranie wiadomości treści element za fragment jest również nazywany *odczytywania komunikatu*. Odczytywanie wiadomości jest używany głównie przez platformę service podczas odbierania wiadomości. Na przykład, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> jest w użyciu, w ramach usługi będą uzyskać modułu odczytującego XML w treści i przekaż ją do aparat deserializacji, który zostanie następnie uruchom odczytywanie wiadomości--elementów i utworzenie odpowiednich wykres obiektu.  
  
 Treść komunikatu może zostać pobrany tylko raz. Dzięki temu można pracować z strumieni tylko do przodu. Na przykład można napisać <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> zastąpienia, która odczytuje z <xref:System.IO.FileStream> i zwraca wynik jako XML typu Infoset. Nigdy nie należy do "tyłu" na początku pliku.  
  
 `WriteBodyContents` i `GetReaderAtBodyContents` metody po prostu zaznacz nigdy nie ma zostały pobrane przed treści wiadomości, a następnie wywołać `OnWriteBodyContents` lub `OnGetReaderAtBodyContents`odpowiednio.  
  
## <a name="message-usage-in-wcf"></a>Obciążenie komunikatu w programie WCF  
 Większość komunikaty mogą być klasyfikowane jako *wychodzących* (te, które są tworzone przez platformę usługi do wysłania przez kanał stos) lub *przychodzące* (te, które zostaną odebrane z kanału stosu i czy interpretowane przez platformę service). Ponadto stosu kanału może działać w trybie buforowanego lub przesyłania strumieniowego. Struktura usługi również może narazić przesyłanej strumieniowo lub nonstreamed model programowania. Prowadzi to do przypadków wymienionych w poniższej tabeli, wraz z uproszczonego szczegóły ich realizacji.  
  
|Typ komunikatu|Treść danych w komunikacie|Implementacja zapisu (OnWriteBodyContents)|Implementacja odczytu (OnGetReaderAtBodyContents)|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Wychodzące utworzone na podstawie nonstreamed model programowania|Dane wymagane do zapisywania wiadomości (na przykład obiekt i <xref:System.Runtime.Serialization.DataContractSerializer> wystąpienia potrzebne do serializacji go) *|Niestandardowa logika do zapisywania wiadomości na podstawie przechowywanych danych (na przykład wywołać `WriteObject` na `DataContractSerializer` jeżeli jest to element serializujący używany) *|Wywołanie `OnWriteBodyContents`, buforować wyniki, zwracać modułu odczytującego XML w buforze|  
|Wychodzące utworzone na podstawie strumienia model programowania|`Stream` z danymi do zapisania *|Zapisz dane z przechowywanych stream przy użyciu <xref:System.Xml.IStreamProvider> mechanizmu *|Wywołanie `OnWriteBodyContents`, buforować wyniki, zwracać modułu odczytującego XML w buforze|  
|Przychodzące z przesyłania strumieniowego stosu kanału|A `Stream` obiekt, który reprezentuje danych przesyłanych sieci z <xref:System.Xml.XmlReader> nad nim|Zapisać zawartość z przechowywanych `XmlReader` przy użyciu`WriteNode`|Zwraca zapisana`XmlReader`|  
|Przychodzące z kanału nonstreaming stosu|Buforu, który zawiera treść danych za pomocą `XmlReader` nad nim|Zapisuje się zawartość z przechowywanych `XmlReader` przy użyciu`WriteNode`|Zwraca język przechowywane|  
  
 \*Te elementy nie zostały zaimplementowane bezpośrednio w `Message` podklasy, ale w podklasy <xref:System.ServiceModel.Channels.BodyWriter> klasy. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.BodyWriter>, zobacz [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-headers"></a>Nagłówki komunikatów  
 Komunikat może zawierać nagłówki. Nagłówek logicznie składa się z typu infoset sprawdzonych XML, który jest skojarzony z nazwą przestrzeni nazw i kilka innych właściwości. Nagłówki komunikatów są dostępne przy użyciu `Headers` właściwość <xref:System.ServiceModel.Channels.Message>. Każdy nagłówek jest reprezentowany przez <xref:System.ServiceModel.Channels.MessageHeader> klasy. Zwykle nagłówki komunikatów są mapowane na nagłówkach wiadomości SOAP przy użyciu stosu kanału skonfigurowane do pracy z komunikatami SOAP.  
  
 Umieszczanie informacji w nagłówku wiadomości i wyodrębniania informacji z niego jest podobne do korzystania z treści wiadomości. Proces nieco jest uproszczone, ponieważ przesyłania strumieniowego nie jest obsługiwane. Istnieje możliwość dostępu do zawartości tego samego nagłówka więcej niż raz, a nagłówki można uzyskać w kolejności dowolnego, wymuszanie nagłówków, aby zawsze można buforować. Nie istnieje mechanizm ogólnego przeznaczenia, można uzyskać za pośrednictwem nagłówka modułu odczytującego XML, ale `MessageHeader` podklasy wewnętrzne [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] reprezentujący można odczytać nagłówka takiej możliwości. Ten typ `MessageHeader` jest tworzony przez stos kanału, gdy wiadomość z nagłówków niestandardowych aplikacji. Dzięki temu w ramach usługi na korzystanie z aparatu deserializacji, takich jak <xref:System.Runtime.Serialization.DataContractSerializer>, aby zinterpretować tych nagłówków.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-properties"></a>Właściwości wiadomości  
 Komunikat może zawierać właściwości. A *właściwości* dowolnego [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obiekt, który jest skojarzony z nazwą ciągu. Właściwości są dostępne za pośrednictwem `Properties` właściwość `Message`.  
  
 W przeciwieństwie do treści wiadomości i nagłówków komunikatów, (które zwykle mapowania treści protokołu SOAP i nagłówki SOAP odpowiednio) właściwości wiadomości zwykle nie są wysyłane lub odbierane wraz z wiadomości. Właściwości komunikatu istnieje głównie jako mechanizm komunikacji, aby przekazać dane o komunikacie, między różnych kanałów w stosie kanału i między stosu kanału i model usługi.  
  
 Na przykład HTTP transport kanału wchodzącego w skład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest w stanie tworzenie różnych kodów stanu HTTP, takie jak "404 (nie znaleziono)" i "500 (wewnętrzny błąd serwera)," podczas wysyłania odpowiedzi do klientów. Przed wysłaniem wiadomości odpowiedzi, sprawdza, czy `Properties` z `Message` zawiera właściwość o nazwie "httpResponse", która zawiera obiekt typu <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>. Jeśli zostanie znaleziony takich właściwości, zostanie ona wyszukana w <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> właściwości i użyj tego kodu stanu. Jeśli go nie zostanie znaleziony, wartość domyślna "200 (OK)" używany jest kod.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Komunikat jako całość  
 Do tej pory Omówiliśmy metod dostępu do poszczególnych części komunikatu w izolacji. Jednak <xref:System.ServiceModel.Channels.Message> klasy udostępnia również metody służące do pracy z cały komunikat jako całość. Na przykład `WriteMessage` metoda zapisuje się cały komunikat do edytora XML.  
  
 Aby było to możliwe, należy zdefiniować mapowania między całą `Message` wystąpienia i XML typu Infoset. Takie mapowanie w rzeczywistości istnieje: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa standardowego protokołu SOAP w celu zdefiniowania to mapowanie. Gdy `Message` wystąpienia jest zapisywany jako XML typu infoset sprawdzonych wynikowy obiekt typu Infoset jest prawidłowy koperty protokołu SOAP, który zawiera komunikat. W związku z tym `WriteMessage` zwykle może wykonać następujące czynności:  
  
1.  Zapisu elementu koperty protokołu SOAP tagu początkowego.  
  
2.  Element nagłówka SOAP tagu początkowego zapisu, zapisać wszystkie nagłówki i Zamknij element nagłówka.  
  
3.  Zapisu elementu treści protokołu SOAP tagu początkowego.  
  
4.  Wywołanie `WriteBodyContents` lub metodę równoważną zapisać treści.  
  
5.  Zamknij elementy treści i koperty.  
  
 Poprzednie kroki są ściśle powiązane z standardowego protokołu SOAP. To jest skomplikowane faktem, że wiele wersji SOAP istnieje, na przykład nie można zapisać element koperty protokołu SOAP poprawnie bez uprzedniego uzyskania informacji o wersji protokołu SOAP w użyciu. Ponadto w niektórych przypadkach może być pożądane, aby wyłączyć to złożony SOAP specyficzne dla mapowania całkowicie.  
  
 W tym celu `Version` właściwości znajduje się na `Message`. Można ją ustawić na wersję SOAP do użycia podczas zapisywania wiadomości lub można ją ustawić `None` zapobiegające mapowań specyficzne dla protokołu SOAP. Jeśli `Version` właściwość jest ustawiona na `None`, metody, które pracować z czynnością cały komunikat tak, jakby komunikat składa się z jego treści, na przykład `WriteMessage` po prostu spowodowałoby wywołanie `WriteBodyContents` zamiast wykonywania wielu kroków opisanych powyżej. Oczekuje się, które w komunikatach przychodzących `Version` zostanie automatycznie wykrytej i poprawnie ustawiony.  
  
## <a name="the-channel-stack"></a>Stos kanału  
  
### <a name="channels"></a>Kanały  
 Określone przed stosu kanał jest odpowiedzialny za konwertowanie wychodzące <xref:System.ServiceModel.Channels.Message> wystąpienia na niektóre działania (takie jak wysyłanie pakietów za pośrednictwem sieci) lub konwersji niektóre akcje (takich jak odbieranie pakietów sieciowych) na przychodzące `Message` wystąpienia.  
  
 Stos kanału składa się z jednego lub kilku kanałów uporządkowanych w sekwencji. Wychodzące `Message` wystąpienia są przekazywane do pierwszego kanału w stosie (nazywane również *kanałowi*), która przekazuje ją do następnego kanału w dół stosu i tak dalej. Komunikat kończy ostatniego kanału, która jest wywoływana *kanał transportu*. Przychodzące komunikaty pochodzą kanał transportu i są przekazywane kanałów stosu. Z kanału najwyższego poziomu komunikatu zwykle są przekazywane w ramach usługi. Jest to zwykle wzorca dla komunikatów aplikacji, niektórych kanałów może działać nieco inaczej, na przykład mogli przesłać wiadomości infrastruktury bez przekazano komunikat przez kanał powyżej.  
  
 Kanały może działać na wiadomości na różne sposoby, kiedy przechodzi on przez stos. Najbardziej typowych operacji jest dodanie nagłówka do wysyłanej wiadomości i odczytywania nagłówków na wiadomości przychodzącej. Na przykład kanału może obliczyć podpisu cyfrowego wiadomości i dodaj go jako nagłówek. Kanał może również sprawdzić ten nagłówek podpisu cyfrowego wiadomości przychodzących i blokowanie wiadomości, które nie mają prawidłowego podpisu z wprowadzeniem ich sposób górę stosu kanału. Kanały również często ustawić lub sprawdzić właściwości wiadomości. Treść komunikatu zwykle nie jest modyfikowany, mimo że jest to dozwolone, na przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanału zabezpieczeń można zaszyfrować wiadomości.  
  
### <a name="transport-channels-and-message-encoders"></a>Kanały transportu i kodery wiadomości  
 Znajdujących się najniżej kanału w stosie jest odpowiedzialny za faktycznie Przekształcanie wychodzące <xref:System.ServiceModel.Channels.Message>, ponieważ modyfikowany przez inne kanały do określonej akcji. Po stronie odbierania jest kanału, który konwertuje niektóre akcje w `Message` czy inne kanały procesu.  
  
 Jak wspomniano wcześniej, może być zmieniona akcje: wysyłanie lub odbieranie pakietów sieciowych za pośrednictwem różnych protokołów, odczytu lub zapisu komunikatu w bazie danych usługi kolejkowania lub usuwania komunikatów w kolejki usługi kolejkowania komunikatów, aby zapewnić, ale kilka przykładów. Te akcje są wspólne rzecz: wymagają przekształceń między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Message` wystąpienia i rzeczywistego grupy bajtów, które mogą być wysyłane, odebrany, odczytu, zapisana, Zakolejkowane lub usuniętej. Proces konwersji `Message` do grupy bajtów jest nazywany *kodowanie*i procesu tworzenia `Message` z grupy bajtów jest nazywany *dekodowania*.  
  
 Większość kanały transportu używanie składnika o nazwie *komunikatu koderów* kodowania i dekodowania pracy. Koder komunikatów jest podklasą <xref:System.ServiceModel.Channels.MessageEncoder> klasy. `MessageEncoder`zawiera różne `ReadMessage` i `WriteMessage` przeciążenia metody, które umożliwia konwersję pomiędzy `Message` i grup bajtów.  
  
 Po stronie wysyłającej przekazuje buforowania kanał transportu `Message` obiekt, który otrzymał od kanału powyżej `WriteMessage`. Ponownie pobiera tablicę bajtów, które używa następnie wykonać jego operacji (np. pakowania tych bajtów jako prawidłowy pakiety TCP i wysyłania ich do poprawny docelowy). Najpierw tworzy przesyłania strumieniowego kanał transportu `Stream` (na przykład za pośrednictwem wychodzące połączenie TCP) i następnie przekazuje zarówno `Stream` i `Message` należy wysłać do odpowiedniego `WriteMessage` przeciążenia, które zapisuje się komunikat .  
  
 Po stronie odbiorczej buforowania kanał transportu wyodrębnia przychodzące bajty (na przykład z pakietów przychodzących TCP) do tablicy i wywołania `ReadMessage` uzyskanie `Message` obiektów, jaką może przekroczyć dalsze górę stosu kanału. Tworzy przesyłania strumieniowego kanał transportu `Stream` obiektu (na przykład strumień sieci przez przychodzące połączenie TCP) i przekazuje do `ReadMessage` odzyskać `Message` obiektu.  
  
 Rozdzielenie kanały transportu i kodera wiadomości nie jest obowiązkowe; istnieje możliwość zapisu kanał transportu, który nie korzysta z kodera wiadomości. Jednak zaletą oddzielenie jest łatwość kompozycji. Tak długo, jak kanał transportu używa tylko base <xref:System.ServiceModel.Channels.MessageEncoder>, można pracować ze wszystkimi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lub kodera wiadomości innych firm. Podobnie tego samego kodera zwykle można w dowolnym kanał transportu.  
  
### <a name="message-encoder-operation"></a>Operacja kodera komunikatów  
 Do opisania typową operację kodera, warto należy wziąć pod uwagę następujące cztery przypadków.  
  
|Operacja|Komentarz|  
|---------------|-------------|  
|Kodowanie, buforowane|W tryb buforowany koder zwykle tworzy buforu rozmiarach i następnie tworzy edytora XML nad nim. Następnie wywołuje <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> w komunikacie zakodowane, który zapisuje nagłówki i następnie w treści przy użyciu <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, zgodnie z opisem w poprzedniej sekcji o `Message` w tym temacie. Zawartość buforu (reprezentowane jako tablicę bajtów) są następnie zwracane dla kanał transportu do użycia.|  
|Kodowanie, strumieniowego|W trybie przesyłanej strumieniowo operacji jest podobny do powyżej, ale jest to prostsze. Nie istnieje potrzeba bufora. Edytora XML jest zwykle tworzony przez strumień i <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> jest wywoływana na `Message` zapisać go do tego składnika zapisywania.|  
|Dekodowanie, buforowane|Podczas dekodowania w tryb buforowany specjalnego `Message` zwykle utworzono podklasę, który zawiera buforowane dane. Nagłówki wiadomości są odczytywane i tworzenia modułu odczytującego XML znajduje się w treści wiadomości. Jest to reader, który zostanie zwrócony z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Dekodowanie, strumieniowego|Podczas dekodowania w trybie przesyłany strumieniowo, zwykle jest tworzony specjalne podklasy wiadomości. Strumień jest zaawansowane, aby odczytać wszystkie nagłówki i umieść go w treści wiadomości. Czytnik XML zostanie utworzona przez strumień. Jest to reader, który zostanie zwrócony z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Kodery można wykonywać również inne funkcje. Na przykład koderów może utworzyć pulę czytniki XML i modułów zapisujących. Jest kosztowna do utworzenia nowego modułu odczytującego XML lub zapisywania za każdym razem, gdy jest ono wymagane. W związku z tym koderów zwykle Obsługa puli czytelników i składników zapisywania można skonfigurować rozmiaru puli. W opisach operacji kodera opisanych powyżej po każdej zmianie frazę "Utwórz czytnika/składnika zapisywania XML" jest używana, zwykle oznacza to "wykonać jedną z puli, lub stworzyć, jeśli nie jest dostępny." Koder (i `Message` podklasy tworzy podczas dekodowania) zawiera logikę do zwrócenia czytelników i zapisywania do pul, gdy nie są już potrzebne (na przykład, gdy `Message` jest zamknięty).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia trzy koderów wiadomości, mimo że można tworzyć dodatkowe niestandardowych typów. Podane typy tekstu, dane binarne i mechanizmu optymalizacji transmisji wiadomości (MTOM). Te ustawienia zostały opisane szczegółowo w [Wybieranie kodera komunikatów](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>Element IStreamProvider interfejsu  
 Podczas zapisywania wysyłanej wiadomości zawiera treść przesyłany strumieniowo do edytora XML <xref:System.ServiceModel.Channels.Message> używa sekwencję wywołań podobne do następujących w jego <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> implementacji:  
  
-   Zapisać wszelkie niezbędne informacje poprzedzających strumienia (na przykład otwierający XML tag).  
  
-   Zapisu strumienia.  
  
-   Zapis żadnych informacji po strumienia (na przykład zamykający XML tag).  
  
 To dobrze działa z kodowania, które są podobne do kodowania tekstowy XML. Jednak niektóre kodowania nie umieszczaj XML typu infoset sprawdzonych informacji (na przykład znaczników początkowych i końcowych elementów XML) wraz z danych zawartych w elementów. Na przykład w kodowanie MTOM wiadomość jest podzielony na wiele części. Jedną część zawiera XML typu Infoset, który może zawierać odwołania do innych części dla elementu rzeczywistej zawartości. XML typu infoset sprawdzonych jest zwykle małe w porównaniu do strumienia zawartości, więc warto buforu typu Infoset, zapisać go, a następnie wpisz zawartość w sposób przesyłany strumieniowo. Oznacza to, że do czasu zamknięcia tagu elementu są zapisywane, strumień powinien nie został napisany jeszcze.  
  
 W tym celu <xref:System.Xml.IStreamProvider> używany jest interfejs. Interfejs ma <xref:System.Xml.IStreamProvider.GetStream> metodę, która zwraca strumień do zapisania. Do zapisał komunikat przesyłany strumieniowo treści w prawidłowy sposób <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> wygląda następująco:  
  
1.  Zapisać wszelkie niezbędne informacje poprzedzających strumienia (na przykład otwierający XML tag).  
  
2.  Wywołanie `WriteValue` przeciążenia na <xref:System.Xml.XmlDictionaryWriter> pobierającej <xref:System.Xml.IStreamProvider>, z `IStreamProvider` implementację, która zwraca strumień do zapisania.  
  
3.  Zapis żadnych informacji po strumienia (na przykład zamykający XML tag).  
  
 Z tej metody edytora XML może wybrać kiedy wywołać metodę <xref:System.Xml.IStreamProvider.GetStream> i zapisać dane przesyłany strumieniowo. Na przykład zapisywania XML tekstową i binarne wywołują go bezpośrednio i zapisać zawartości przesyłanej strumieniowo między tagiem początkowym i końcowym. Modułu zapisującego MTOM może podjąć <xref:System.Xml.IStreamProvider.GetStream> później, gdy będzie gotowy do zapisu w odpowiedniej części wiadomości.  
  
## <a name="representing-data-in-the-service-framework"></a>Reprezentacja danych w ramach usługi  
 Jak już wspomniano w sekcji "Podstawowej architektury" tego tematu, w ramach usługi jest częścią [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , między innymi, jest odpowiedzialny za konwertowanie model programowania przyjazną dla użytkownika komunikat danych i rzeczywistych `Message` wystąpienia. Zazwyczaj wymiany wiadomości jest reprezentowana w ramach usługi jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metoda oznaczona atrybutem <xref:System.ServiceModel.OperationContractAttribute> atrybutu. Metoda może zająć w niektórych parametrów i może zwrócić wartości zwracanej ani out (lub obu). Na stronie usługi parametry wejściowe reprezentują wiadomości przychodzącej i wartości zwracanej i parametrów out reprezentują komunikatu wychodzącego. Po stronie klienta odwrotnej ma wartość true. Model programowania dla opisu wiadomości przy użyciu parametrów i wartości zwracanej jest szczegółowo opisane w [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Jednak w tej sekcji zapewni krótkie omówienie.  
  
## <a name="programming-models"></a>Modele programowania  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Struktura usługi obsługuje pięć różne modele programowania dla opisu wiadomości:  
  
### <a name="1-the-empty-message"></a>1. Pusty komunikat  
 Jest to najprostsza. Do opisania pusty komunikat przychodzący, nie używaj parametrów wejściowych.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Do opisania wiadomości wychodzącej puste, użyj pustą wartość zwracaną i nie należy używać żadnego parametry wyjściowe:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Należy pamiętać, że jest inny niż kontraktu jednokierunkowego operację:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 W `SetDesiredTemperature` przykład dwukierunkowe wymiany komunikatów jest opisany. Komunikat jest zwrócony przez operację, ale nie jest pusty. Istnieje możliwość zwraca błąd przez operację. W przykładzie "Ustaw żarówka" wymiany komunikatów jest jednokierunkowa, więc nie ma żadnych komunikatu wychodzącego do opisu. Usługa nie może komunikować się o stanie do klienta w tym przypadku.  
  
### <a name="2-using-the-message-class-directly"></a>2. Używanie klasy Message bezpośrednio  
 Istnieje możliwość użycia <xref:System.ServiceModel.Channels.Message> klasy (lub jeden z jego podklas) bezpośrednio w kontrakt operacji. W takim przypadku po prostu przekazuje struktura usługi `Message` przez operację na stos kanału i odwrotnie, żadne dalsze przetwarzanie nie.  
  
 Istnieją dwa główne zastosowania przy użyciu `Message` bezpośrednio. Umożliwia to dla zaawansowanych scenariuszy, gdy żaden z innymi modelami programowania pozwala za mało opisano wiadomości. Można na przykład opis komunikatu z właściwości pliku staje się nagłówki komunikatów i jego zawartość się coraz treść komunikatu przy użyciu plików na dysku. Następnie można tworzyć coś podobnego do następującego.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 Drugi typowe na użytek `Message` w kontrakt operacji jest Jeśli usługi nie interesują danego komunikatu zawartości i działa w komunikacie na czarne pole. Na przykład może być to usługa, która przekazuje dalej wiadomości do wielu innych odbiorców. Kontrakt można pisać w następujący sposób.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Akcja = "*" wiersz skutecznie wyłącza potrzeby rozsyłania komunikatów i zapewnia, że wszystkie wiadomości wysyłane do `IForwardingService` kontraktu należy ich sposobem `ForwardMessage` operacji. (Zazwyczaj Dyspozytor zbada nagłówka "Akcja" wiadomości do operacji, które jest przeznaczone do określenia. Akcja = "\*" oznacza "wszystkie możliwe wartości nagłówka Action".) Kombinacja akcji = "\*" i za pomocą komunikatu jako parametr nosi nazwę "universal kontraktu", ponieważ jest w stanie wszystkie komunikaty możliwe. Aby móc wysyłać komunikaty możliwe, należy użyć komunikatu jako wartości zwracane i ustawić `ReplyAction` do "\*". Uniemożliwi to struktura usługi Dodawanie nagłówka własnego działania, dzięki któremu można kontrolować przy użyciu tego nagłówka `Message` obiekt powrocie.  
  
### <a name="3-message-contracts"></a>3. Kontrakty komunikatów  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zapewnia model programowania deklaratywne opisujące wiadomości, nazywane *komunikatu kontrakty*. Ten model jest szczegółowo opisane w [za pomocą kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Zasadniczo cały komunikat jest reprezentowane przez jeden [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu, który używa atrybutów, takich jak <xref:System.ServiceModel.MessageBodyMemberAttribute> i <xref:System.ServiceModel.MessageHeaderAttribute> do opisywania części klasy kontraktu komunikatu, które powinny być mapowane na której części wiadomości.  
  
 Kontrakty komunikatu zapewniają dużą kontrolę nad powstałe w ten sposób `Message` wystąpień (chociaż oczywiście nie tak formantu przy użyciu `Message` bezpośrednio klasa). Na przykład treści wiadomości często składają się z wielu rodzajów informacji, każdy jest reprezentowany przez jego własnej — element XML. Te elementy albo mogą występować bezpośrednio w treści (*systemu od zera* tryb) lub może być *opakowana* w tym elemencie XML. Za pomocą kontraktu komunikatu, model programowania umożliwia podjęcie decyzji bez systemu operacyjnego i opakowana i nazwa przestrzeni nazw i nazwa otoki formantu.  
  
 W poniższym przykładzie kodu kontraktu komunikatu pokazano te funkcje.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Elementy oznaczony do serializacji (z <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, lub innych powiązanych atrybutów) muszą mieć możliwość serializowania uczestniczyć w kontrakcie komunikatu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]w sekcji "Serializacji" w dalszej części tego tematu.  
  
### <a name="4-parameters"></a>4. Parametry  
 Często deweloperze, który chce opisuje operację, która działa na wielu fragmentów danych nie jest konieczne stopień kontroli, które zapewniają kontraktów komunikatu. Na przykład podczas tworzenia nowych usług, co nie zwykle chce podjąć decyzję dotyczącą bez systemu operacyjnego i opakowana i zdecydować, nazwa elementu otoki. Podejmowanie tych decyzji często wymaga dokładnego wiedzę na temat usługi sieci Web i SOAP.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Struktura usługi może automatycznie wybrać reprezentacja SOAP najlepszym i najbardziej interoperacyjne do wysyłania i odbierania wielu powiązanych rodzajów informacji, bez wymuszania tych opcji na użytkownika. To jest realizowane przez po prostu opisujące te elementy informacji jako parametry lub zwracać wartości kontrakt operacji. Na przykład należy wziąć pod uwagę następujące kontrakt operacji.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Struktura usługi automatycznie decyduje się wszystkie trzy informacje (`customerID`, `item`, i `quantity`) w treści wiadomości i zawijania je w element otoki o nazwie `SubmitOrderRequest`.  
  
 Informacje, które mają być wysyłane lub odbierane to prosta lista parametrów kontrakt operacji jest zalecane podejście, jeśli nie istnieją specjalne przyczyny można przenieść do kontraktu komunikatu bardziej skomplikowane opisujące lub `Message`— na podstawie modele programowania.  
  
### <a name="5-stream"></a>5. Strumień  
 Przy użyciu `Stream` lub jednej z jego podklas w kontrakt operacji lub w ramach treści wiadomości wyłącznie w kontrakcie komunikatu jest uznawana za oddzielne model programowania z opisane powyżej. Przy użyciu `Stream` w ten sposób jest jedynym sposobem zagwarantowania, że Umowa będzie można używać w sposób przesyłany strumieniowo, jest zbyt mała pisanie własnych przesyłania strumieniowego zgodnego `Message` podklasy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Dużej ilości danych i przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Gdy `Stream` lub jednej z jego podklas jest używany w ten sposób, nie zostanie wywołany element serializujący. Dla komunikatów wychodzących, specjalne przesyłania strumieniowego `Message` podklasy jest tworzony i strumień jest zapisywany limit zgodnie z opisem w sekcji na <xref:System.Xml.IStreamProvider> interfejsu. Dla komunikatów przychodzących, tworzy struktura usługi `Stream` podklasy za pośrednictwem wiadomości przychodzącej i udostępnia go wykonać operację.  
  
## <a name="programming-model-restrictions"></a>Ograniczenia modelu programowania  
 Modele programowania opisane powyżej, nie można łączyć arbitralnie. Na przykład jeśli operacja akceptuje typ kontraktu komunikatu, kontraktu komunikatu musi być jego tylko parametr wejściowy. Ponadto operacji musi być następnie zwracany jest pusty komunikat (zwracanego typu void) lub innej kontraktu komunikatu. Ograniczenia te modelu programowania są opisane w tematach dla każdego określonego modelu programowania: [za pomocą kontraktów komunikatu](../../../../docs/framework/wcf/feature-details/using-message-contracts.md), [używanie klasy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md), i [duże ilości danych i przesyłania strumieniowego ](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Elementy formatujące komunikaty  
 Modele programowania opisane powyżej są obsługiwane przez podłączenie składniki o nazwie *komunikatu elementy formatujące* w ramach usługi. Elementy formatujące komunikaty są typy, które implementują <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> lub <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejsu i/lub dla klientów i usług [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, odpowiednio.  
  
 Elementy formatujące komunikaty są zwykle podłączone przez zachowania. Na przykład <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> podłącza programu formatującego kontraktu danych. To zrobić na stronie usługi, ustawiając <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> do poprawny element formatujący w <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> metody, lub po stronie klienta, ustawiając <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> do poprawny element formatujący w <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> — metoda.  
  
 Poniższe tabele zawierają listę metod, które mogą zaimplementować programu formatującego.  
  
|Interface|Metoda|Akcja|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Konwertuje przychodzące `Message` parametrów operacji|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Tworzy wychodzące `Message` wartość zwracana z operacji/out parametrów|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Tworzy wychodzące `Message` z parametrów operacji|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Konwertuje przychodzące `Message` do wartości zwracanej/parametrów out|  
  
## <a name="serialization"></a>Serializacja  
 Zawsze, gdy używasz kontraktów komunikatu lub parametrów do opisywania treść wiadomości, należy użyć serializacji w celu konwersji między [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy i reprezentacji XML typu Infoset. Serializacja jest używana w innych miejscach w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], na przykład <xref:System.ServiceModel.Channels.Message> ma ogólnego <xref:System.ServiceModel.Channels.Message.GetBody%2A> metodę, która służy do odczytu treści cały komunikat deserializacji do obiektu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje dwie technologie serializacji "fabrycznej" serializację i deserializację parametrów i części wiadomości: <xref:System.Runtime.Serialization.DataContractSerializer> i `XmlSerializer`. Ponadto można pisać niestandardowe serializatorów. Jednak inne części [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (takich jak ogólnego `GetBody` metody lub protokołu SOAP fault serializacji) może być ograniczony do użycia tylko <xref:System.Runtime.Serialization.XmlObjectSerializer> podklasy (<xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer>, ale nie <xref:System.Xml.Serialization.XmlSerializer>), lub może być ustalony używana będzie tylko <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 `XmlSerializer` Jest używany mechanizm serializacji w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web. `DataContractSerializer` Jest nowy aparat serializacji, która obsługuje usługę nowy model programowania kontraktu danych. `DataContractSerializer`wybór domyślny i decyzja o korzystaniu z `XmlSerializer` można wprowadzić na podstawie na operację przy użyciu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> atrybutu.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> są zobowiązani do podłączania elementy formatujące komunikaty dla zachowania operacji `DataContractSerializer` i `XmlSerializer`odpowiednio. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Zachowanie faktycznie mogą pracować z dowolnego serializator, która pochodzi z <xref:System.Runtime.Serialization.XmlObjectSerializer>, takie jak <xref:System.Runtime.Serialization.NetDataContractSerializer> (opisano szczegółowo w za pomocą serializacji autonomicznego). Jeden z wywołuje `CreateSerializer` przeciążenia metody wirtualnej uzyskanie serializatora. Aby dołączyć innego serializatora, Utwórz nową <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> podklasy i zastąpienie `CreateSerializer` przeciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
