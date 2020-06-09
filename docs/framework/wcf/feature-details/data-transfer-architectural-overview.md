---
title: Omówienie architektury transferu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: f34bf82ec44140827c5d8da59911afe10ab7a853
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576476"
---
# <a name="data-transfer-architectural-overview"></a>Omówienie architektury transferu danych
Windows Communication Foundation (WCF) może być uważana za infrastrukturę obsługi komunikatów. Może on odbierać komunikaty, przetwarzać je i wysyłać do kodu użytkownika w celu wykonania dalszych działań lub może tworzyć komunikaty z danych podanymi przez kod użytkownika i dostarczać je do miejsca docelowego. W tym temacie, który jest przeznaczony dla zaawansowanych deweloperów, opisano architekturę obsługi komunikatów i zawartych danych. Aby uprościć widok zorientowany na zadania, jak wysyłać i odbierać dane, zobacz [określanie transfer danych w umowach dotyczących usług](specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
> W tym temacie omówiono szczegóły implementacji WCF, które nie są widoczne przez badanie modelu obiektów WCF. Dwa słowa przestroga są w porządku w odniesieniu do udokumentowanych szczegółów implementacji. Najpierw opisy są uproszczone; Rzeczywista implementacja może być bardziej złożona ze względu na optymalizacje lub inne powody. W drugim przypadku nigdy nie należy polegać na określonych szczegółach implementacji, nawet udokumentowanych, ponieważ mogą one ulec zmianie bez powiadomienia z wersji do wersji, a nawet w wersji z obsługą techniczną.  
  
## <a name="basic-architecture"></a>Podstawowa architektura  
 Na podstawowym poziomie funkcji obsługi komunikatów WCF jest <xref:System.ServiceModel.Channels.Message> Klasa, która jest opisana szczegółowo w temacie using the [Message Class](using-the-message-class.md). Składniki środowiska uruchomieniowego WCF można podzielić na dwie główne części: stos kanału i środowisko usługi z <xref:System.ServiceModel.Channels.Message> klasą punktu połączenia.  
  
 Stos kanału jest odpowiedzialny za konwersję między prawidłowym <xref:System.ServiceModel.Channels.Message> wystąpieniem a pewną akcją, która odnosi się do wysyłania lub otrzymywania danych komunikatów. Po stronie wysyłającej stos kanału jest prawidłowym <xref:System.ServiceModel.Channels.Message> wystąpieniem, a po pewnym przetwarzaniu wykonuje pewne działania, które logicznie odpowiadają na wysłanie komunikatu. Akcja może wysyłać pakiety TCP lub HTTP, kolejkować wiadomość w usłudze kolejkowania komunikatów, zapisywać komunikat do bazy danych, zapisywać ją w udziale plików lub dowolną inną akcję, w zależności od implementacji. Najbardziej typowa akcja wysyła komunikat za pośrednictwem protokołu sieciowego. Po stronie odbierającej następuje wykrycie działania (które może być pakietem TCP lub HTTP, który dociera lub jakąkolwiek inną akcją), a po przetworzeniu stos kanału konwertuje tę akcję na prawidłowe <xref:System.ServiceModel.Channels.Message> wystąpienie.  
  
 Możesz użyć programu WCF, używając <xref:System.ServiceModel.Channels.Message> klasy i stosu kanału bezpośrednio. Jednak taka operacja jest trudna i czasochłonna. Ponadto obiekt nie <xref:System.ServiceModel.Channels.Message> zapewnia obsługi metadanych, dlatego nie można generować klientów WCF o jednoznacznie określonym typie, jeśli używasz WCF w ten sposób.  
  
 W związku z tym WCF zawiera platformę usługi, która zapewnia łatwy w użyciu model programowania, który służy do konstruowania i odbierania `Message` obiektów. Struktura usługi mapuje usługi do .NET Framework typów za pomocą koncepcji kontraktów usługi i wysyła komunikaty do operacji użytkownika, które są po prostu .NET Framework metodami oznaczonymi <xref:System.ServiceModel.OperationContractAttribute> atrybutem (Aby uzyskać więcej informacji, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md)). Metody te mogą mieć parametry i wartości zwracane. Po stronie usługi, struktura usługi konwertuje <xref:System.ServiceModel.Channels.Message> wystąpienia przychodzące na parametry i konwertuje wartości zwracane na wystąpienia wychodzące <xref:System.ServiceModel.Channels.Message> . Po stronie klienta działa odwrotnie. Rozważmy na przykład `FindAirfare` operację poniżej.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Załóżmy `FindAirfare` , że jest wywoływana na kliencie. Struktura usługi na kliencie konwertuje `FromCity` `ToCity` Parametry i na wystąpienie wychodzące <xref:System.ServiceModel.Channels.Message> i przekazuje je do stosu kanału do wysłania.  
  
 Po stronie usługi, gdy <xref:System.ServiceModel.Channels.Message> wystąpienie dociera do stosu kanału, struktura usługi wyodrębni odpowiednie dane z komunikatu w celu wypełnienia `FromCity` parametrów i, `ToCity` a następnie wywołuje metodę po stronie usługi `FindAirfare` . Gdy metoda zwraca, platforma usług pobiera zwróconą wartość całkowitą i `IsDirectFlight` parametr wyjściowy oraz tworzy <xref:System.ServiceModel.Channels.Message> wystąpienie obiektu, które zawiera te informacje. Następnie przekazuje `Message` wystąpienie do stosu kanału w celu wysłania ich z powrotem do klienta.  
  
 Po stronie klienta <xref:System.ServiceModel.Channels.Message> wystąpienie zawierające komunikat odpowiedzi jest wychodzą ze stosu kanału. Struktura usługi wyodrębnia wartość zwracaną oraz `IsDirectFlight` wartość i zwraca je do obiektu wywołującego klienta.  
  
