---
title: "Omówienie kolejek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eb5d0f51fbbb6c8bad9bfbbfd9977368fdbd0666
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="queues-overview"></a>Omówienie kolejek
W tej sekcji przedstawiono ogólne i podstawowe pojęcia oczekujących komunikacji. Kolejne sekcje przejdź do szczegółów dotyczących sposobu kolejkowania pojęcia opisane w tym miejscu są manifestowany w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="basic-queuing-concepts"></a>Podstawowe pojęcia kolejkowania  
 Podczas projektowania aplikacji rozproszonej, wybór ważne jest prawo transportu do komunikacji między usług i klientów. Istnieje kilka możliwych wpływa na rodzaj transportu do użycia. Jeden ważnym czynnikiem — izolację między usługa, klient i transportu — Określa użycie transport z kolejką lub transportu bezpośredniego, takiego jak protokół TCP lub HTTP. Ze względu na specyfikę transportów bezpośrednie, takie jak protokół TCP i HTTP komunikacji zatrzymuje całkowicie czy usługi lub klienta przestaną działać, czy sieć nie powiedzie się. W tym samym czasie dla aplikacji do pracy musi działać usługa, klient i sieci. Transporty w kolejce zapewniają izolację, co oznacza, że usługi lub klienta się nie powieść lub łączy komunikacji między nimi zakończyć się niepowodzeniem, klient i usługa mogą nadal działać.  
  
 Kolejki zapewniają niezawodne komunikację nawet z błędami w komunikującymi się Stronami lub sieci. Kolejki przechwytywania i dostarczania wiadomości wymieniane między komunikującymi się Stronami. Kolejki są zwykle wspierany przez określonego rodzaju magazynu, który może być nietrwałe lub trwałe. Kolejki przechowywania komunikatów z klienta w imieniu usługi i później przesyła te komunikaty do usługi. Operatory pośrednie, zapewniają kolejek zapewnia izolację awarii przez strony, co w związku z tym mechanizm komunikacji preferowanych systemy o wysokiej dostępności i odłączony usług. Pośredni zawiera koszt duże opóźnienie. *Czas oczekiwania* jest czas opóźnienia między czas, klient wysyła komunikat i usługa odbiera on. Oznacza to, że po wysłaniu komunikatu nie wiadomo, kiedy wiadomości mogą być przetwarzane. Najbardziej umieszczonych w kolejce aplikacji radzenia sobie duże opóźnienie. Na poniższej ilustracji przedstawiono model koncepcyjny komunikatu w kolejce.  
  
 ![Model komunikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual Figure1c")  
  
 Komunikacja z obsługą kolejek model koncepcyjny  
  
 W rzeczywistości kolejki to pojęcie rozproszonych. Tak można je lokalnego drugiej strony lub zdalnego obu stron. Kolejka jest zazwyczaj lokalnych z usługą. W tej konfiguracji klient nie może zależeć od łączności zdalnej kolejki być stale dostępne. Podobnie kolejki musi być dostępna niezależnie od dostępności usługi czytania z kolejki. Menedżer kolejek zarządza kolekcji kolejek. Jest odpowiedzialny za akceptowanie komunikatów wysłanych do jego kolejki z innymi menedżerami kolejki. Również jest odpowiedzialny za zarządzanie łączność z kolejek zdalnych i przesyłania komunikatów do tych kolejek zdalnych. Aby zapewnić dostępność kolejek niezależnie od awarii aplikacji klienta lub usługę, menedżera kolejek jest są zazwyczaj uruchamiane jako zewnętrznej usługi.  
  
 Gdy klient wysyła wiadomość do kolejki, rozwiązuje wiadomości do kolejki docelowej, który jest zarządzany przez menedżera kolejek usługi kolejki. Menedżer kolejek na kliencie wysyła wiadomość do transmisji (lub wychodzących) kolejki. Kolejka transmisji jest kolejką na menedżera kolejek klienta, który przechowuje komunikaty w celu przesłania go do kolejki docelowej. Następnie menedżera kolejek znalezienie ścieżkę do menedżera kolejek, który jest właścicielem kolejki docelowej i przesyła komunikat, aby go. W celu zapewnienia komunikacji niezawodnej menedżerami kolejki implementacji protokołu transferu niezawodne, aby zapobiec utracie danych. Menedżer kolejki docelowej akceptuje komunikaty adresowane do kolejki docelowej, jest właścicielem i przechowuje komunikaty. Usługa wykonuje żądaniami odczytu z kolejki docelowej, w tym czasie menedżera kolejek następnie dostarcza wiadomość aplikacji docelowej. Na poniższej ilustracji przedstawiono komunikację między cztery strony.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejki — rysunek")  
  
 Komunikacja z obsługą kolejek w przypadku typowego wdrożenia  
  
 W związku z tym Menedżer kolejek zapewnia to wymaganą izolację, aby nadawca i odbiorca może niezależnie zakończyć się niepowodzeniem bez wpływu na rzeczywiste komunikacji. Zaletą pośredni dodatkowe, które zapewniają kolejek również umożliwia wiele wystąpień aplikacji do odczytu z tej samej kolejki, dzięki czemu hodowli pracy między węzłami osiągnięcie wyższej przepustowości. W związku z tym nie jest rzadko Zobacz kolejki używane do uzyskania wymagania dotyczące przepływności i zwiększenia skali.  
  
## <a name="queues-and-transactions"></a>Kolejki i transakcji  
 Transakcje umożliwiają pogrupować zestaw operacji, dzięki czemu w przypadku niepowodzenia operacji jednej operacji nie powiedzie się. Przykład sposobu użycia transakcji jest, gdy osoba używa ATM do transferu wynosi 1000 z jego konta oszczędności jego konta. Pociąga to za sobą następujące operacje:  
  
-   Wycofanie 1000 USD z konta oszczędności.  
  
-   Złożenie 1000 USD przeznaczony na konta bankowego.  
  
 Jeśli pierwsza operacja zakończy się powodzeniem i 1000 USD zostanie wycofany z konta oszczędności, ale druga operacja nie powiedzie się, wynosi 1000 jest utracone, ponieważ już zostało wycofane z konta oszczędności. Aby zachować konta w nieprawidłowym stanie, jeśli jedna operacja zakończy się niepowodzeniem, operacjami musi zakończyć się niepowodzeniem.  
  
 W wiadomości transakcyjnych wysłanych do kolejki można wiadomości i odbierane z kolejki w ramach transakcji. W związku z tym w transakcji jest wysyłany komunikat transakcja zostanie wycofana, następnie wynik jest tak, jakby nigdy wiadomości została wysłana do kolejki. Podobnie jeśli wiadomość zostanie odebrana w transakcji, a transakcja zostanie wycofana, następnie wynik jest tak, jakby wiadomości nie była nigdy nie zostały odebrane. Komunikat pozostaje w kolejce do odczytu.  
  
 Ze względu na duże opóźnienie podczas wysyłania wiadomości, że nie ma możliwości otrzymuje żadnej informacji o czas potrzebny do osiągnięcia swojej kolejki docelowej, podobnie jak wiadomo, jak długo trwa do przetworzenia komunikatów usługi. W związku z tym czy chcesz użyć pojedynczej transakcji do wysłania wiadomości, komunikat, a następnie przetworzyć komunikatu. Spowoduje to utworzenie transakcji, która nie została przekazana przez nieokreślony czas. Gdy klient i usługa komunikują się za pośrednictwem kolejki przy użyciu transakcji, są związane z dwóch transakcji: na kliencie i jeden w usłudze. Na poniższej ilustracji przedstawiono granice transakcji w typowym umieszczonych w kolejce.  
  
 ![Kolejka transakcji](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions Figure3")  
  
 Komunikacja z obsługą kolejek przedstawiający oddzielnych transakcji do przechwytywania i dostarczenia  
  
 Transakcja klienta przetwarza i wysyła wiadomość. Gdy transakcja zostanie zatwierdzone, wiadomość jest w kolejce transmisji. W usłudze transakcji odczytuje komunikat z kolejki docelowej, przetwarza komunikat i następnie zatwierdza transakcji. Jeśli wystąpi błąd podczas przetwarzania, wiadomość jest wycofana i umieszczane w kolejce docelowej.  
  
## <a name="asynchronous-communication-using-queues"></a>Asynchroniczną komunikację za pomocą kolejek  
 Kolejki zapewniają asynchronicznych metod komunikacji. Aplikacje, które wysyłanie wiadomości przy użyciu kolejki nie może czekać na komunikat jest odbierany i przetwarzany przez odbiornik. ze względu na duże opóźnienie wprowadzane przez menedżera kolejek. Komunikaty mogą pozostać w kolejce znacznie dłużej niż aplikację zamierzone. Aby tego uniknąć, aplikacji można określić wartość czasu wygaśnięcia wiadomości. Ta wartość określa, jak długo komunikatu może pozostawać w kolejce transmisji. Jeśli ta wartość czasu zostanie przekroczony, a komunikat nadal nie została wysłana do kolejki docelowej, można przenosić wiadomości do kolejki utraconych wiadomości.  
  
 Gdy nadawca wysyła komunikat, powrocie z operacji wysyłania oznacza, że komunikat tylko zapisane w kolejce transmisji na nadawcy. Tak Jeśli występuje błąd uzyskiwania wiadomości do kolejki docelowej, aplikacja wysyłająca nie wiesz natychmiast. Aby wziąć pod uwagę takie błędy, wiadomości nie powiodło się jest przekazywane do kolejki utraconych wiadomości.  
  
 Błędu, takie jak wiadomości, można osiągnąć kolejka docelowa lub Time-To-Live wygasa, muszą być przetwarzane osobno. Nie jest rzadko, w związku z tym dla aplikacji w kolejce do zapisania dwa zestawy logiki:  
  
-   Normalne klient i usługa logiki wysyłania i odbierania wiadomości.  
  
-   Logika kompensacji do obsługi przekazywania nie powiodło się i dostarczania wiadomości.  
  
 W poniższych sekcjach omówiono te pojęcia.  
  
## <a name="dead-letter-queue-programming"></a>Programowanie kolejki utraconych wiadomości  
 Kolejki utraconych wiadomości zawiera komunikaty, które nie może połączyć się z różnych powodów kolejki docelowej. Przyczyny mogą należeć do zakresu od wygasłych komunikatów do problemów z łącznością uniemożliwiające transfer wiadomości do kolejki docelowej.  
  
 Zwykle aplikacja może odczytywać wiadomości z kolejki utraconych wiadomości systemowe, określić, co poszło źle i podejmij odpowiednie działania, takie jak naprawa błędów i ponowne wysyłanie wiadomości lub biorąc pod uwagę go.  
  
## <a name="poison-message-queue-programming"></a>Trująca wiadomość została kolejki programowania  
 Po powoduje wiadomości do kolejki docelowej, usługa wielokrotnie może zakończyć się niepowodzeniem do przetworzenia komunikatów. Na przykład aplikacja czytania wiadomości z kolejki w ramach transakcji i aktualizowanie bazy danych może się okazać tymczasowo odłączone bazy danych. W takim przypadku transakcja zostanie wycofana, utworzono nową transakcję i wiadomość jest odczytać z kolejki. Druga próba może succeed lub fail. W niektórych przypadkach, w zależności od przyczyny tego błędu komunikat wielokrotnie może nie powieść dostarczenia do aplikacji. W takim przypadku wiadomość jest traktowany jako "poison." Takie wiadomości są przenoszone do kolejki skażone, który może zostać odczytany przez aplikację do obsługi poison.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Kolejki utraconych komunikatów](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 [Komunikacja za pomocą nietrwałych kolejek](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Przykłady powiązanie integracji usługi kolejkowania komunikatów](http://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Obsługa kolejek komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
