---
title: Najlepsze rozwiązania dotyczące sesji niezawodnych
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 1d9671e7e3124d535b66de8cd8468f76dcb32b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857990"
---
# <a name="best-practices-for-reliable-sessions"></a>Najlepsze rozwiązania dotyczące sesji niezawodnych

W tym temacie omówiono najlepsze rozwiązania dotyczące sesji niezawodnych.

## <a name="setting-maxtransferwindowsize"></a>Setting MaxTransferWindowSize

Niezawodne sesje w Windows Communication Foundation (WCF) okno transferu do przechowywania komunikatów na klienta i usługi. Można skonfigurować właściwości <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> wskazuje, ile komunikatów może zawierać okno transferu.

Na nadawcy oznacza to, ile komunikatów okien transfer może zawierać podczas oczekiwania na potwierdzeń; na odbiornik oznacza to, ile komunikatów do buforowania dla usługi.

Wybieranie wielkości wpływa na wydajność sieci i optymalne pojemność usługi. W poniższych sekcjach opisano, co należy wziąć pod uwagę podczas wybierania wartości tej właściwości i wpływu na wartość.

Domyślny rozmiar okna transferu jest osiem komunikatów.

### <a name="efficient-use-of-the-network"></a>Efektywne wykorzystanie sieci

W tym kontekście pojęcie *sieci* odpowiada wszystko, co jest używany jako podstawa komunikacji między klientem (nadawcy) a usługą (odbiorca). W tym połączenia transportu i dowolnym pośrednika lub mostków się między tym routery protokołu SOAP i HTTP serwery proxy/zapory.

Efektywne wykorzystanie sieci zapewnia, że pojemność sieci jest w pełni wykorzystywany. Ilość danych, które mogą być przesyłane za pośrednictwem sieci na sekundę (*szybkość danych*) i czas potrzebny na transfer danych od nadawcy do odbiorcy (*opóźnienie*) jak skutecznie mieć wpływ na sieć jest używana.

Na nadawcy, właściwość <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> wskazuje, ile komunikatów jej transfer okna może zawierać podczas oczekiwania na potwierdzeń. Jeśli opóźnienie sieci jest wysokie, a w celu zapewnienia odpowiadać nadawcy i wykorzystanie sieci skuteczne, należy zwiększyć rozmiar okna transferu.

Na przykład nawet wtedy, gdy nadawca nadąża za pomocą szybkość danych, czas oczekiwania może być wysokiej Jeśli kilka pośredników istnieje między nadawcą i odbiorcą lub dane musi przechodzić przez pośrednika stratnej lub w sieci. W związku z tym nadawca ma oczekiwania przed zaakceptowaniem nowych wiadomości do wysłania na potrzeby przesyłu potwierdzeń komunikatów w jego oknie transferu. Mniejszy buforu dużymi opóźnieniami, mniej skuteczny wykorzystanie sieci. Z drugiej strony zbyt duży rozmiar okna transfer może mieć wpływ na usługi, ponieważ usługa może być konieczne nadrób zaległości na wysoki stopień dane wysyłane przez klienta.

### <a name="running-the-service-to-capacity"></a>Uruchomiona usługa do pojemności

Jak sieć używana jest efektywne, najlepiej również ma usługę, aby była uruchamiana z optymalną wydajnością. Właściwości rozmiaru okna transferu odbiornika wskazuje, ile komunikatów można buforować odbiornika. Tej buforowanie komunikat pozwala nie tylko sterowanie przepływem sieci, a także umożliwia usługa do uruchamiania w celu pełnego wykorzystania możliwości. Na przykład, jeśli bufor jest jeden komunikat dociera szybciej niż usługa może przetwarzać je następnie sieci może porzucić wiadomości i pojemności może być potrzebne dodatkowe lub skutkowało niewystarczającym wykorzystaniem.

Przy użyciu bufora zwiększa dostępność usługi, jednocześnie odbiera i buforuje komunikat podczas przetwarzania wcześniej Odebrane komunikaty.