## <a name="message-class"></a>Message, klasa  
 <xref:System.ServiceModel.Channels.Message>Klasa powinna być abstrakcyjną reprezentacją komunikatu, ale jego konstrukcja jest silnie związana z komunikatem protokołu SOAP. A <xref:System.ServiceModel.Channels.Message> zawiera trzy główne elementy informacji: treść komunikatu, nagłówki komunikatów i właściwości wiadomości.  
  
## <a name="message-body"></a>Treść komunikatu  
 Treść komunikatu jest przeznaczona do reprezentowania rzeczywistego ładunku danych wiadomości. Treść wiadomości jest zawsze reprezentowana jako sprawdzonych XML. Nie oznacza to, że wszystkie komunikaty utworzone lub odebrane w usłudze WCF muszą być w formacie XML. Na stosie kanałów można zdecydować, jak interpretować treść wiadomości. Może go emitować jako plik XML, przekonwertować go na inny format lub nawet całkowicie pominąć. Oczywiście w przypadku większości powiązań WCF treść komunikatu jest reprezentowana jako zawartość XML w sekcji treść koperty protokołu SOAP.  
  
 Należy pamiętać, że `Message` Klasa nie musi zawierać buforu z danymi XML reprezentującymi treść. Logicznie `Message` zawiera sprawdzonych XML, ale ten sprawdzonych może być dynamicznie skonstruowany i może nigdy nie istnieć fizycznie w pamięci.  
  
### <a name="putting-data-into-the-message-body"></a>Umieszczanie danych w treści wiadomości  
 Nie istnieje jednolity mechanizm umieszczania danych w treści wiadomości. <xref:System.ServiceModel.Channels.Message>Klasa ma metodę abstrakcyjną, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> która przyjmuje <xref:System.Xml.XmlDictionaryWriter> . Każda podklasa <xref:System.ServiceModel.Channels.Message> klasy jest odpowiedzialna za zastąpienie tej metody i zapisanie jej własnej zawartości. Treść komunikatu logicznie zawiera sprawdzonych XML, który `OnWriteBodyContent` tworzy. Rozważmy na przykład następującą `Message` podklasę.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fizycznie `AirfareRequestMessage` wystąpienie zawiera tylko dwa ciągi ("FromCity" i "ToCity"). Jednak logicznie komunikat zawiera następujący sprawdzonych XML:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Oczywiście zazwyczaj nie można tworzyć komunikatów w ten sposób, ponieważ można użyć struktury usługi do utworzenia komunikatu tak jak powyżej, z parametrów kontraktu operacji. Ponadto <xref:System.ServiceModel.Channels.Message> Klasa ma `CreateMessage` metody statyczne, których można użyć do tworzenia komunikatów o wspólnych typach zawartości: pusty komunikat, komunikat zawierający obiekt Zserializowany do XML z <xref:System.Runtime.Serialization.DataContractSerializer> , komunikat zawierający błąd protokołu SOAP, komunikat zawierający kod XML reprezentowany przez itd <xref:System.Xml.XmlReader> .  
  
### <a name="getting-data-from-a-message-body"></a>Pobieranie danych z treści wiadomości  
 Dane przechowywane w treści wiadomości można wyodrębnić na dwa sposoby:  
  
- Całą treść komunikatu można pobrać jednocześnie przez wywołanie <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> metody i przekazanie do składnika zapisywania XML. Pełna treść komunikatu jest zapisywana dla tego składnika zapisywania. Jednoczesne pobranie całej treści wiadomości jest również nazywane *pisaniem wiadomości*. Pisanie odbywa się przede wszystkim przez stos kanałów podczas wysyłania komunikatów — część stosu kanału zwykle uzyskuje dostęp do całej treści wiadomości, koduje ją i wysyła.  
  
- Innym sposobem uzyskania informacji z treści wiadomości jest wywołanie <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> i uzyskanie czytnika XML. Treść komunikatu może następnie być dostępna sekwencyjnie, w razie konieczności, wywołując metody z czytnika. Pobieranie treści komunikatu przez element jest również nazywane *odczytywaniem wiadomości*. Odczytywanie wiadomości jest przede wszystkim używany przez strukturę usługi podczas otrzymywania wiadomości. Na przykład gdy <xref:System.Runtime.Serialization.DataContractSerializer> jest używany, środowisko usługi pobierze czytnik XML nad treścią i przekaże go do aparatu deserializacji, który następnie rozpocznie odczytywanie komunikatu po elemencie i konstruowanie odpowiedniego grafu obiektów.  
  
 Treść komunikatu można pobrać tylko raz. Dzięki temu można korzystać z strumieni tylko do przesyłania dalej. Na przykład można napisać <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> przesłonięcie, które odczytuje z <xref:System.IO.FileStream> i zwraca wyniki jako sprawdzonych XML. Na początku pliku nigdy nie będzie konieczne przewinięcie do tyłu.  
  
 `WriteBodyContents`Metody i `GetReaderAtBodyContents` po prostu sprawdzają, czy treść wiadomości nigdy nie została wcześniej pobrana, a następnie Wywołaj `OnWriteBodyContents` lub `OnGetReaderAtBodyContents` .  
  
