---
title: "Najlepsze rozwiązania dotyczące sesji niezawodnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea7266cb89a233146217d8cadd85839360351f71
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="best-practices-for-reliable-sessions"></a>Najlepsze rozwiązania dotyczące sesji niezawodnych

W tym temacie omówiono najlepsze rozwiązania dla sesji niezawodnej.

## <a name="setting-maxtransferwindowsize"></a>Ustawienie MaxTransferWindowSize

Niezawodne sesje w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] okno transferu służy do przechowywania wiadomości na klienta i usługi. Można skonfigurować właściwości <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> wskazuje, ile komunikatów okna transfer może przechowywać.

Na nadawcy oznacza to, ile komunikatów okna transfer może przechowywać podczas oczekiwania na potwierdzeń; odbiornik wskazuje ile komunikatów do buforowania dla usługi.

Wybieranie właściwego rozmiaru wpływa na wydajność sieci i optymalną wydajność usług. W poniższych sekcjach opisano, co należy wziąć pod uwagę podczas wybierania wartości dla tej właściwości i ich wpływ na wartość.

Domyślny rozmiar okna transfer jest osiem wiadomości.

### <a name="efficient-use-of-the-network"></a>Efektywne wykorzystanie sieci

W tym kontekście termin *sieci* odpowiada wszystko, co jest używane jako podstawa komunikacji między klientem (nadawcy) i usługi (odbiorca). Dotyczy to również połączenia transportu i pośredników lub mostków w między tym routery SOAP i HTTP proxy/zapory.

Efektywne wykorzystanie sieci zapewnia pełni służy pojemność sieci. Ilość danych, który można przenosić za pośrednictwem sieci na sekundę (*szybkość danych*) i czas potrzebny na transfer danych od nadawcy, odbiorcy (*opóźnienia*) wpływ jak skutecznie sieci jest wykorzystywany.

Na nadawcy, właściwość <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> wskazuje, ile komunikatów okna transfer może przechowywać podczas oczekiwania na potwierdzeń. Jeśli opóźnienie w sieci jest wysokie, a w celu zapewnienia odpowiadać nadawcy i wykorzystania sieci skuteczne, należy zwiększyć rozmiar okna transmisji.

Na przykład nawet wtedy, gdy nadawca zachowuje o szybkości danych, czas oczekiwania może być wysoka Jeśli istnieje kilka pośredników między nadawcą i odbiorcą lub dane przechodzą przez pośrednika stratna lub sieci. W związku z tym nadawca ma oczekiwania potwierdzeń komunikatów w jego oknie transmisji zanim zaczną akceptować nowych komunikatów do wysłania w sieci. Mniejszy rozmiar buforu duże opóźnienie, mniej skuteczne użycie sieci. Z drugiej strony zbyt duży rozmiar okna transmisji może mieć wpływ usługi, ponieważ usługa może być konieczne nadążyć wysokiej szybkości danych wysłanych przez klienta.

### <a name="running-the-service-to-capacity"></a>Uruchomiona usługa pojemności

Jak sieci są wydajnie używane, najlepiej również ma usługę by było uruchamiane z optymalną wydajność. Właściwość rozmiar okna transfer odbiornika wskazuje ile komunikatów można buforować odbiornika. Ten komunikat buforowanie umożliwia nie tylko sterowanie przepływem sieci, ale umożliwia również usługę, aby uruchomić pełną pojemność. Na przykład, jeśli bufor jest jeden komunikat i szybciej, niż może je przetwarzać usługi nadchodzą komunikaty następnie sieci może porzucić wiadomości i pojemności może niewykorzystana lub niedostatecznego wykorzystania.

Przy użyciu buforu zwiększa dostępność usługi jednocześnie odbiera i buforuje komunikat podczas przetwarzania wcześniej odebranej wiadomości.

Zaleca się używać tego samego `MaxTransferWindowSize` na nadawcy i odbiorcy.

### <a name="enabling-flow-control"></a>Włączanie przepływu sterowania

*Sterowanie przepływem* mechanizm, który zapewnia nadawcę i odbiorcę bieżąco ze sobą, oznacza to, że komunikaty są używane i reagować tak szybko, jak są one tworzone. Rozmiar okna transmisji na klienta i usługi zapewnia, że nadawca i odbiorca są uzasadnione okna synchronizacji.

Zaleca się ustawienie właściwości <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> do `true` Jeśli używasz niezawodnej sesji między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.

## <a name="setting-maxpendingchannels"></a>Ustawienie MaxPendingChannels

Podczas zapisywania to usługa umożliwiająca komunikacji niezawodnej sesji od różnych klientów, istnieje możliwość dużej liczby klientów utworzyć niezawodnej sesji z usługą w tym samym czasie. Odpowiedź usługi w takich sytuacjach jest zależna od `MaxPendingChannels` właściwości.

Gdy nadawca tworzy kanał niezawodnej sesji do odbiornika, uzgadniania między nimi ustanawia niezawodnej sesji. Po ustanowieniu sesji niezawodnej kanał jest umieszczany w kolejce kanałów oczekujących na akceptację przez usługę. `MaxPendingChannels` Właściwość wskazuje, ile kanałów może znajdować się w tym stanie.

Istnieje możliwość usługa jest w stanie, w których nie można zaakceptować więcej kanałów. Jeśli kolejka jest pełna, próby ustanowienia niezawodnej sesji zostało odrzucone, a klient musi próbę.

Istnieje również możliwość, że kanałów oczekujących w kolejce pozostają w kolejce przez dłuższy czas. Tymczasem limitu czasu bezczynności sesji niezawodnej może wystąpić, powoduje kanału do przejścia do stan.

Podczas zapisywania usługę, która obsługuje wielu klientów jednocześnie, należy ustawić wartość, która jest odpowiednia do własnych potrzeb. Ustawienie zbyt wysokiej wartości dla `MaxPendingChannels` właściwość ma wpływ na zestaw roboczy.

Wartość domyślna dla <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> jest czterech kanałów.

## <a name="reliable-sessions-and-hosting"></a>Niezawodne sesje i hostingu

Gdy sieci web obsługującym usługę korzystającą z sesji niezawodnych, następujące istotne kwestie należy mieć na uwadze:

- Niezawodnej sesji nie jest obiektem stanowym i stanie są przechowywane w obiekcie AppDomain. Oznacza to, że wszystkie komunikaty, które są częścią niezawodnej sesji muszą być przetwarzane w tej samej domenie AppDomain. Farmy serwerów sieci Web i ogrodach sieci web, których rozmiar farmy lub ogrodu jest większa niż jeden węzeł nie gwarantuje to ograniczenie.

- Niezawodnej sesji przy użyciu dwa kanały HTTP (na przykład za pomocą `WsDualHttpBinding`) mogą wymagać więcej niż domyślne dwa połączenia na — klient HTTP. Oznacza to, że niezawodnej sesji dupleksowej może wymagać połączeń do dwóch każdego sposób, ponieważ równoczesnych komunikatów aplikacji i protokół może przesyłania każdego sposób w danym momencie. W niektórych warunkach, w zależności od wymiany komunikatów usługi oznacza to, że ma możliwość zakleszczenie usługi hostowanej w sieci web przy użyciu dwóch HTTP i sesje niezawodne. Aby zwiększyć liczbę dozwolonych połączeń HTTP na klienta, dodaj następującą wartość do pliku konfiguracyjnego odpowiedniego (na przykład *web.config* z danej usługi):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  Wartość `maxconnection` atrybut jest wymagana liczba połączeń. W takim przypadku powinno być cztery połączenia.
