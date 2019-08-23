---
title: Wybieranie platformy wymiany komunikatów
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: 518a21ef34d52ef4b70871ba8bad7876374dd319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951861"
---
# <a name="choosing-a-message-exchange-pattern"></a>Wybieranie platformy wymiany komunikatów
Pierwszym krokiem w przypadku tworzenia niestandardowego transportu jest podjęcie decyzji, które *wzorce wymiany komunikatów* (lub MEPs) są wymagane dla opracowywanego kanału. W tym temacie opisano dostępne opcje i omówiono różne wymagania. Jest to pierwsze zadanie na liście zadań opracowywania kanału opisane w temacie [Tworzenie kanałów](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Wzorce wymiany komunikatów 6  
 Istnieją trzy MEPs do wyboru:  
  
- Datagram (<xref:System.ServiceModel.Channels.IInputChannel> i <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     W przypadku korzystania z unikatowy MEP datagramu klient wysyła komunikat przy użyciu *ognia i zapomni* wymianę. Usługa Fire i zapomnij wymiany jest taka, która wymaga potwierdzenia pomyślnego dostarczenia poza pasmem. Komunikat może zostać utracony podczas przesyłania i nigdy nie docierał do usługi. Jeśli operacja wysyłania zostanie zakończona pomyślnie na końcu klienta, nie gwarantuje to, że zdalny punkt końcowy odebrał komunikat. Datagram jest podstawowym blokiem konstrukcyjnym do obsługi komunikatów, ponieważ można tworzyć własne protokoły na jego podstawie — w tym niezawodne protokoły i bezpieczne protokoły. Kanały datagramów klienta <xref:System.ServiceModel.Channels.IOutputChannel> implementują interfejs i kanały datadatagramu usługi <xref:System.ServiceModel.Channels.IInputChannel> implementują interfejsy.  
  
- Żądanie-odpowiedź (<xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     W tym unikatowy MEP komunikat jest wysyłany, a odpowiedź zostanie odebrana. Wzorzec składa się z par żądanie-odpowiedź. Przykłady wywołań żądania-odpowiedź to zdalne wywołania procedury (RPC) i żądania GET przeglądarki. Ten wzorzec jest również znany jako półdupleks. W tym unikatowy MEP zaimplementowano kanały <xref:System.ServiceModel.Channels.IRequestChannel> klienta i zaimplementowano <xref:System.ServiceModel.Channels.IReplyChannel>kanały usług.  
  
- Duplex (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     UNIKATOWY MEP dupleks umożliwia wysyłanie dowolnej liczby komunikatów przez klienta i odbieranie ich w dowolnej kolejności. UNIKATOWY MEP dupleks jest taka sama jak rozmowa telefoniczna, gdzie każdy wypowiadany wyraz jest komunikatem. Ponieważ obie strony mogą wysyłać i odbierać dane w tym unikatowy MEP, interfejs zaimplementowany przez klienta i kanały usług to <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Wybieranie wzorca wymiany komunikatów](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Trzy podstawowe wzorce wymiany komunikatów. Od góry do dołu: datagram, żądanie-odpowiedź i dupleks.  
  
 Każdy z tych MEPs może również obsługiwać *sesje*. Sesja (i implementacja <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> typu <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) umożliwia skorelowanie wszystkich komunikatów wysłanych i odebranych w kanale. Wzorzec żądanie-odpowiedź jest autonomiczną sesją dwustronicową, ponieważ żądanie i odpowiedź są skorelowane. Z kolei wzorzec żądanie-odpowiedź, który obsługuje sesje, oznacza, że wszystkie pary żądanie/odpowiedź w tym kanale są skorelowane ze sobą. Zapewnia to sześć MEPs do wyboru:  
  
- Odebran  
  
- Żądanie-odpowiedź  
  
- Dupleks  
  
- Datagram z sesjami  
  
- Żądanie-odpowiedź z sesjami  
  
- Dupleks z sesjami  
  
> [!NOTE]
> W przypadku transportu UDP jedyną obsługiwaną unikatowy MEPą jest datagram, ponieważ protokół UDP jest z natury i zapomnij.  
  
## <a name="sessions-and-sessionful-channels"></a>Sesje i kanały sesji  
 W świecie sieci dostępne są protokoły zorientowane na połączenia (na przykład TCP) i protokoły bez połączenia (na przykład UDP). Funkcja WCF używa sesji do oznaczania logicznego abstrakcji. Protokoły WCF w sesji są podobne do protokołów sieciowych zorientowanych na połączenia, a protokoły WCF bez sesji są podobne do protokołów sieciowych bez połączenia.  
  
 W modelu obiektu kanału każdy manifest sesji logicznej jest wystąpieniem kanału sesji. W związku z tym każda nowa sesja utworzona przez klienta i zaakceptowana w usłudze odnosi się do nowego kanału sesji na każdej stronie. Na poniższym diagramie pokazano, w górnej części, struktura kanałów bezsesyjnych i na dole, struktura kanałów sesji.  
  
 ![Wybieranie wzorca wymiany komunikatów](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Klient tworzy nowy kanał sesji i wysyła komunikat. Po stronie usługi odbiornik kanału otrzymuje ten komunikat i wykryje, że należy on do nowej sesji, aby utworzyć nowy kanał sesji i skontaktować się z nim do aplikacji (w odpowiedzi na aplikację wywołującą AcceptChannel na odbiorniku kanału). Następnie aplikacja odbiera ten komunikat i wszystkie kolejne komunikaty wysyłane w ramach tej samej sesji za pośrednictwem tego samego kanału sesji.  
  
 Inny klient (lub ten sam Klient) tworzy nową sesję i wysyła komunikat. Odbiornik kanału wykrywa, że ten komunikat jest w nowej sesji i tworzy nowy kanał sesji, a proces powtarza się.  
  
 Bez sesji nie ma korelacji między kanałami i sesjami. W związku z tym odbiornik kanału tworzy tylko jeden kanał, za pośrednictwem którego wszystkie odebrane komunikaty są dostarczane do aplikacji. Nie ma również kolejności komunikatów, ponieważ nie ma sesji, w której ma być zachowana kolejność komunikatów. W górnej części poprzedniej ilustracji przedstawiono wymianę komunikatów bezsesyjnych.  
  
## <a name="starting-and-terminating-sessions"></a>Uruchamianie i przerywanie sesji  
 Sesje są uruchamiane na kliencie przez po prostu utworzenie nowego kanału sesji. Są one uruchamiane w usłudze, gdy usługa otrzymuje komunikat wysłany w nowej sesji. Podobnie sesje są kończone przez zamknięcie lub przerwanie kanału sesji.  
  
 Wyjątkiem jest <xref:System.ServiceModel.Channels.IDuplexSessionChannel> to, który jest używany do wysyłania i otrzymywania wiadomości w postaci dwustronnego, wzorca komunikacji z sesją. Istnieje możliwość, że jedna strona będzie zatrzymywać wysyłanie komunikatów, ale nadal otrzymuje komunikaty, w związku <xref:System.ServiceModel.Channels.IDuplexSessionChannel> z czym jest mechanizm, który umożliwia zamknięcie sesji wyjściowej wskazującej, że nie wyśle więcej komunikatów, ale utrzymuje sesję wejściową otwarte, co pozwoli na kontynuowanie odbierania wiadomości.  
  
 Ogólnie rzecz biorąc, sesje są zamknięte po stronie wychodzącej, a nie na stronie przychodzącej. Oznacza to, że kanały wyjściowe sesji można zamknąć, co oznacza całkowite zakończenie sesji. Zamknięcie kanału wyjściowego sesji powoduje, że odpowiedni kanał wejściowy sesji zwraca wartość null do aplikacji wywołującej <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.IDuplexSessionChannel>na.  
  
 Jednak kanały wejściowe sesji nie powinny być zamknięte, chyba <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> że <xref:System.ServiceModel.Channels.IDuplexSessionChannel> na zwraca wartość null, wskazując, że sesja jest już zamknięta. <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> Jeśli<xref:System.ServiceModel.Channels.IDuplexSessionChannel> na serwerze nie zwrócono wartości null, zamknięcie kanału wejściowego sesji może zgłosić wyjątek, ponieważ może on otrzymywać nieoczekiwane komunikaty podczas zamykania. Jeśli odbiorca chce zakończyć sesję przed wykonaniem nadawcy, powinien wywołać <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kanał wejściowy, który nagle kończy sesję.  
  
## <a name="writing-sessionful-channels"></a>Zapisywanie kanałów sesji  
 Jako autor kanału sesji, istnieje kilka rzeczy, które musi wykonać kanał, aby zapewnić sesje. Na stronie wysyłanie kanał musi:  
  
- Dla każdego nowego kanału Utwórz nową sesję i skojarz ją z nowym identyfikatorem sesji, który jest unikatowym ciągiem. Lub Uzyskaj nową sesję z kanału sesji poniżej użytkownika w stosie.  
  
- Dla każdego komunikatu wysyłanego za pomocą tego kanału, jeśli Kanał utworzył sesję (w przeciwieństwie do uzyskania jej z warstwy poniżej), należy skojarzyć komunikat z sesją. W przypadku kanałów protokołu zwykle odbywa się to przez dodanie nagłówka SOAP. W przypadku kanałów transportowych zwykle odbywa się to przez utworzenie nowego połączenia transportowego lub dodanie informacji o sesji do protokołu ramek.  
  
- Dla każdej wiadomości wysyłanej przy użyciu tego kanału należy podać gwarancje dostarczenia wymienione powyżej. Jeśli korzystasz z kanału poniżej, aby zapewnić sesję, ten kanał zapewni również gwarancje dostarczenia. Jeśli sesja jest dostarczana samodzielnie, należy zaimplementować te gwarancje jako część protokołu. Ogólnie rzecz biorąc, jeśli piszesz kanał protokołu, który przyjmuje WCF na obu stronach, może być konieczne przetransport TCP lub kanał niezawodnej obsługi komunikatów i poleganie na jednym z nich w celu zapewnienia sesji.  
  
- Gdy <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> jest wywoływana w kanale, należy wykonać niezbędne czynności, aby zamknąć sesję przy użyciu określonego limitu czasu lub wartości domyślnej. Może to być równie proste, jak <xref:System.ServiceModel.ICommunicationObject.Close%2A> wywołanie w kanale poniżej (Jeśli właśnie uzyskano sesję) lub wysłanie specjalnego komunikatu protokołu SOAP lub zamknięcie połączenia transportowego.  
  
- Gdy <xref:System.ServiceModel.ICommunicationObject.Abort%2A> jest wywoływana w kanale, Przerwij sesję w nieoczekiwany sposób bez wykonywania operacji we/wy. Może to oznaczać, że nic się nie dzieje, lub może dotyczyć przerwania połączenia sieciowego lub innego zasobu.  
  
 Na stronie odbierającej Twój kanał musi:  
  
- Dla każdego komunikatu przychodzącego odbiornik kanału musi wykryć sesję, do której należy. Jeśli jest to pierwszy komunikat w sesji, odbiornik kanału musi utworzyć nowy kanał i zwrócić go z wywołania do <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. W przeciwnym razie odbiornik kanału musi znaleźć istniejący kanał odpowiadający sesji i dostarczyć komunikat za pośrednictwem tego kanału.  
  
- Jeśli kanał udostępnia sesję (wraz z wymaganymi gwarancjami dostarczania), strona odbierająca może być wymagana do wykonania niektórych akcji, takich jak zmiana kolejności komunikatów lub wysyłanie potwierdzeń.  
  
- Gdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana w kanale, należy wykonać niezbędne czynności, aby zamknąć sesję albo określony limit czasu, albo wartość domyślną. Może to powodować wyjątki, jeśli kanał odbiera komunikat podczas oczekiwania na wygaśnięcie limitu czasu zamykania. Dzieje się tak, ponieważ kanał będzie znajdował się w stanie zamykającym, gdy odbierze komunikat, który mógłby zgłosić.  
  
- Gdy <xref:System.ServiceModel.ICommunicationObject.Abort%2A> jest wywoływana w kanale, Przerwij sesję w nieoczekiwany sposób bez wykonywania operacji we/wy. Może to oznaczać, że nic się nie dzieje, lub może pociągać za sobą przerwanie połączenia sieciowego lub innego zasobu.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md)