Zaleca się używać tego samego `MaxTransferWindowSize` na nadawcy i odbiorcy.

### <a name="enabling-flow-control"></a>Włączanie przepływu sterowania

*Sterowanie przepływem* to mechanizm, który zapewnia, że nadawcą i odbiorcą dotrzymuje kroku ze sobą, oznacza to, komunikaty są używane i podjęte tak szybko, jak są one generowane. Rozmiar okna transferu na klienta i usługi dzięki nadawcy i odbiorcy są uzasadnione okna o synchronizacji.

Firma Microsoft zdecydowanie zaleca się ustawienie właściwości <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> do `true` podczas pracy z niezawodnej sesji od klienta programu WCF i usługi WCF.

## <a name="setting-maxpendingchannels"></a>Ustawienie MaxPendingChannels

Podczas pisania to usługa, która umożliwia komunikację niezawodnej sesji od różnych klientów, istnieje możliwość dużej liczby klientów, utworzyć niezawodnej sesji do usługi w tym samym czasie. Odpowiedź usługi w takich sytuacjach jest zależna od `MaxPendingChannels` właściwości.

Gdy nadawca tworzy kanał niezawodnej sesji do odbiornika, uzgadniania między nimi ustanawia niezawodnej sesji. Po ustanowieniu sesji kanał jest umieszczana w kolejce kanałów oczekujących na akceptację przez usługę. `MaxPendingChannels` Właściwość wskazuje, ile kanałów mogą znajdować się w tym stanie.

Istnieje możliwość usługi będzie w stanie, w których nie można zaakceptować więcej kanałów. Jeśli kolejka jest zapełniona, próby ustanowienia niezawodnej sesji zostanie odrzucony, a klient musi próbę.

Istnieje również możliwość, że kanałów oczekujących w kolejce pozostaną w kolejce przez dłuższy czas. W międzyczasie limit czasu braku aktywności na niezawodnej sesji może wystąpić, powodując kanału, do którego nastąpi przejście w stan.

Podczas pisania Usługa obsługująca wielu klientów jednocześnie, należy ustawić wartość, która jest odpowiednia dla Twoich potrzeb. Ustawienie zbyt wysokiej wartości dla `MaxPendingChannels` właściwość ma wpływ na zestaw roboczy.

Wartością domyślną dla <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> jest czterech kanałów.

## <a name="reliable-sessions-and-hosting"></a>Niezawodne sesje i hosting

Gdy sieci web obsługujący usługę korzystającą z sesji niezawodnych, następujące ważne kwestie należy mieć na uwadze:

- Niezawodne sesje są stanowe i jest zachowywana w domenie aplikacji. Oznacza to, że wszystkie komunikaty, które są dostępne w ramach sesji niezawodnej muszą zostać przetworzone w tej samej domenie aplikacji. To ograniczenie nie może zagwarantować, farmy serwerów sieci Web i ogrodach sieci web, w których rozmiar farmy lub ogrodzie jest większa niż jeden węzeł.

- Niezawodne sesje za pomocą podwójnego kanałów HTTP (na przykład za pomocą `WsDualHttpBinding`) mogą wymagać więcej niż domyślna wartość dwóch połączeń na — klient HTTP. Oznacza to, że dupleks niezawodnej sesji może wymagać połączeń z maksymalnie dwóch danej opcji, ponieważ współbieżnych komunikatów aplikacji i protokół może przesyłania danej opcji w danym momencie. W pewnych okolicznościach, w zależności od wymiany komunikatów usługi oznacza to, że istnieje możliwość zakleszczenie usługi hostowanej w sieci web za pomocą podwójnego HTTP i sesje niezawodne. Aby zwiększyć liczbę dozwolonych połączeń HTTP na klienta, dodaj następującą zawartość do pliku konfiguracji związanych z (na przykład *web.config* usługi w danym):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  Wartość `maxconnection` atrybut jest wymagana liczba połączeń. W takim przypadku powinno być cztery połączeń.
