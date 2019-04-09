---
title: Wybieranie platformy wymiany komunikatów
ms.date: 03/30/2017
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
ms.openlocfilehash: 98788fb89fc68dc1220d9bf8d9ad89df5ca69e6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157788"
---
# <a name="choosing-a-message-exchange-pattern"></a>Wybieranie platformy wymiany komunikatów
Pierwszym krokiem podczas pisania niestandardowych transportu jest podjęcie decyzji, które *wiadomości programu exchange wzorców* (lub MEPs) są wymagane dla kanału, tworzysz. W tym temacie opisano dostępne opcje, a w tym artykule omówiono różne wymagania. Jest to pierwsze zadanie na liście zadań tworzenia kanału, opisanego w [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Sześć wzorców wymiany komunikatów  
 Istnieją trzy MEPs do wyboru:  
  
-   Datagramów (<xref:System.ServiceModel.Channels.IInputChannel> i <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Korzystając z datagram MEP, klient wysyła komunikat przy użyciu *zostanie wyzwolony i zapomnij* programu exchange. Element zostanie wyzwolony i zapomnij programu exchange to taki, który wymaga potwierdzenia out-of-band skutecznej. Komunikat może zostać utracone podczas przesyłania i nigdy nie dotrzeć do usługi. Jeśli operacja wysyłania zakończy się pomyślnie po stronie klienta, nie gwarantuje to, że zdalny punkt końcowy otrzymał komunikat. Datagram jest elementem konstrukcyjnym podstawowych do obsługi komunikatów, możesz tworzyć własne protokołów na jego podstawie — w tym protokoły niezawodne i bezpieczne protokoły. Implementowanie kanały datagram klientów <xref:System.ServiceModel.Channels.IOutputChannel> implementuje interfejs i usługi kanały datagram <xref:System.ServiceModel.Channels.IInputChannel> interfejsu.  
  
-   Odpowiedź na żądanie (<xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     W tym MEP wiadomość jest wysyłana i odpowiedzi. Wzorzec składa się z pary odpowiedź na żądanie. Odpowiedź na żądanie wywołania przykłady zdalnych wywołań procedur (RPC) i przeglądarka GET żądań. Ten wzorzec jest nazywany również półdupleks. W tym MEP zaimplementuj kanały klientów <xref:System.ServiceModel.Channels.IRequestChannel> i zaimplementować usługi kanały <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplex (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     Dwukierunkowe MEP umożliwia dowolną liczbę wiadomości wysłane przez klienta i odbieranie w dowolnej kolejności. Dwukierunkowego MEP przypomina rozmowy telefonicznej, gdzie każdy wyraz mowy jest komunikat. Obie strony może wysyłać i odbierać w tym MEP, interfejs implementowany przez kanały klient internetowy i usługa jest <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Wybieranie platformy wymiany komunikatów](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Trzy wzorce podstawowe wiadomości programu exchange. Od góry do dołu: datagram, odpowiedź na żądanie i dupleks.  
  
 Każda z tych MEPs może również obsługiwać *sesje*. Sesję (i stosowania <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> typu <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) jest skorelowane wszystkie komunikaty wysłane i odebrane w kanale. Wzorzec odpowiedź na żądanie jest sesję komunikat dwóch autonomicznych, jak żądania i odpowiedzi są powiązane. Z kolei wzorzec odpowiedź na żądanie, który obsługuje sesji oznacza, że wszystkie pary żądanie/odpowiedź, w tym kanale są powiązane ze sobą. Daje w sumie sześć MEPs do wyboru:  
  
-   Datagram  
  
-   Odpowiedź na żądanie  
  
-   Dupleks  
  
-   Datagram z sesjami  
  
-   Odpowiedź na żądanie z sesji  
  
-   Komunikacja dwukierunkowa z sesjami  
  
> [!NOTE]
>  Dla transportu UDP datagram, jest tylko MEP, która jest obsługiwana, ponieważ UDP jest pożar i zapomnij protokołu.  
  
## <a name="sessions-and-sessionful-channels"></a>Sesje i Sessionful kanałów  
 W sieci world istnieją połączeniowy protokołów (na przykład, TCP) i protokoły bez połączenia (na przykład, UDP). Usługi WCF używa sesji termin oznacza abstrakcji logiczne podobne do połączenia. Przekroczono WCF protokoły są podobne do połączeniowy protokołów sieciowych i Bezsesyjne WCF protokoły są podobne do protokołów sieciowych bez połączenia.  
  
 W modelu obiektu kanału każdej sesji logicznej manifesty jako wystąpienie kanału sesji. W związku z tym każdej nowej sesji utworzone przez klienta i zaakceptowane w usłudze odnosi się do nowego kanału sesji na każdej stronie. Na poniższym diagramie przedstawiono, w górnej części, struktura Bezsesyjne kanały, a w dolnej części, struktura zamykania kanałów.  
  
 ![Wybieranie platformy wymiany komunikatów](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Klient tworzy nowego kanału sesji i wysyła komunikat. Na stronie usługi odbiornika kanałów odbiera ten komunikat i wykrywa, czy należy on do nowej sesji więc tworzy nowego kanału sesji i przekazuje go do aplikacji (w odpowiedzi do aplikacji podczas wywoływania AcceptChannel odbiornik kanału). Następnie aplikacja otrzymuje tę wiadomość, a wszystkie kolejne komunikaty wysłane w jednej sesji przez tego samego kanału sesji.  
  
 Innym kliencie (lub tego samego klienta) tworzy nowe sessionful i wysyła komunikat. Odbiornik kanału wykrywa ten komunikat jest w nowej sesji i tworzy nowy kanał sesji, a ten proces jest powtarzany.  
  
 Bez sesji istnieje korelacja kanałów i sesji. W związku z tym odbiornik kanału tworzy tylko jeden kanał, za pomocą którego wszystkie odebrane komunikaty są dostarczane do aplikacji. Nie ma również kolejność, ponieważ nie istnieje żadna sesja, w którym należy utrzymywać kolejność komunikatów. Górna część poprzedniego rysunku przedstawiono Bezsesyjne wiadomości programu exchange.  
  
## <a name="starting-and-terminating-sessions"></a>Uruchamianie i kończenie sesji  
 Sesje są uruchamiane na komputerze klienckim, po prostu tworząc nowy kanał sesji. Są one uruchamiane w usłudze podczas usługa odbiera komunikat, który został wysłany w nowej sesji. Podobnie sesje są kończone przez zamknięcie lub przerywanie kanału sesji.  
  
 Wyjątkiem jest <xref:System.ServiceModel.Channels.IDuplexSessionChannel> używany do wysyłania i odbierania wiadomości we wzorcu dupleksowy, sesji komunikacji. Istnieje możliwość, obok będzie chcesz zatrzymać wysyłanie komunikatów, ale nadal odbierać komunikaty w związku z tym, za pomocą <xref:System.ServiceModel.Channels.IDuplexSessionChannel> istnieje mechanizm, który umożliwia zamknięcie wyjście sesji wskazujący, nie będzie wysyłać więcej wiadomości, ale zachować ją danych wejściowych otwarte, dzięki czemu możesz w dalszym ciągu otrzymywać wiadomości.  
  
 Ogólnie rzecz biorąc sesje zostaną zamknięte po stronie wychodzących i nie po stronie przychodzących. Oznacza to kanałów sesji danych wyjściowych może zostać zamknięty, a tym samym nie pozostawia żadnych śladów zakończenie sesji. Zamknięcie kanału w danych wyjściowych Przekroczono powoduje, że odpowiednie zamykania kanału wejściowego do zwrócenia wartości null do wywoływania aplikacji <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 Jednak zamykania kanałów danych wejściowych nie powinien zostać zamknięty, chyba że <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel> zwraca wartość null, wskazując, że sesja jest już zamknięty. Jeśli <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ma nie zwrócił wartość null, zamykanie sesji kanał wejściowy może zgłosić wyjątek, ponieważ może zostać wyświetlony nieoczekiwane komunikaty podczas zamykania. Jeśli odbiorca chce zakończyć sesję przed nadawcy, powinny wywoływać <xref:System.ServiceModel.ICommunicationObject.Abort%2A> nagle w kanale danych wejściowych, który kończy sesję.  
  
## <a name="writing-sessionful-channels"></a>Zapisywanie Sessionful kanałów  
 Jako autor kanału sesji istnieje kilka rzeczy, które kanał należy wykonać, aby zapewnić sesji. Na stronie wysyłania kanał musi:  
  
-   Dla każdego nowego kanału utworzenie nowej sesji i skojarz go z identyfikatorem nowej sesji, który jest unikatowy ciąg. Lub uzyskać nową sesję z kanału sesji poniżej w stosie.  
  
-   Dla każdej wiadomości wysyłane za pomocą tego kanału Jeśli kanał utworzony sesji (w przeciwieństwie do uzyskania go z warstwy poniżej), należy skojarzyć wiadomości z sesją. Dla protokołu kanałów zazwyczaj jest to wykonywane przez dodanie nagłówka SOAP. Kanały transportu na zwykle odbywa się przez utworzenie nowego połączenia transportu lub dodawanie informacji o sesji protokołu ramek.  
  
-   Dla każdej wiadomości wysyłane za pomocą tego kanału musisz podać gwarancją dostarczania wymienionych powyżej. Jeśli polegasz na kanale poniżej musisz podać sesji przez kanał udostępni również gwarancją dostarczania. Jeśli udostępniasz sesji samodzielnie, należy zaimplementować te gwarancje w ramach usługi protokołu. Ogólnie rzecz biorąc Jeśli piszesz kanału protokołu, który przyjmuje WCF po obu stronach może wymagają warstwy transportowej TCP lub kanał niezawodna obsługa komunikatów i zależą od jednego zapewnienie sesji.  
  
-   Gdy <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> jest wywoływana na kanale, wykonują pracę niezbędne zamknąć sesję przy użyciu określonego limitu czasu lub domyślny. Może to być proste co wywołanie metody <xref:System.ServiceModel.ICommunicationObject.Close%2A> na kanale poniżej możesz (jeśli jest to po prostu sesji są uzyskiwane z niego) lub wysyłania komunikatu protokołu SOAP specjalne lub zamyka połączenie transportu.  
  
-   Gdy <xref:System.ServiceModel.ICommunicationObject.Abort%2A> jest wywoływana na kanale, zakończyć sesję nagle bez wykonywania operacji We/Wy. To może oznaczać, że czynności lub mogą spowodować przerwanie połączenia sieciowego lub innego zasobu.  
  
 Po stronie odbierającej kanał musi:  
  
-   Dla każdego komunikatu przychodzącego odbiornika kanałów musi wykryć sesji, do której należy. Jeśli jest to pierwszy komunikat w sesji, odbiornik kanału, należy utworzyć nowy kanał i przywrócić go z wywołania <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. W przeciwnym razie odbiornika kanałów musi znaleźć istniejącego kanału, który odnosi się do sesji i dostarczenia komunikatu za pośrednictwem tego kanału.  
  
-   Jeśli kanał jest zapewnienie sesji (wraz z gwarancją dostarczania wymagane) stronie odbierającej może być konieczne wykonywać niektórych akcji, takich jak zmienić kolejność komunikatów lub wysyłać potwierdzenia.  
  
-   Gdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana na kanale, wykonują pracę niezbędne zamknąć sesję, określony limit czasu lub domyślny. Może to spowodować wyjątki Jeśli kanał odbiera komunikat podczas oczekiwania na limit czasu zamknięcia wygaśnie. To, ponieważ kanał będzie w stanie zamknięcia po odebraniu wiadomości, dzięki czemu będzie ona zgłaszają.  
  
-   Gdy <xref:System.ServiceModel.ICommunicationObject.Abort%2A> jest wywoływana na kanale, zakończyć sesję nagle bez wykonywania operacji We/Wy. Ponownie to może oznaczać, że czynności lub mogą spowodować przerwanie połączenia sieciowego lub innego zasobu.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md)
