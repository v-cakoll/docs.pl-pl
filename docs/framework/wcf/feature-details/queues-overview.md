---
title: Omówienie kolejek
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: 78d80a88153ee15f7ab152da44801c77900f874d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184599"
---
# <a name="queues-overview"></a>Omówienie kolejek

W tej sekcji przedstawiono ogólne i podstawowe pojęcia dotyczące komunikacji w kolejce. Kolejne sekcje przejść do szczegółów dotyczących sposobu kolejkowania pojęcia opisane w tym miejscu są widoczne w Programie Windows Communication Foundation (WCF).  
  
## <a name="basic-queuing-concepts"></a>Podstawowe koncepcje kolejkowania  
 Podczas projektowania aplikacji rozproszonej ważne jest wybranie odpowiedniego transportu do komunikacji między usługami a klientami. Kilka czynników wpływa na rodzaj transportu do wykorzystania. Jeden ważny czynnik — izolacja między usługą, klientem i transportem — określa użycie transportu w kolejce lub transportu bezpośredniego, takiego jak TCP lub HTTP. Ze względu na charakter transportu bezpośredniego, takich jak TCP i HTTP, komunikacja zatrzymuje się całkowicie, jeśli usługa lub klient przestanie działać lub jeśli sieć ulegnie awarii. Usługa, klient i sieć muszą być uruchomione w tym samym czasie, aby aplikacja działała. Transporty w kolejce zapewniają izolację, co oznacza, że jeśli usługa lub klient nie powiedzie się lub jeśli łącza komunikacyjne między nimi nie powiedzie się, klient i usługa mogą nadal działać.  
  
 Kolejki zapewniają niezawodną komunikację nawet w przypadku awarii w komunikujących się stronach lub w sieci. Kolejki przechwytują i dostarczają wiadomości wymieniane między komunikującymi się stronami. Kolejki są zazwyczaj wspierane przez jakiś sklep, który może być lotny lub trwały. Kolejki przechowują wiadomości od klienta w imieniu usługi, a później prześlij te wiadomości do usługi. Kolejki pośrednie zapewniają zapewnioną izolację awarii przez jedną ze stron, co czyni go preferowanym mechanizmem komunikacji dla systemów o wysokiej dostępności i odłączonych usług. Pośredni jest z kosztem dużych opóźnień. *Opóźnienie* to opóźnienie między czasem, w której klient wysyła wiadomość, a czasem, w której usługa ją odbiera. Oznacza to, że po wysłaniu wiadomości nie wiadomo, kiedy ta wiadomość może zostać przetworzona. Większość aplikacji w kolejce radzi sobie z dużym opóźnieniem. Na poniższej ilustracji przedstawiono koncepcyjny model komunikacji w kolejce.  
  
 ![Model komunikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual-Rysunek1c")  
  
 Model koncepcyjny komunikacji w kolejce  
  
 W rzeczywistości kolejka jest pojęciem rozproszonym. W związku z tym mogą one być lokalne dla każdej ze stron lub zdalne dla obu stron. Zazwyczaj kolejka jest lokalna dla usługi. W tej konfiguracji klient nie może zależeć od łączności z kolejką zdalną, która będzie stale dostępna. Podobnie kolejka musi być dostępna niezależnie od dostępności usługi odczytu z kolejki. Menedżer kolejek zarządza kolekcją kolejek. Jest odpowiedzialny za akceptowanie wiadomości wysyłanych do swoich kolejek od innych menedżerów kolejek. Jest również odpowiedzialny za zarządzanie łącznością z kolejkami zdalnymi i przesyłanie wiadomości do tych kolejek zdalnych. Aby zapewnić dostępność kolejek pomimo awarii aplikacji klienta lub usługi, menedżer kolejki jest zazwyczaj uruchamiany jako usługa zewnętrzna.  
  
 Gdy klient wysyła wiadomość do kolejki, adresuje wiadomość do kolejki docelowej, która jest kolejką zarządzaną przez menedżera kolejek usługi. Menedżer kolejek na kliencie wysyła wiadomość do kolejki transmisji (lub wychodzącej). Kolejka transmisji jest kolejką w menedżerze kolejki klienta, która przechowuje wiadomości do transmisji do kolejki docelowej. Menedżer kolejek znajduje ścieżkę do menedżera kolejek, który jest właścicielem kolejki docelowej i przenosi do niej wiadomość. Aby zapewnić niezawodną komunikację, menedżerowie kolejek implementują niezawodny protokół transferu, aby zapobiec utracie danych. Menedżer kolejek docelowych akceptuje wiadomości adresowane do kolejek docelowych, które posiada, i przechowuje wiadomości. Usługa wysyła żądania do odczytu z kolejki docelowej, w którym to czasie menedżer kolejki następnie dostarcza komunikat do aplikacji docelowej. Na poniższej ilustracji przedstawiono komunikację między czterema stronami.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Liczba rozproszonych kolejek")  
  
 Komunikacja w kolejce w typowym scenariuszu wdrażania  
  
 W związku z tym menedżer kolejki zapewnia wymaganą izolację, dzięki czemu nadawca i odbiorca mogą niezależnie zakończyć się niepowodzeniem bez wpływu na rzeczywistą komunikację. Korzyści z dodatkowych pośrednich, które zapewniają kolejki umożliwia również wiele wystąpień aplikacji do odczytu z tej samej kolejki, dzięki czemu praca rolnictwo między węzłami osiąga wyższą przepływność. W związku z tym nie jest rzadkością, aby zobaczyć kolejki używane do osiągnięcia wyższej skali i przepływności wymagania.  
  
## <a name="queues-and-transactions"></a>Kolejki i transakcje  
 Transakcje umożliwiają grupowanie zestawu operacji razem, tak aby w przypadku niepowodzenia jednej operacji wszystkie operacje zakończyć się niepowodzeniem. Przykładem użycia transakcji jest to, że dana osoba korzysta z bankomatu do przelania 1000 USD z konta oszczędnościowego na swoje konto czekowe. Wiąże się to z następującymi operacjami:  
  
- Wypłata $1,000 z konta oszczędnościowego.  
  
- Wpłacenie $1,000 na konto czekowe.  
  
 Jeśli pierwsza operacja zakończy się powodzeniem, a 1000 USD zostanie wycofane z konta oszczędnościowego, ale druga operacja zakończy się niepowodzeniem, 1000 USD zostanie utracone, ponieważ zostało już wycofane z konta oszczędnościowego. Aby zachować konta w prawidłowym stanie, jeśli jedna operacja zakończy się niepowodzeniem, obie operacje muszą zakończyć się niepowodzeniem.  
  
 W wiadomościach transakcyjnych wiadomości mogą być wysyłane do kolejki i odbierane z kolejki w ramach transakcji. W związku z tym jeśli wiadomość jest wysyłana w transakcji i transakcja jest przywracana, a następnie wynik jest tak, jakby wiadomość nigdy nie zostały wysłane do kolejki. Podobnie, jeśli wiadomość zostanie odebrana w transakcji i transakcja jest przywracana, wynik jest tak, jakby wiadomość nigdy nie została odebrana. Wiadomość pozostaje w kolejce do odczytania.  
  
 Ze względu na duże opóźnienia podczas wysyłania wiadomości nie masz możliwości poznania, jak długo trwa dotarcie do kolejki docelowej, ani nie wiesz, jak długo trwa usługa do przetworzenia wiadomości. Z tego powodu nie chcesz używać pojedynczej transakcji do wysyłania wiadomości, odbierania wiadomości, a następnie przetwarzania wiadomości. Spowoduje to utworzenie transakcji, która nie jest zatwierdzona przez nieokreślony czas. Gdy klient i usługa komunikują się za pośrednictwem kolejki przy użyciu transakcji, zaangażowane są dwie transakcje: jedna na kliencie i jedna w usłudze. Na poniższej ilustracji przedstawiono granice transakcji w typowej komunikacji w kolejce.  
  
 ![Kolejka z transakcjami](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions-Rysunek3")  
  
 Komunikacja w kolejce pokazująca oddzielne transakcje do przechwytywania i dostarczania  
  
 Transakcja klienta przetwarza i wysyła komunikat. Po zawiązaniu transakcji komunikat znajduje się w kolejce transmisji. W usłudze transakcja odczytuje komunikat z kolejki docelowej, przetwarza komunikat, a następnie zatwierdza transakcję. Jeśli wystąpi błąd podczas przetwarzania, wiadomość jest przywracana i umieszczana w kolejce docelowej.  
  
## <a name="asynchronous-communication-using-queues"></a>Komunikacja asynchronizacjowa przy użyciu kolejek  
 Kolejki zapewniają asynchroniczne środki komunikacji. Aplikacje, które wysyłają wiadomości przy użyciu kolejek nie można czekać na wiadomość, która ma zostać odebrana i przetworzona przez odbiorcę z powodu dużych opóźnień wprowadzonych przez menedżera kolejek. Wiadomości mogą pozostać w kolejce przez znacznie dłuższy czas niż aplikacja przeznaczona. Aby tego uniknąć, aplikacja może określić wartość czas do żywo w wiadomości. Ta wartość określa, jak długo wiadomość powinna pozostać w kolejce transmisji. Jeśli ta wartość czasu zostanie przekroczona, a wiadomość nadal nie została wysłana do kolejki docelowej, wiadomość może zostać przeniesiona do kolejki utraconych wiadomości.  
  
 Gdy nadawca wysyła wiadomość, powrót z operacji wysyłania oznacza, że wiadomość tylko dotarła do kolejki transmisji u nadawcy. W związku z tym jeśli występuje błąd w uzyskaniu wiadomości do kolejki docelowej, aplikacja wysyłająca nie może wiedzieć o tym natychmiast. Aby wziąć pod uwagę takie błędy, wiadomość nie powiodła się jest przenoszona do kolejki utraconych wiadomości.  
  
 Każdy błąd, taki jak komunikat, który nie może dotrzeć do kolejki docelowej lub wygasający czas wygaśnięcia, musi być przetwarzany oddzielnie. Nie jest rzadkością, w związku z tym dla aplikacji w kolejce do zapisu dwa zestawy logiki:  
  
- Normalna logika klienta i usługi wysyłania i odbierania wiadomości.  
  
- Logika kompensacji do obsługi wiadomości z nieudanej transmisji lub dostarczania.  
  
 W poniższych sekcjach omówiono te pojęcia.  
  
## <a name="dead-letter-queue-programming"></a>Programowanie kolejek utraconych  
 Kolejki utraconych wiadomości zawierają wiadomości, których nie udało się dotrzeć do kolejki docelowej z różnych powodów. Przyczyny mogą wahać się od wygasłych wiadomości do problemów z łącznością uniemożliwiających przeniesienie wiadomości do kolejki docelowej.  
  
 Zazwyczaj aplikacja może odczytywać wiadomości z kolejki utraconych wiadomości w całym systemie, określić, co poszło nie tak i podjąć odpowiednie działania, takie jak poprawianie błędów i ponowne wysyłanie wiadomości lub zanotowanie jej.  
  
## <a name="poison-message-queue-programming"></a>Programowanie kolejki trujących komunikatów  
 Po wiadomości sprawia, że do kolejki docelowej, usługa może wielokrotnie nie przetwarzać wiadomości. Na przykład aplikacja odczytująca wiadomość z kolejki w ramach transakcji i aktualizująca bazę danych może znaleźć bazę danych tymczasowo rozłączony. W takim przypadku transakcja jest przywracana, tworzona jest nowa transakcja, a wiadomość jest ponownie odczytyna z kolejki. Druga próba może zakończyć się powodzeniem lub niepowodzeniem. W niektórych przypadkach, w zależności od przyczyny błędu, komunikat może wielokrotnie zakończyć się niepowodzeniem dostarczania do aplikacji. W takim przypadku wiadomość jest uważana za "truciznę". Takie komunikaty są przenoszone do kolejki trucizny, które mogą być odczytywane przez aplikację obsługi trucizny.  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Kolejki utraconych komunikatów](../../../../docs/framework/wcf/samples/dead-letter-queues.md)
- [Komunikacja za pomocą nietrwałych kolejek](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)
- [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Obsługa kolejek komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