## <a name="message-usage-in-wcf"></a>Użycie komunikatów w programie WCF  
 Większość komunikatów może być sklasyfikowanych jako *wychodzące* (te, które są tworzone przez strukturę usługi do wysłania przez stos kanałów) lub *przychodzące* (te, które docierają do stosu kanału i są interpretowane przez strukturę usługi). Ponadto stos kanału może działać w trybie buforowanym lub przesyłania strumieniowego. Platforma usług może również uwidaczniać strumieniowy lub niestrumieniowy model programowania. Prowadzi to do przypadków wymienionych w poniższej tabeli wraz z uproszczonymi szczegółami ich implementacji.  
  
|Typ wiadomości|Dane treści w wiadomości|Implementacja zapisu (OnWriteBodyContents)|Odczytaj (OnGetReaderAtBodyContents) implementację|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Wychodzące, utworzone na podstawie nieprzesyłanego modelu programowania|Dane niezbędne do zapisania wiadomości (na przykład obiektu i <xref:System.Runtime.Serialization.DataContractSerializer> wystąpienia niezbędnego do serializacji) *|Logika niestandardowa umożliwiająca zapisanie wiadomości na podstawie przechowywanych danych (na przykład wywołania `WriteObject` w `DataContractSerializer` przypadku użycia serializatora) *|Wywołaj `OnWriteBodyContents` , przebuforuj wyniki, zwróć czytnik XML na bufor|  
|Wychodzące, utworzone na podstawie przesyłanego modelu programowania|`Stream`Z danymi, które mają być zapisywane *|Zapisuj dane z zapisanego strumienia przy użyciu <xref:System.Xml.IStreamProvider> mechanizmu *|Wywołaj `OnWriteBodyContents` , przebuforuj wyniki, zwróć czytnik XML na bufor|  
|Przychodzące ze stosu kanału przesyłania strumieniowego|`Stream`Obiekt, który reprezentuje dane przychodzące za pośrednictwem sieci z <xref:System.Xml.XmlReader>|Zapisz zawartość z przechowywanych `XmlReader` przy użyciu`WriteNode`|Zwraca przechowywane`XmlReader`|  
|Przychodzące z niestrumieniowego stosu kanału|Bufor zawierający dane treści z `XmlReader`|Zapisuje zawartość z przechowywanych `XmlReader` przy użyciu`WriteNode`|Zwraca przechowywany plik lang|  
  
 \*Te elementy nie są implementowane bezpośrednio w `Message` podklasach, ale w podklasach <xref:System.ServiceModel.Channels.BodyWriter> klasy. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.BodyWriter> , zobacz [Korzystanie z klasy Message](using-the-message-class.md).  
  
## <a name="message-headers"></a>Nagłówki komunikatów  
 Komunikat może zawierać nagłówki. Nagłówek logicznie składa się z sprawdzonych XML, który jest skojarzony z nazwą, przestrzenią nazw i kilkoma innymi właściwościami. Do nagłówków wiadomości uzyskuje się dostęp przy użyciu `Headers` właściwości w <xref:System.ServiceModel.Channels.Message> . Każdy nagłówek jest reprezentowany przez <xref:System.ServiceModel.Channels.MessageHeader> klasę. Zwykle nagłówki wiadomości są mapowane na nagłówki wiadomości protokołu SOAP, gdy używany jest stos kanału skonfigurowany do pracy z komunikatami protokołu SOAP.  
  
 Umieszczenie informacji w nagłówku wiadomości i wyodrębnienie informacji jest podobne do użycia treści komunikatu. Proces jest nieco uproszczony, ponieważ przesyłanie strumieniowe nie jest obsługiwane. Możliwe jest uzyskanie dostępu do zawartości tego samego nagłówka więcej niż raz, a nagłówki mogą być dostępne w dowolnej kolejności, co wymusza, aby nagłówki były zawsze buforowane. Nie istnieje mechanizm ogólnego przeznaczenia, który umożliwia uzyskanie czytnika XML nad nagłówkiem, ale istnieje `MessageHeader` podklasa wewnętrzna dla WCF, która reprezentuje nagłówek z możliwością odczytu. Ten typ `MessageHeader` jest tworzony przez stos kanału po pojawieniu się komunikatu z nagłówkami aplikacji niestandardowych. Dzięki temu platforma usług może używać aparatu deserializacji, takiego jak <xref:System.Runtime.Serialization.DataContractSerializer> , do interpretacji tych nagłówków.  
  
 Aby uzyskać więcej informacji, zobacz [Korzystanie z klasy Message](using-the-message-class.md).  
  
