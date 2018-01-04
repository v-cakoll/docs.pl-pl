---
title: "Wybieranie platformy wymiany komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f502ca1-6a8e-4607-ba15-59198c0e6146
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 961f5e84fb46a791127a9d80c0f03d2b87fdea77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="choosing-a-message-exchange-pattern"></a>Wybieranie platformy wymiany komunikatów
Pierwszą czynnością przy tworzeniu niestandardowych transportu jest podjęcie decyzji, które *komunikatu wzorce exchange* (lub MEPs) są wymagane dla kanału tworzysz. W tym temacie opisano dostępne opcje oraz omówiono różne wymagania. Jest to pierwsze zadanie na liście zadań rozwoju kanału opisane w [kanały rozwijających się](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="six-message-exchange-patterns"></a>Sześć wzorców wymiany komunikatów  
 Istnieją trzy MEPs do wyboru:  
  
-   Datagramów (<xref:System.ServiceModel.Channels.IInputChannel> i <xref:System.ServiceModel.Channels.IOutputChannel>)  
  
     Korzystając z datagram MEP, klient wysyła komunikat przy użyciu *wyzwalać i zapomnij* programu exchange. Uruchomienie a zapomnieć exchange to taki, który wymaga potwierdzenia poza pasmem pomyślnie dostawy. Komunikat mogą zostać utracone podczas przesyłania i nigdy nie dotarcia do usługi. Jeśli operacja wysyłania zakończy się pomyślnie po stronie klienta, nie gwarantuje to, że zdalny punkt końcowy odebrał komunikat. Datagram jest bloku konstrukcyjnego podstawowych do obsługi wiadomości, ponieważ można tworzyć własne protokoły na nim — łącznie z protokołów bezpieczne i niezawodne protokoły. Wdrożenie klienta datagram kanałów <xref:System.ServiceModel.Channels.IOutputChannel> implementuje interfejs i Usługa datagramów kanałów <xref:System.ServiceModel.Channels.IInputChannel> interfejsu.  
  
-   Żądanie odpowiedź (<xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel>)  
  
     W tym MEP jest wysyłany komunikat i odpowiedzi. Wzorzec składa się z pary żądanie / odpowiedź. Przykłady wywołań żądań i odpowiedzi są zdalnych wywołań procedur (RPC) i GET przeglądarką żądania. Ten wzorzec jest nazywany również półdupleks. W tym MEP wdrożenia klienta kanałów <xref:System.ServiceModel.Channels.IRequestChannel> i wdrożenie usługi kanałów <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Dupleks (<xref:System.ServiceModel.Channels.IDuplexChannel>)  
  
     Dupleks MEP umożliwia dowolnej liczby wiadomości wysłane przez klienta i odbieranie w dowolnej kolejności. Dupleks MEP przypomina rozmowy telefonicznej każdego wyrazu jest używany w przypadku komunikatu. Ponieważ obie strony może wysyłać i odbierać w tym MEP, interfejs implementowany przez kanały klient i usługa jest <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 ![Wybieranie platformy wymiany komunikatów](../../../../docs/framework/wcf/extending/media/wcfc-basicthreemepsc.gif "wcfc_BasicThreeMEPsc")  
Trzy wzorce exchange podstawowe wiadomości. Z góry na dół: datagram, żądanie odpowiedź i dupleks.  
  
 Każdy z tych MEPs może również obsługiwać *sesji*. Sesja (i stosowania <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> typu <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>) są powiązane z wszystkich wiadomości wysłanych i odebranych na kanale. Wzorzec żądań i odpowiedzi się sesję komunikat dwa autonomiczne skorelowanych żądania i odpowiedzi. Z kolei wzorzec żądań i odpowiedzi, który obsługuje sesji oznacza skorelowanych wszystkie pary żądanie/odpowiedź w tym kanale ze sobą. Daje łączną liczbę sześć MEPs do wyboru:  
  
-   Datagram  
  
-   Żądanie odpowiedź  
  
-   Dupleks  
  
-   Datagram z sesji  
  
-   Żądań i odpowiedzi z sesji  
  
-   Komunikacja dwukierunkowa z sesji  
  
> [!NOTE]
>  Dla transportu UDP tylko MEP, która jest obsługiwana jest datagram, ponieważ jest z założenia fire UDP, a zapomnieć protokołu.  
  
## <a name="sessions-and-sessionful-channels"></a>Sesje i Sessionful kanałów  
 W sieci world istnieją bez połączenia protokołów (na przykład UDP) i nawiązaniem połączenia protokołów (na przykład TCP). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa sesji termin oznacza abstrakcji logiczne typu połączenia. Przekroczono WCF protokoły są podobne do połączeń protokołów sieciowych i Bezsesyjne WCF protokoły są podobne do protokołów sieciowych bez połączenia.  
  
 W modelu obiektu kanału każdej sesji logicznej manifesty jako wystąpienie podczas zamykania kanału sesji. W związku z tym co nowej sesji, które są tworzone przez klienta i zaakceptowane w usłudze odnosi się do nowego podczas zamykania kanału sesji na każdej stronie. Na poniższym diagramie przedstawiono, w górnej części, struktura Bezsesyjne kanałów i u dołu, struktura zamykania kanałów.  
  
 ![Wybieranie platformy wymiany komunikatów](../../../../docs/framework/wcf/extending/media/wcfc-sessionandsessionlesschannelsc.gif "wcfc_SessionAndSessionlessChannelsc")  
  
 Klient tworzy nowy podczas zamykania kanału sesji i wysyła komunikat. Na stronie usługi odbiornika kanałów odbiera ten komunikat i wykrywa, że należy on do nowej sesji tworzy nowy podczas zamykania kanału sesji i przekazuje ją do aplikacji (w odpowiedzi do wywoływania AcceptChannel dla odbiornika kanałów aplikacji). Następnie aplikacja odbiera ten komunikat i wszystkie kolejne wiadomości wysłanych w tej samej sesji przy użyciu tego samego zamykania kanału.  
  
 Inny klient (lub ten sam klient) tworzy nowy sessionful i wysyła komunikat. Odbiornik kanału wykrywa ten komunikat jest w nowej sesji i tworzy nowy podczas zamykania kanału sesji i proces powtarza się.  
  
 Bez sesji Brak korelacja kanałów i sesje. W związku z tym odbiornika kanałów tworzy tylko jeden kanał za pośrednictwem której wszystkie odebrane wiadomości są dostarczane do aplikacji. Nie ma również kolejność, ponieważ nie istnieje żadna sesja w ramach którego do obsługi komunikatów kolejności. Górna część powyższej grafiki przedstawiono exchange Bezsesyjne wiadomości.  
  
## <a name="starting-and-terminating-sessions"></a>Uruchamianie i kończenie sesji  
 Sesje są uruchamiane na komputerze klienckim po prostu, tworząc nowe podczas zamykania kanału sesji. Są one uruchomione usługi, gdy usługa odbiera wiadomość została wysłana w nowej sesji. Podobnie sesje są zakończone przez zamknięcie lub przerywanie podczas zamykania kanału sesji.  
  
 Wyjątkiem jest <xref:System.ServiceModel.Channels.IDuplexSessionChannel> używany zarówno wysyłania i odbierania wiadomości we wzorcu komunikacji dupleksowej, sesyjnych. Istnieje możliwość, po jednej stronie będzie można zatrzymać wysyłanie wiadomości, ale nadal odbierać wiadomości w związku z tym, za pomocą <xref:System.ServiceModel.Channels.IDuplexSessionChannel> istnieje mechanizm, który umożliwia zamknięcie wskazujący sesji danych wyjściowych nie będzie wysyłać więcej wiadomości, ale zachować ją wejściowych otwarty, umożliwiając nadal otrzymywać wiadomości.  
  
 Ogólnie rzecz biorąc sesje zostaną zamknięte po stronie wychodzących, a nie na stronie przychodzących. Oznacza to dane wyjściowe zamykania kanałów może zostać zamknięty, a tym samym prawidłowo przerywanie sesji. Zamknięcie kanału w danych wyjściowych Przekroczono powoduje, że odpowiednie zamykania kanał wejściowy do zwrócenia wartości null do wywoływania aplikacji <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 Jednak zamykania kanałów wejściowych nie powinien zostać zamknięty, chyba że <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel> zwraca wartość null, wskazując, że sesja jest już zamknięty. Jeśli <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ma nie zwróciła wartość null, podczas zamykania kanału wejściowego zamknięcia może zgłosić wyjątek, ponieważ może pojawić się nieoczekiwane komunikaty podczas zamykania. Jeśli odbiornik życzą sobie, aby zakończyć sesję przed nadawcy, powinny wywoływać <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na kanał wejściowy, który nagle zakończenia sesji.  
  
## <a name="writing-sessionful-channels"></a>Zapisywanie Sessionful kanałów  
 Jako autor podczas zamykania kanału sesji istnieje kilka sposobów kanału należy wykonać, aby zapewnić sesji. Po stronie wysyłającej kanału musi:  
  
-   Dla każdego nowego kanału utworzenie nowej sesji i powiązać ją z identyfikatorem nowej sesji, który jest unikatowy ciąg. Lub uzyskać nową sesję z zamykania kanału poniżej w stosie.  
  
-   Jeśli kanał utworzony sesji (w przeciwieństwie do uzyskania go z warstwy poniżej), każdy komunikat jest wysyłany przy użyciu tego kanału, należy skojarzyć wiadomości z sesją. Protokół kanałów jest to zazwyczaj wykonywane przez dodanie nagłówka SOAP. Dla kanały transportu jest to zazwyczaj wykonywane przez utworzenie nowego połączenia transportu lub dodawanie informacji o sesji protokołu ramek.  
  
-   Dla każdego komunikatu wysyłanego przy użyciu tego kanału musisz podać gwarancją dostarczania wymienionych powyżej. Jeśli używasz w kanale poniżej należy podać sesji, tym kanale zawiera również gwarancją dostarczania. Jeśli sesja użytkownika, należy wdrożyć te gwarancje w ramach sieci protokołu. Ogólnie rzecz biorąc podczas pisania kanału protokołu, który przyjmuje WCF po obu stronach może wymagać transportu TCP lub kanału niezawodna obsługa komunikatów i polegać na jedną zapewnienie, sesji.  
  
-   Gdy <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> jest wywoływana na kanał, wykonać niezbędne pracy, aby zamknąć sesję przy użyciu określonego limitu czasu lub domyślny. Może to być równie proste co wywołanie <xref:System.ServiceModel.ICommunicationObject.Close%2A> w kanale poniżej (Jeśli właśnie sesji są uzyskiwane z niego) lub wysyłania komunikatu SOAP specjalnych lub zamykanie połączenia transportu.  
  
-   Gdy <xref:System.ServiceModel.ICommunicationObject.Abort%2A> jest wywoływana na kanał, zakończyć sesję nagle bez wykonywania operacji We/Wy. To może oznaczać, wykonywanie nic lub mogą spowodować przerwanie połączenia sieciowego lub innego zasobu.  
  
 Po stronie odbierania kanału musi:  
  
-   Dla każdej wiadomości przychodzącej odbiornika kanałów musi wykryć sesji, do której należy. Jest to pierwszy komunikat w sesji, odbiornika kanałów należy utworzyć nowy kanał, przywrócić go z wywołania <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType>. W przeciwnym razie odbiornika kanałów musi znaleźć istniejące kanał, który odpowiada sesji i dostarczenie wiadomości za pośrednictwem tego kanału.  
  
-   Jeśli kanał jest zapewnienie sesji (wraz z gwarancją dostarczania wymagane) po stronie odbierania może wymagać do wykonywania pewnych działań, takich jak zmienić kolejność wiadomości lub wysyłania potwierdzeń.  
  
-   Gdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana na kanał, wykonać niezbędne pracy, aby zamknąć sesję określony limit czasu lub domyślny. To może spowodować wystąpienie wyjątków Jeśli kanał odebrał komunikat podczas oczekiwania na limit czasu zamknięcia wygaśnie. Wynika to z kanału będzie w stanie zamknięcia po odebraniu wiadomości, więc go spowoduje zgłoszenie.  
  
-   Gdy <xref:System.ServiceModel.ICommunicationObject.Abort%2A> jest wywoływana na kanał, zakończyć sesję nagle bez wykonywania operacji We/Wy. Ponownie to może oznaczać, wykonywanie nic lub mogą spowodować przerwanie połączenia sieciowego lub innego zasobu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd modelu kanału](../../../../docs/framework/wcf/extending/channel-model-overview.md)
