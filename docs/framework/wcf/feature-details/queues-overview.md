---
title: Omówienie kolejek
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: c181a415c8702c3032077728139b23e86d85d1f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480407"
---
# <a name="queues-overview"></a>Omówienie kolejek
W tej sekcji przedstawiono ogólne i podstawowe pojęcia związane oczekujących komunikacji. Kolejne sekcje przejść do szczegółów dotyczących sposobu kolejkowania pojęcia opisane w tym miejscu są dyskowe widoczne w Windows Communication Foundation (WCF).  
  
## <a name="basic-queuing-concepts"></a>Podstawowe pojęcia kolejkowania wiadomości  
 Podczas projektowania aplikacji rozproszonej, wybierając odpowiednie transport dla komunikacji między usługami i klientami jest ważne. Kilka czynników wpływa na rodzaj transportu do użycia. Jednym ważnym czynnikiem — izolacji między usługą, klienta i transport — Określa użycie transportu umieszczonych w kolejce lub transportu bezpośredniego, takiego jak protokół TCP lub HTTP. Ze względu na charakter transportów bezpośrednich, takich jak TCP i HTTP, komunikacja zatrzymuje się całkowicie czy usługi lub klienta przestanie działać, czy sieć nie powiedzie się. Usługi, klient i sieć musi działać w tym samym czasie dla aplikacji do pracy. Transporty umieszczonych w kolejce zapewniają izolację, co oznacza, że w przypadku awarii usługi lub klienta lub w przypadku awarii łącza komunikacji między nimi, klienta i usługi mogą nadal działać.  
  
 Kolejki stanowią niezawodny, nawet w przypadku błędów strony komunikujące się lub sieci. Kolejki przechwytywania i dostarczania wiadomości wymieniane między uczestników komunikacji. Kolejki są zazwyczaj obsługiwane przez pewnego rodzaju magazynu, który może być lotnych lub trwałe. Kolejki przechowywanie komunikatów w kliencie w imieniu usługi i później przekazuje te komunikaty do usługi. Operatory pośrednie, które kolejki zapewniają zapewnić izolację awarii przez którąkolwiek ze stron, w związku z tym co systemy o wysokiej dostępności przy użyciu mechanizmu komunikacji preferowanych i odłączone usług. Operator pośredni jest powiązana z koszt duże opóźnienie. *Opóźnienie* jest czas opóźnienia między czas, klient wysyła komunikat i usługa odbiera on. Oznacza to, że po wysłaniu komunikatu nie wiadomo, kiedy można przetworzyć ten komunikat. Najbardziej umieszczonych w kolejce aplikacji poradzić sobie z duże opóźnienie. Na poniższej ilustracji przedstawiono model koncepcyjny komunikatu w kolejce.  
  
 ![Model komunikacji umieszczonych w kolejce](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual Figure1c")  
  
 Model koncepcyjny komunikacji z obsługą kolejek  
  
 W rzeczywistości kolejka jest koncepcja rozproszonych. W efekcie mogą być lokalny dla każdej ze stron lub zdalnej w obie strony. Zazwyczaj kolejki jest lokalny z usługą. W tej konfiguracji klient nie może zależeć od łączności Kolejka zdalna ma być stale dostępny. Podobnie kolejki musi być dostępny, niezależnie od dostępności usługi czytania z kolejki. Menedżer kolejki zarządza kolekcji kolejek. Jest on odpowiedzialny za akceptowanie komunikatów wysłanych do swojej kolejki z innych menedżerów kolejki. Jest również odpowiedzialny za zarządzanie połączeniem kolejek zdalnych i przesyłania komunikatów do tych kolejkach zdalnego. Aby zapewnić dostępność kolejek, niezależnie od awarii aplikacji klienckich lub usługi, Menedżer kolejki jest zazwyczaj uruchamiany jako usługi zewnętrznej.  
  
 Gdy klient wysyła komunikat do kolejki, adresy wiadomości do kolejki docelowej jest kolejką zarządzane przez usługę Menedżer kolejki. Menedżer kolejki na kliencie wysyła wiadomość do transmisji (lub wychodzące) kolejki. Kolejki transmisji jest kolejką na menedżera kolejek klient, który przechowuje komunikaty w celu przesłania go do kolejki docelowej. Menedżer kolejki następnie znalezienie ścieżki menedżera kolejki, który jest właścicielem kolejka docelowa i przesyła do niej komunikatu. W celu zapewnienia komunikacji niezawodnej menedżerami kolejki zaimplementować protokół transferu niezawodne, aby zapobiec utracie danych. Menedżer kolejki docelowej akceptuje komunikaty adresowane do kolejki docelowej jest właścicielem i zapisuje komunikaty. Usługa wykonuje żądania odczytu z kolejki docelowej, które Menedżer kolejki po następnie dostarcza wiadomość do aplikacji docelowej. Poniższa ilustracja przedstawia komunikacji między cztery strony.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejka rysunek")  
  
 Komunikacji z obsługą kolejek w scenariuszu typowe wdrożenie  
  
 W związku z tym Menedżer kolejki udostępnia wymaganą izolację, tak aby nadawca i odbiorca może niezależnie zakończyć się niepowodzeniem bez wywierania wpływu na rzeczywistych komunikacji. Korzyści dodatkowe pośredniego, zapewniające kolejek umożliwia także wielu wystąpień aplikacji do odczytywania z tej samej kolejki tak, aby hodowli pracy między węzłami osiąga większej przepływności. W związku z tym nie jest niczym niezwykłym, aby wyświetlić używane w celu uzyskania większej skali i wymagań w zakresie przepływności kolejek.  
  
## <a name="queues-and-transactions"></a>Kolejki i transakcji  
 Transakcje umożliwiają grupowanie zestawu operacji, więc, że jeśli jedna operacja zakończy się niepowodzeniem, wszystkie operacje zakończyć się niepowodzeniem. Przykładowy sposób, aby móc używać transakcji jest, gdy osoba używa ATM do transferowania 1000 USD z jego rachunek oszczędnościowy jego konta. Pociąga za sobą następujące operacje:  
  
-   Wycofanie 1000 USD z konta oszczędności.  
  
-   Złożenie 1000 USD przeznaczony do konta rozliczeniowego.  
  
 Jeśli pierwsza operacja zakończy się pomyślnie i 1000 USD są wybierane z konta oszczędności, ale druga operacja zakończy się niepowodzeniem, 1000 USD jest utracone, ponieważ została już wycofana z konta oszczędności. Aby zachować konta w nieprawidłowym stanie, jeśli jedna operacja zakończy się niepowodzeniem, zarówno operacji musi zakończyć się niepowodzeniem.  
  
 W wiadomości transakcyjne wiadomości można wysłanych do kolejki i odbierane z kolejki w ramach transakcji. W związku z tym jeśli wiadomość jest wysyłana w transakcji, transakcja zostanie wycofana następnie wynik jest tak, jakby nigdy wiadomość została wysłana do kolejki. Podobnie jeśli wiadomość zostaje odebrana w transakcji, transakcja zostanie wycofana następnie wynik jest tak, jakby komunikatu nie było nigdy nie zostały odebrane. Komunikat pozostaje w kolejce do odczytu.  
  
 Ze względu na duże opóźnienie podczas wysyłania wiadomości, że nie ma możliwości określenia, jak długo trwa dotrzeć do swojej kolejki docelowej, podobnie jak wiesz, jak długo trwa do przetwarzania wiadomości usługi. W związku z tym czy chcesz użyć jednej transakcji do wysłania wiadomości, pojawia się komunikat o, a następnie przetworzyć komunikatu. Spowoduje to utworzenie transakcji, która nie jest zatwierdzona przez nieokreślony czas. Gdy klient i usługa komunikują się za pośrednictwem kolejki za pomocą transakcji, dwie transakcje są zaangażowane: jeden na kliencie i jeden w usłudze. Poniższa ilustracja przedstawia granice transakcji w typowej komunikacji z obsługą kolejek.  
  
 ![Kolejka o transakcji](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions Figure3")  
  
 Wyświetlanie oddzielnych transakcji do przechwytywania i dostarczania komunikacji z obsługą kolejek  
  
 Transakcja klienta przetwarza i wysyła komunikat. Gdy transakcja zostanie zatwierdzone, komunikat jest w kolejce transmisji. W usłudze transakcji odczytuje komunikat z kolejki docelowej, przetwarza komunikat i następnie zatwierdzeń transakcji. Jeśli wystąpi błąd podczas przetwarzania, komunikat jest wycofana i umieszczane w kolejce docelowej.  
  
## <a name="asynchronous-communication-using-queues"></a>Komunikacji asynchronicznej za pomocą kolejek  
 Kolejki zapewniają asynchronicznych metod komunikacji. Aplikacje, które wysyłania komunikatów przy użyciu kolejki nie może czekać na komunikat jest odbierany i przetwarzany przez odbiornik. ze względu na duże opóźnienia wynikające z menedżera kolejek. Komunikaty mogą pozostać w kolejce znacznie dłużej niż aplikacja przeznaczone. Aby tego uniknąć, aplikacja może określić wartość czasu wygaśnięcia wiadomości. Ta wartość określa, jak długo komunikat może pozostawać w kolejce transmisji. Jeśli ta wartość czasu zostanie przekroczony, a komunikat wciąż nie została wysłana do kolejki docelowej, można przenieść komunikatu do kolejki utraconych wiadomości.  
  
 Gdy nadawca wysyła komunikat, powrocie z operacji wysyłania oznacza, że wiadomość tylko dotarło do kolejki transmisji na nadawcy. Jako takie Jeśli występuje błąd podczas pobierania komunikatu do kolejki docelowej, aplikacji wysyłającej nie ma informacji o nim natychmiast. Zapoznanie się z tych błędów, nie powiodło się komunikat jest przekazywana do kolejki utraconych wiadomości.  
  
 Jakikolwiek błąd, takich jak wiadomości, których nie można osiągnąć kolejka docelowa lub Time-To-Live wygaśnie, muszą być przetwarzane osobno. Nie jest niczym niezwykłym, dlatego aplikacje umieszczonych w kolejce do zapisania dwa zestawy logiki:  
  
-   Normalne klient i usługa logiki wysyłania i odbierania wiadomości.  
  
-   Logiki wyrównującej może obsługiwać komunikaty z transmisji nieudane lub dostarczania.  
  
 W poniższych sekcjach omówiono te pojęcia.  
  
## <a name="dead-letter-queue-programming"></a>Programowanie kolejki utraconych wiadomości  
 Kolejki utraconych wiadomości zawiera wiadomości, które nie zostały dostarczone do kolejki docelowej z różnych powodów. Powody do zakresu od wygasłe wiadomości do problemów z łącznością, wykluczając transferu wiadomości do kolejki docelowej.  
  
 Zazwyczaj aplikacja może odczytywać komunikaty z kolejki utraconych wiadomości całego systemu i określić, co poszło źle i podjąć odpowiednie działania, takie jak naprawa błędów i ponowne wysyłanie wiadomości lub biorąc pod uwagę jej.  
  
## <a name="poison-message-queue-programming"></a>Obsługa zanieczyszczonych komunikatów kolejki programowania  
 Po powoduje komunikat do kolejki docelowej, usługa wielokrotnie może zakończyć się niepowodzeniem przetworzyć komunikatu. Na przykład aplikacja czytania wiadomości z kolejki w ramach transakcji i aktualizowanie bazy danych może się okazać bazy danych, tymczasowo odłączone. W tym przypadku transakcja zostanie wycofana, utworzono nową transakcję i komunikat jest ponownie Pobierz z kolejki. Druga próba może powodzenie lub niepowodzenie. W niektórych przypadkach w zależności od przyczyny tego błędu komunikat wielokrotnie mogą nie działać dostarczania aplikacji. W takich przypadkach komunikat jest uznawany za jako "poison." Takie wiadomości są przenoszone do kolejki skażone, który może zostać odczytany przez aplikację do obsługi poison.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Kolejki utraconych komunikatów](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 [Komunikacja za pomocą nietrwałych kolejek](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Przykłady powiązania Integracja usługi kolejkowania komunikatów](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Obsługa kolejek komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