## <a name="message-properties"></a>Właściwości komunikatu  
 Komunikat może zawierać właściwości. *Właściwość* jest dowolnym obiektem .NET Framework, który jest skojarzony z nazwą ciągu. Właściwości są dostępne za pomocą `Properties` właściwości w `Message` .  
  
 W przeciwieństwie do treści wiadomości i nagłówków wiadomości (które zwykle mapują odpowiednio do treści protokołu SOAP i nagłówków protokołu SOAP), właściwości wiadomości nie są zwykle wysyłane ani odbierane wraz z komunikatami. Właściwości wiadomości istnieją głównie jako mechanizm komunikacji do przekazywania danych o wiadomości między różnymi kanałami w stosie kanału oraz między stosem kanału i modelem usługi.  
  
 Na przykład kanał transportu HTTP dołączony jako część WCF ma możliwość tworzenia różnych kodów stanu HTTP, takich jak "404 (nie znaleziono)" i "500 (wewnętrzny błąd serwera)," podczas wysyłania odpowiedzi do klientów. Przed wysłaniem komunikatu odpowiedzi sprawdza, czy element `Properties` `Message` zawiera właściwość o nazwie "HttpResponse", która zawiera obiekt typu <xref:System.ServiceModel.Channels.HttpResponseMessageProperty> . Jeśli taka właściwość zostanie znaleziona, zobaczy <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> Właściwość i użyje tego kodu stanu. Jeśli nie zostanie znaleziona, zostanie użyty domyślny kod "200 (OK)".  
  
 Aby uzyskać więcej informacji, zobacz [Korzystanie z klasy Message](using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Wiadomość jako całość  
 Do tej pory omawiamy metody uzyskiwania dostępu do różnych części komunikatu w izolacji. Jednak <xref:System.ServiceModel.Channels.Message> Klasa zawiera również metody do pracy z całą wiadomością jako całość. Na przykład `WriteMessage` Metoda zapisuje cały komunikat do składnika zapisywania XML.  
  
 Aby to było możliwe, należy zdefiniować mapowanie między całym `Message` wystąpieniem a sprawdzonych XML. Takie mapowanie, w rzeczywistości, istnieje: WCF używa standardu SOAP do definiowania tego mapowania. Gdy `Message` wystąpienie jest zapisywane jako sprawdzonych XML, wynikiem sprawdzonych jest prawidłowa Koperta protokołu SOAP, która zawiera komunikat. W ten sposób `WriteMessage` zwykle wykonaj następujące czynności:  
  
1. Napisz tag otwierającego elementu koperty protokołu SOAP.  
  
2. Napisz tag otwierający element nagłówka SOAP, Wypisz wszystkie nagłówki i Zamknij element header.  
  
3. Napisz tag otwierającego elementu treści protokołu SOAP.  
  
4. Wywołaj `WriteBodyContents` lub równoważną metodę zapisywania treści.  
  
5. Zamknij elementy treści i formy.  
  
 Powyższe kroki są ściśle powiązane ze standardem protokołu SOAP. Jest to skomplikowane przez fakt, że istnieje wiele wersji protokołu SOAP, na przykład nie można zapisać elementu koperty protokołu SOAP prawidłowo, bez znajomości używanej wersji protokołu SOAP. Ponadto w niektórych przypadkach może być pożądane, aby całkowicie wyłączyć złożone mapowanie specyficzne dla protokołu SOAP.  
  
 W tym celu `Version` Właściwość jest dostępna w `Message` . Można ją ustawić na wersję protokołu SOAP, która ma być używana podczas zapisywania wiadomości lub można ją ustawić, aby `None` zapobiec jakimkolwiek mapowaniem specyficznym dla protokołu SOAP. Jeśli `Version` Właściwość jest ustawiona na `None` , metody, które współdziałają z całym komunikatem, działają tak jak wtedy, gdy komunikat składa się tylko z jego treści, na przykład `WriteMessage` po prostu wywołuje `WriteBodyContents` zamiast wykonywania wielu kroków wymienionych powyżej. Oczekuje się, że w przypadku wiadomości przychodzących `Version` zostanie on wykryty i poprawnie ustawiony.  
  
## <a name="the-channel-stack"></a>Stos kanału  
  
### <a name="channels"></a>Kanały  
 Jak wspomniano wcześniej, stos kanału jest odpowiedzialny za konwertowanie <xref:System.ServiceModel.Channels.Message> wystąpień wychodzących na niektóre akcje (takie jak wysyłanie pakietów przez sieć) lub konwertowanie niektórych akcji (takich jak otrzymywanie pakietów sieciowych) na wystąpienia przychodzące `Message` .  
  
 Stos kanału składa się z co najmniej jednego kanału uporządkowanego w sekwencji. Wystąpienie wychodzące `Message` jest przekazywane do pierwszego kanału w stosie (nazywanego również *kanałem najwyższego*poziomu), który przekazuje go do następnego kanału w dół w stosie i tak dalej. Komunikat kończy się w ostatnim kanale, który jest nazywany *kanałem transportu*. Komunikaty przychodzące pochodzą z kanału transportowego i są przesyłane z kanału w celu uzyskania kanału w górę stosu. W kanale najwyższego poziomu komunikat jest zwykle przesyłany do struktury usługi. Chociaż jest to typowy wzorzec komunikatów aplikacji, niektóre kanały mogą się nieco różnić, na przykład mogą wysyłać własne komunikaty infrastruktury bez przekazywania komunikatu z kanału powyżej.  
  
 Kanały mogą działać na wiadomości na różne sposoby, gdy przechodzi przez stos. Najbardziej typową operacją jest dodawanie nagłówka do wiadomości wychodzącej i odczytywanie nagłówków w komunikacie przychodzącym. Na przykład kanał może obliczyć podpis cyfrowy wiadomości i dodać go jako nagłówek. Kanał może również sprawdzać ten nagłówek podpisu cyfrowego w komunikatach przychodzących i blokować komunikaty, które nie mają prawidłowego podpisu w celu realizacji stosu kanału. Kanały często ustawiają lub sprawdzają właściwości komunikatów. Treść komunikatu zwykle nie jest modyfikowana, chociaż jest to dozwolone, na przykład kanał zabezpieczeń WCF może zaszyfrować treść wiadomości.  
  
### <a name="transport-channels-and-message-encoders"></a>Kodery przesyłania kanałów i komunikatów  
 Kanał znajdujący się niżej w stosie jest odpowiedzialny za faktyczne transformacje wychodzące <xref:System.ServiceModel.Channels.Message> , jak zmodyfikowano przez inne kanały, do pewnej akcji. Na stronie odbierającej jest to kanał, który konwertuje niektóre akcje na `Message` proces innych kanałów.  
  
 Jak wspomniano wcześniej, działania mogą być różne: wysyłanie lub otrzymywanie pakietów sieciowych przez różne protokoły, odczytywanie lub zapisywanie wiadomości w bazie danych lub kolejkowanie lub dekolejkowanie komunikatu w kolejce usługi kolejkowania komunikatów, aby podać, ale kilka przykładów. Wszystkie te akcje są wspólne: wymagają przekształcenia między `Message` wystąpieniem programu WCF i rzeczywistą grupą bajtów, które mogą być wysyłane, odbierane, odczytywane, zapisywane, umieszczane w kolejce lub z kolejki. Proces konwersji a `Message` na grupę bajtów nazywa się *kodowaniem*, a proces odwrotny tworzenia z `Message` grupy bajtów nazywa się *dekodowaniem*.  
  
 Większość kanałów transportowych wykorzystuje składniki zwane *koderami komunikatów* w celu wykonania kodowania i dekodowania. Koder komunikatów jest podklasą <xref:System.ServiceModel.Channels.MessageEncoder> klasy. `MessageEncoder`obejmuje różne `ReadMessage` i `WriteMessage` przeciążenia metod do przekonwertowania między `Message` i grupą bajtów.  
  
 Po stronie wysyłającej kanał transportu buforowania przekazuje `Message` obiekt otrzymany z kanału nad nim `WriteMessage` . Pobiera on tablicę bajtów, która następnie używa do wykonywania akcji (takich jak pakowanie tych bajtów jako prawidłowych pakietów TCP i wysyłanie ich do poprawnego miejsca docelowego). Kanał transportowy przesyłania strumieniowego najpierw tworzy `Stream` (na przykład za pośrednictwem wychodzącego połączenia TCP), a następnie przekazuje zarówno `Stream` i `Message` musi przesłać do odpowiedniego `WriteMessage` przeciążenia, które zapisuje komunikat.  
  
 Po stronie odbierania bufory przesyłania strumieniowego są wyodrębniane z przychodzących bajtów (na przykład z przychodzących pakietów TCP) do tablicy i wywołań `ReadMessage` w celu uzyskania `Message` obiektu, który może przekazywać więcej informacji stosu kanału. Kanał transportu przesyłania strumieniowego tworzy `Stream` obiekt (na przykład strumień sieciowy przez przychodzące połączenie TCP) i przekazuje go do programu `ReadMessage` w celu uzyskania kopii zapasowej `Message` obiektu.  
  
 Separacja kanałów transportowych i kodera komunikatów nie jest obowiązkowa; Istnieje możliwość napisania kanału transportowego, który nie używa kodera komunikatów. Zaletą tego rozbarwień jest jednak łatwość tworzenia kompozycji. Tak długo, jak kanał transportowy używa tylko podstawy <xref:System.ServiceModel.Channels.MessageEncoder> , może współdziałać z dowolnym koderem usługi WCF lub innej firmy. Podobnie ten sam koder może być używany w każdym kanale transportu.  
  
### <a name="message-encoder-operation"></a>Operacja kodera komunikatu  
 Aby opisać Typowe operacje kodera, warto rozważyć następujące cztery przypadki.  
  
|Operacja|Komentarz|  
|---------------|-------------|  
|Kodowanie, buforowane|W trybie buforowanym koder zazwyczaj tworzy bufor o zmiennym rozmiarze, a następnie tworzy na nim składnik zapisywania XML. Następnie wywołuje on <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> zakodowany komunikat, który zapisuje nagłówki, a następnie treść przy użyciu <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> , jak wyjaśniono w poprzedniej sekcji dotyczącej `Message` tego tematu. Zawartość bufora (reprezentowana jako tablica bajtów) jest następnie zwracana do użycia przez kanał transportu.|  
|Kodowanie, przesyłane strumieniowo|W trybie przesyłania strumieniowego operacja jest podobna do powyższego, ale prostsze. Bufor nie jest potrzebny. Składnik zapisywania XML jest zwykle tworzony przez strumień i <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> jest wywoływany w `Message` celu zapisania go w ramach tego składnika zapisywania.|  
|Dekodowanie, buforowane|Podczas dekodowania w trybie buforowanym `Message` zwykle tworzona jest specjalna podklasa, która zawiera dane buforowane. Nagłówki wiadomości są odczytywane i tworzony jest czytnik XML umieszczony w treści komunikatu. To jest czytnik, który zostanie zwrócony z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> .|  
|Dekodowanie, przesyłane strumieniowo|Podczas dekodowania w trybie przesyłania strumieniowego zwykle tworzona jest specjalna podklasa wiadomości. Strumień jest wystarczająco zaawansowany, aby można było odczytać wszystkie nagłówki i umieścić je w treści wiadomości. Obiekt odczytujący XML jest następnie tworzony w strumieniu. To jest czytnik, który zostanie zwrócony z <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> .|  
  
 Kodery mogą również wykonywać inne funkcje. Na przykład kodery mogą mieć pulę czytelników i autorów XML. Tworzenie nowego czytnika lub składnika zapisywania XML jest droższe, gdy jest to konieczne. W związku z tym kodery zwykle utrzymują pulę czytników i pulę modułów zapisujących konfigurowalny rozmiar. W opisach operacji kodera opisanej wcześniej, za każdym razem, gdy zostanie użyta fraza "Tworzenie czytnika XML/składnik zapisywania", zazwyczaj oznacza to, że jest to jedno z puli lub utwórz je, jeśli nie jest dostępna. Koder (i `Message` podklasy tworzone podczas dekodowania) zawierają logikę zwracającą czytelników i autorów do pul, gdy nie są już potrzebne (na przykład gdy `Message` jest zamknięty).  
  
 Funkcja WCF oferuje trzy kodery komunikatów, chociaż istnieje możliwość utworzenia dodatkowych typów niestandardowych. Dostarczone typy to mechanizm optymalizacji tekstu, binarny i przesyłania komunikatów (MTOM). Są one szczegółowo opisane w temacie [Wybieranie kodera komunikatów](choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>Interfejs element IStreamProvider  
 Podczas pisania wiadomości wychodzącej zawierającej przesłaną strumieniowo do składnika zapisywania XML, program <xref:System.ServiceModel.Channels.Message> używa sekwencji wywołań podobnej do następującej w jej <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> implementacji:  
  
- Zapisz wszelkie niezbędne informacje przed strumieniem (na przykład otwierającym tagiem XML).  
  
- Zapisz strumień.  
  
- Napisz wszystkie informacje następujące po strumieniu (na przykład zamykając tag XML).  
  
 Dobrze sprawdza się w przypadku kodowań, które są podobne do tekstu kodowania XML. Jednak niektóre kodowania nie umieszczają informacji sprawdzonych XML (na przykład Tagi dla początkowych i końcowych elementów XML) wraz z danymi zawartymi w elementach. Na przykład w kodowaniu MTOM komunikat jest podzielony na wiele części. Jedna część zawiera sprawdzonych XML, który może zawierać odwołania do innych części dla rzeczywistej zawartości elementu. Sprawdzonych XML jest zwykle mały w porównaniu do zawartości przesyłanej strumieniowo, dlatego warto buforować sprawdzonych, zapisywać go, a następnie zapisywać zawartość w sposób przesyłany strumieniowo. Oznacza to, że przez czas zapisywania znacznika elementu zamykającego nie należy jeszcze zapisywać strumienia.  
  
 W tym celu <xref:System.Xml.IStreamProvider> używany jest interfejs. Interfejs ma <xref:System.Xml.IStreamProvider.GetStream> metodę, która zwraca strumień, który ma zostać zapisany. Prawidłowy sposób zapisania przesyłanej strumieniowo treści wiadomości w programie <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> jest następujący:  
  
1. Zapisz wszelkie niezbędne informacje przed strumieniem (na przykład otwierającym tagiem XML).  
  
2. Wywołaj `WriteValue` Przeciążenie, <xref:System.Xml.XmlDictionaryWriter> które przyjmuje obiekt <xref:System.Xml.IStreamProvider> , z `IStreamProvider` implementacją zwracającą strumień, który ma zostać zapisany.  
  
3. Napisz wszystkie informacje następujące po strumieniu (na przykład zamykając tag XML).  
  
 W tym podejściu składnik zapisywania XML ma możliwość wyboru, kiedy należy wywołać <xref:System.Xml.IStreamProvider.GetStream> i napisać dane przesyłane strumieniowo. Na przykład tekst i binarne moduły zapisujące XML będą natychmiast je wywoływać i zapisywać przesyłane strumieniowo zawartość między tagami początkowymi i końcowymi. Składnik zapisywania MTOM może zdecydować się na <xref:System.Xml.IStreamProvider.GetStream> późniejsze wywołanie, gdy jest gotowy do zapisania odpowiedniej części wiadomości.  
  
## <a name="representing-data-in-the-service-framework"></a>Reprezentuje dane w środowisku usługi  
 Jak określono w sekcji "podstawowa architektura" w tym temacie, struktura usługi jest częścią programu WCF, która między innymi jest odpowiedzialna za konwersję między modelem programowania przyjaznym dla użytkownika a rzeczywistymi `Message` wystąpieniami. Zwykle wymiana komunikatów jest reprezentowana w środowisku usługi jako metoda .NET Framework oznaczona <xref:System.ServiceModel.OperationContractAttribute> atrybutem. Metoda może przyjmować pewne parametry i może zwracać wartość zwracaną lub parametry out (lub oba). Po stronie usługi parametry wejściowe reprezentują komunikat przychodzący, a wartość zwracana i parametry out reprezentują komunikat wychodzący. Po stronie klienta odwrotna wartość jest równa true. Model programowania służący do opisywania komunikatów przy użyciu parametrów i wartości zwracanej opisano szczegółowo w temacie [określanie transfer danych w kontraktach usług](specifying-data-transfer-in-service-contracts.md). Jednak ta sekcja zawiera krótkie omówienie.  
  
## <a name="programming-models"></a>Modele programowania  
 Struktura usługi WCF obsługuje pięć różnych modeli programowania do opisywania komunikatów:  
  
### <a name="1-the-empty-message"></a>1. pusty komunikat  
 Jest to najprostszy przypadek. Aby opisać pusty komunikat przychodzący, nie należy używać żadnych parametrów wejściowych.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Aby opisać pustą wiadomość wychodzącą, należy użyć wartości zwracanej void i nie używać żadnych parametrów out:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Należy zauważyć, że różni się to od kontraktu jednokierunkowej operacji:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 W `SetDesiredTemperature` przykładzie opisany jest wzorzec wymiany komunikatów dwukierunkowych. Komunikat jest zwracany z operacji, ale jest pusty. Możliwe jest zwrócenie błędu z operacji. W przykładzie "Set żarówki" wzorzec wymiany komunikatów jest jednokierunkowy, dlatego nie istnieje komunikat wychodzący do opisania. Usługa nie może skomunikować się z klientem w tym przypadku.  
  
### <a name="2-using-the-message-class-directly"></a>2. bezpośrednie Używanie klasy Message  
 Można użyć <xref:System.ServiceModel.Channels.Message> klasy (lub jednej z jej podklas) bezpośrednio w kontrakcie operacji. W takim przypadku struktura usługi po prostu przekazuje ją `Message` od operacji do stosu kanału i na odwrót, bez dalszej obróbki.  
  
 Istnieją dwa główne przypadki użycia do bezpośredniego użycia `Message` . Można jej użyć w zaawansowanych scenariuszach, gdy żaden z innych modeli programowania nie zapewnia wystarczającej elastyczności opisywania wiadomości. Na przykład możesz chcieć użyć plików na dysku do opisania wiadomości, przy czym właściwości pliku stają się nagłówkami wiadomości, a zawartość pliku staje się treścią wiadomości. Następnie można utworzyć coś podobnego do poniższego.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 Drugim typowym zastosowaniem `Message` w ramach kontraktu operacji jest to, że usługa nie zajmuje się informacjami o określonej zawartości wiadomości i działa na wiadomości jako czarne pole. Na przykład może istnieć usługa, która przesyła dalej komunikaty do wielu innych adresatów. Umowę można napisać w następujący sposób.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 Linia Action = "*" skutecznie wyłącza wysyłanie komunikatów i gwarantuje, że wszystkie komunikaty wysyłane do kontraktu przypracują `IForwardingService` do tej `ForwardMessage` operacji. (Zwykle Dyspozytor przeanalizuje nagłówek "Action" komunikatu, aby określić, która operacja jest przeznaczona dla. Action = " \* " oznacza "wszystkie możliwe wartości nagłówka akcji".) Kombinacja akcji = " \* " i używania komunikatu jako parametru jest znana jako "Umowa uniwersalna", ponieważ może odbierać wszystkie możliwe komunikaty. Aby można było wysyłać wszystkie możliwe komunikaty, należy użyć komunikatu jako wartości zwracanej i ustawić `ReplyAction` na " \* ". Uniemożliwi to platformie usługi dodanie własnego nagłówka akcji, co umożliwia kontrolowanie tego nagłówka przy użyciu `Message` zwracanego obiektu.  
  
### <a name="3-message-contracts"></a>3. kontrakty komunikatów  
 Funkcja WCF oferuje deklaratywny model programowania do opisywania komunikatów, nazywanych *kontraktami komunikatów*. Ten model został szczegółowo opisany w artykule [Używanie kontraktów komunikatów](using-message-contracts.md). Zasadniczo cały komunikat jest reprezentowany przez pojedynczy typ .NET Framework, który używa atrybutów, takich jak <xref:System.ServiceModel.MessageBodyMemberAttribute> i, <xref:System.ServiceModel.MessageHeaderAttribute> do opisywania, które części klasy kontraktu wiadomości powinny mapować, która część komunikatu.  
  
 Umowy dotyczące komunikatów zapewniają dużą kontrolę nad wystąpieniami wynikającymi `Message` (choć nie jest to bardzo dużo formantu jako `Message` bezpośredniego użycia klasy). Na przykład treści komunikatów często składają się z wielu informacji, z których każdy reprezentuje własny element XML. Te elementy mogą wystąpić bezpośrednio w treści (w trybie "*bCzy* ") lub mogą być *opakowane* w element XML obejmujący. Korzystając z modelu programowania kontraktu komunikatów, można podejmować decyzje dotyczące zawiniętej i kontrolowania nazwy otoki i przestrzeni nazw.  
  
 W poniższym przykładzie kodu kontraktu komunikatu przedstawiono te funkcje.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Elementy oznaczone jako serializowane (z <xref:System.ServiceModel.MessageBodyMemberAttribute> , <xref:System.ServiceModel.MessageHeaderAttribute> lub innymi atrybutami powiązanymi) muszą być możliwe do serializacji, aby uczestniczyć w kontrakcie komunikatu. Aby uzyskać więcej informacji, zobacz sekcję "serializacji" w dalszej części tego tematu.  
  
### <a name="4-parameters"></a>4. parametry  
 Często deweloperzy, którzy chcą opisać operację, która działa na wielu fragmentach danych, nie potrzebują kontroli nad tym, że umowy o wiadomości zapewniają. Na przykład podczas tworzenia nowych usług jeden z nich nie ma zazwyczaj podejmowania decyzji bez systemu operacyjnego i decyduje o nazwie elementu otoki. Podejmowanie tych decyzji często wymaga głębokiej znajomości usług sieci Web i protokołu SOAP.  
  
 Struktura usługi WCF może automatycznie wybierać najlepszą i najbardziej międzyplatformową reprezentację protokołu SOAP do wysyłania lub otrzymywania wielu powiązanych informacji, bez wymuszania tych opcji na użytkowniku. Jest to realizowane przez proste opisywanie tych informacji jako parametry lub zwracane wartości kontraktu operacji. Rozważmy na przykład następujący kontrakt operacji.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Struktura usługi automatycznie decyduje się umieścić wszystkie trzy informacje ( `customerID` , `item` , i `quantity` ) w treści wiadomości i otoczyć je w elemencie otoki o nazwie `SubmitOrderRequest` .  
  
 Zalecanym podejściem jest opisywanie informacji, które mają być wysyłane lub odbierane jako prosta lista parametrów kontraktu operacji, chyba że istnieją specjalne powody, aby przejść do bardziej złożonej umowy dotyczącej komunikatów lub `Message` modeli programowania opartych na programie.  
  
### <a name="5-stream"></a>5. Stream  
 Użycie `Stream` lub jedna z jej podklas w kontrakcie operacji lub jako jedyna treść wiadomości w umowie może być traktowana jako oddzielny model programowania od tych opisanych powyżej. Użycie `Stream` w ten sposób jest jedynym sposobem na zagwarantowanie, że kontrakt będzie użyteczny w sposób przesyłany strumieniowo, a w sposób krótszy od pisania własnej podklasy zgodnej z przesyłaniem strumieniowym `Message` . Aby uzyskać więcej informacji, zobacz [dane dotyczące dużych ilości danych i przesyłania strumieniowego](large-data-and-streaming.md).  
  
 Kiedy `Stream` lub jedna z jej podklas jest używana w ten sposób, serializator nie jest wywoływany. W przypadku wiadomości wychodzących tworzona jest specjalna podklasa przesyłania strumieniowego, `Message` a strumień zostaje zapisany zgodnie z opisem w sekcji w <xref:System.Xml.IStreamProvider> interfejsie. W przypadku wiadomości przychodzących Usługa Service Framework tworzy `Stream` podklasę przez komunikat przychodzący i udostępnia ją do operacji.  
  
## <a name="programming-model-restrictions"></a>Ograniczenia modelu programowania  
 Opisane powyżej modele programowania nie mogą być w sposób arbitralny połączone. Na przykład jeśli operacja akceptuje typ kontraktu komunikatu, kontrakt wiadomości musi być jedynym parametrem wejściowym. Ponadto operacja musi zwrócić pusty komunikat (zwracany typ void) lub inny kontrakt komunikatu. Te ograniczenia dotyczące modelu programowania są opisane w tematach dotyczących poszczególnych modeli programowania: [przy użyciu kontraktów komunikatów](using-message-contracts.md), [używania klasy komunikatów](using-the-message-class.md)oraz [dużych ilości danych i przesyłania strumieniowego](large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Elementy formatujące komunikaty  
 Opisane powyżej modele programowania są obsługiwane przez Podłączanie w składnikach programu o nazwie programy *formatujące komunikaty* do struktury usługi. Elementy formatujące komunikatów to typy implementujące <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interfejs lub (lub) do użycia w klientach i klientach usług WCF odpowiednio.  
  
 Elementy formatujące komunikatów są zwykle połączone przez zachowania. Na przykład <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> wtyczki w programie formatującego komunikatów kontraktu danych. Jest to wykonywane po stronie usługi przez ustawienie <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> do poprawnego programu formatującego w <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> metodzie lub po stronie klienta przez ustawienie <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> do poprawnego formatu programu formatującego w <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> metodzie.  
  
 Poniższa tabela zawiera listę metod, które może zaimplementować program formatujący komunikatów.  
  
|Interfejs|Metoda|Akcja|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Konwertuje przychodzące `Message` Parametry operacji|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Tworzy `Message` Parametry wartości/out zwracanego elementu wychodzącego z operacji|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Tworzy parametry wychodzące `Message` z operacji|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Konwertuje przychodzące `Message` do parametrów wartości zwracanej/out|  
  
## <a name="serialization"></a>Serializacja  
 Za każdym razem, gdy korzystasz z kontraktów lub parametrów komunikatów do opisywania zawartości komunikatu, musisz użyć serializacji do konwersji między typami .NET Framework i reprezentacją XML sprawdzonych. Serializacja jest używana w innych miejscach na platformie WCF, na przykład, <xref:System.ServiceModel.Channels.Message> ma metodę rodzajową, <xref:System.ServiceModel.Channels.Message.GetBody%2A> której można użyć do odczytania całej treści komunikatu deserializowanego do obiektu.  
  
 Usługa WCF obsługuje dwie technologie serializacji "poza Box" do serializacji i deserializacji parametrów i części komunikatów: <xref:System.Runtime.Serialization.DataContractSerializer> i `XmlSerializer` . Dodatkowo można napisać Serializatory niestandardowe. Jednak inne części WCF (takie jak Metoda generyczna `GetBody` lub Serializacja błędów SOAP) mogą być ograniczone do korzystania tylko z <xref:System.Runtime.Serialization.XmlObjectSerializer> podklas ( <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> , ale nie do <xref:System.Xml.Serialization.XmlSerializer> ) lub nawet być zakodowane w celu użycia tylko <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 `XmlSerializer`Jest to aparat serializacji używany w usługach sieci Web ASP.NET. `DataContractSerializer`To nowy aparat serializacji, który rozumie nowy model programowania kontraktu danych. `DataContractSerializer`jest to wybór domyślny, a wybór użycia `XmlSerializer` może być wykonywany dla każdej operacji przy użyciu <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> atrybutu.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>i <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> są zachowaniami operacji odpowiedzialnymi za Podłączanie w programie formatującego komunikatów `DataContractSerializer` odpowiednio dla i `XmlSerializer` . <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>Zachowanie może faktycznie działać z dowolnym serializatorem, który pochodzi z <xref:System.Runtime.Serialization.XmlObjectSerializer> , włącznie z <xref:System.Runtime.Serialization.NetDataContractSerializer> (opisany szczegółowo w użyciu serializacji autonomicznej). Zachowanie wywołuje jedną z `CreateSerializer` przeciążeń metody wirtualnej w celu uzyskania serializatora. Aby podłączyć inny Serializator, Utwórz nową <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> podklasę i Zastąp oba `CreateSerializer` przeciążenia.  
  
## <a name="see-also"></a>Zobacz też

- [Określanie transferu danych w kontraktach usług](specifying-data-transfer-in-service-contracts.md)
