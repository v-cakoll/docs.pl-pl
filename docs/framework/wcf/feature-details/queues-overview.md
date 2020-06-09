---
title: Omówienie kolejek
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: 3e75b6d5926b65a93204241eb7c71ca23a5694af
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596724"
---
# <a name="queues-overview"></a>Przegląd kolejek

W tej sekcji przedstawiono ogólne i podstawowe pojęcia związane z łącznością z kolejką. Kolejne sekcje zawierają szczegółowe informacje na temat sposobu opisywania pojęć związanych z kolejką w programie Windows Communication Foundation (WCF).  
  
## <a name="basic-queuing-concepts"></a>Podstawowe pojęcia związane z kolejką  
 Podczas projektowania aplikacji rozproszonej należy wybrać odpowiedni transport do komunikacji między usługami i klientami. Niektóre czynniki wpływają na rodzaj transportu do użycia. Jednym z ważnych czynników — izolacja między usługą, klientem i transportem — określa użycie transportu w kolejce lub transportu bezpośredniego, takiego jak TCP lub HTTP. Ze względu na charakter bezpośrednich transportów, takich jak TCP i HTTP, komunikacja zostaje zatrzymana całkowicie, jeśli usługa lub klient przestaną działać lub w przypadku awarii sieci. Aby aplikacja działała, usługa, klient i sieć muszą być uruchomione w tym samym czasie. Transporty znajdujące się w kolejce zapewniają izolację, co oznacza, że jeśli usługa lub klient zakończy się niepowodzeniem lub jeśli linki komunikacji między nimi nie powiodą się, klient i usługa mogą nadal działać.  
  
 Kolejki zapewniają niezawodną komunikację nawet z błędami w komunikacji stron lub sieci. Kolejki przechwytują i dostarczają komunikaty wymieniane między komunikującymi się stronami. Kolejki są zwykle obsługiwane w przypadku niektórych rodzajów magazynów, które mogą być nietrwałe lub trwałe. Kolejki przechowują komunikaty z klienta w imieniu usługi i później przesyłają je dalej do usługi. Kolejki pośrednie zapewniają izolację awarii przez każdą ze stron, co sprawia, że jest to preferowany mechanizm komunikacji dla systemów wysokiej dostępności i odłączonych usług. Pośredni koszt jest dostępny z dużym opóźnieniem. *Opóźnienie* to opóźnienie od momentu wysłania komunikatu przez klienta oraz momentu odebrania go przez usługę. Oznacza to, że po wysłaniu komunikatu nie wiadomo, kiedy ten komunikat może zostać przetworzony. Większość aplikacji umieszczonych w kolejce ma duże opóźnienia. Na poniższej ilustracji przedstawiono model koncepcyjny komunikacji z kolejką.  
  
 ![Model komunikacji z kolejką](media/qconceptual-figure1c.gif "QConceptual-Figure1c")  
  
 Model koncepcyjny komunikacji w kolejce  
  
 W rzeczywistości kolejka jest koncepcją rozproszoną. W związku z tym mogą one być lokalne dla obu stron lub zdalnie. Zazwyczaj kolejka jest lokalna dla usługi. W tej konfiguracji klient nie może zależeć od łączności z kolejką zdalną, aby stały się dostępne. Podobnie Kolejka musi być dostępna niezależnie od dostępności usługi z kolejki. Menedżer kolejki zarządza kolekcją kolejek. Jest on odpowiedzialny za akceptowanie komunikatów wysyłanych do kolejek z innych menedżerów kolejek. Jest on również odpowiedzialny za zarządzanie łącznością z kolejkami zdalnymi i transferowanie komunikatów do tych kolejek zdalnych. Aby zapewnić dostępność kolejek bez błędów aplikacji klienta lub usługi, Menedżer kolejek jest zwykle uruchamiany jako usługa zewnętrzna.  
  
 Gdy klient wysyła komunikat do kolejki, kieruje komunikat do kolejki docelowej, która jest kolejką zarządzaną przez Menedżera kolejki usługi. Menedżer kolejek na kliencie wysyła komunikat do kolejki transmisji (lub wychodzącej). Kolejka transmisji jest kolejką w Menedżerze kolejki klienta, która przechowuje komunikaty do przesłania do kolejki docelowej. Menedżer kolejek znajduje następnie ścieżkę do menedżera kolejek, który jest właścicielem kolejki docelowej i przesyła do niej komunikat. Aby zapewnić niezawodne komunikację, menedżerowie kolejek implementują niezawodny protokół transferu, aby zapobiec utracie danych. Menedżer kolejki docelowej akceptuje komunikaty rozkierowane do kolejek docelowych, do których należy, i przechowuje komunikaty. Usługa wysyła żądania odczytu z kolejki docelowej, podczas gdy Menedżer kolejki dostarcza komunikat do aplikacji docelowej. Na poniższej ilustracji przedstawiono komunikację między czterema stronami.  
  
 ![Diagram aplikacji znajdujących się w kolejce](media/distributed-queue-figure.jpg "Rozproszona-Queueed-Figure")  
  
 Komunikacja w kolejce w typowym scenariuszu wdrażania  
  
 W związku z tym Menedżer kolejek zapewnia wymaganą izolację, aby nadawca i odbiornik mogli się niezależnie niepowodzeniem bez wpływania na rzeczywistą komunikację. Korzyści płynące z dodatkowych pośrednich, które obsługują kolejki, umożliwiają również odczytywanie z tej samej kolejki wielu wystąpień aplikacji, dzięki czemu hodowla między węzłami osiąga wyższą przepływność. W związku z tym nie ma potrzeby wyświetlania kolejek używanych w celu osiągnięcia wyższych wymagań dotyczących skalowania i przepływności.  
  
## <a name="queues-and-transactions"></a>Kolejki i transakcje  
 Transakcje umożliwiają grupowanie zestawu operacji w taki sposób, aby w przypadku niepowodzenia jednej operacji wszystkie operacje kończyły się niepowodzeniem. Przykład zastosowania transakcji polega na tym, że osoba korzysta z technologii ATM do transferowania $1 000 z konta oszczędności do konta sprawdzania. Obejmuje to następujące operacje:  
  
- Wycofanie $1 000 z konta oszczędności.  
  
- Zdeponowanie $1 000 na koncie sprawdzania.  
  
 Jeśli pierwsza operacja zakończy się pomyślnie i $1 000 zostanie wycofana z konta oszczędności, ale druga operacja nie powiedzie się, $1 000 zostanie utracona, ponieważ została już wycofana z konta oszczędności. W celu zachowania kont w prawidłowym stanie, jeśli jedna operacja nie powiedzie się, obie operacje mogą zakończyć się niepowodzeniem.  
  
 W wiadomościach transakcyjnych komunikaty mogą być wysyłane do kolejki i odbierane z kolejki w ramach transakcji. W takim przypadku, jeśli wiadomość jest wysyłana w transakcji, a transakcja jest wycofywana, wynik jest tak, jakby komunikat nigdy nie był wysyłany do kolejki. Podobnie, jeśli wiadomość zostanie odebrana w transakcji, a transakcja zostanie wycofana, wynik będzie taki jak, jakby komunikat nigdy nie został odebrany. Komunikat pozostaje w kolejce do odczytu.  
  
 Ze względu na duże opóźnienie, podczas wysyłania komunikatu nie ma możliwości znajomości czasu osiągnięcia jego kolejki docelowej, ani wiesz, jak długo trwa przetwarzanie komunikatu przez usługę. W związku z tym nie chcesz używać pojedynczej transakcji do wysłania wiadomości, odebrać komunikat, a następnie przetworzyć komunikat. Spowoduje to utworzenie transakcji, która nie jest zatwierdzona przez nieokreślony czas. Gdy klient i usługa komunikują się za pośrednictwem kolejki przy użyciu transakcji, są wykorzystywane dwa transakcje: jeden na kliencie i jeden w usłudze. Na poniższej ilustracji przedstawiono granice transakcji w typowej komunikacji kolejkowanej.  
  
 ![Kolejka z transakcjami](media/qwithtransactions-figure3.gif "QWithTransactions-Figure3")  
  
 Komunikacja w kolejce pokazująca oddzielne transakcje do przechwycenia i dostarczenia  
  
 Transakcja klienta przetwarza i wysyła komunikat. Gdy transakcja zostanie zatwierdzona, komunikat znajduje się w kolejce transmisji. W ramach usługi transakcja odczytuje komunikat z kolejki docelowej, przetwarza komunikat, a następnie zatwierdza transakcję. Jeśli podczas przetwarzania wystąpi błąd, komunikat jest wycofywany i umieszczany w kolejce docelowej.  
  
## <a name="asynchronous-communication-using-queues"></a>Komunikacja asynchroniczna przy użyciu kolejek  
 Kolejki zapewniają asynchroniczne środki komunikacji. Aplikacje wysyłające komunikaty korzystające z kolejek nie mogą czekać na odebranie i przetworzenie komunikatu przez odbiorcę z powodu dużego opóźnienia wprowadzonego przez Menedżera kolejki. Komunikaty mogą pozostawać w kolejce przez dłuższy czas niż przewidywana aplikacja. Aby tego uniknąć, aplikacja może określić wartość Time-to-Live w komunikacie. Ta wartość określa, jak długo komunikat powinien pozostać w kolejce transmisji. Jeśli ta wartość czasu zostanie przekroczona, a komunikat nadal nie został wysłany do kolejki docelowej, komunikat można przesłać do kolejki utraconych wiadomości.  
  
 Gdy nadawca wysyła komunikat, zwracany z operacji wysyłania oznacza, że wiadomość zostanie przeprowadzona tylko do kolejki transmisji na nadawcy. W związku z tym, jeśli wystąpi błąd podczas pobierania komunikatu do kolejki docelowej, aplikacja wysyłająca nie będzie od razu wiedzieć o tym. Aby zanotować takie błędy, komunikat o błędzie zostanie przekazany do kolejki utraconych wiadomości.  
  
 Każdy błąd, taki jak komunikat, który nie dociera do kolejki docelowej lub czasu wygaśnięcia, musi być przetwarzany osobno. W związku z tym nie jest to rzadko używane w przypadku aplikacji umieszczonych w kolejce do zapisu dwóch zestawów logiki:  
  
- Normalna logika klienta i usługi służąca do wysyłania i otrzymywania wiadomości.  
  
- Logika kompensacji do obsługi komunikatów z nieudanej transmisji lub dostarczania.  
  
 W poniższych sekcjach omówiono te pojęcia.  
  
## <a name="dead-letter-queue-programming"></a>Programowanie kolejki utraconych wiadomości  
 Kolejki utraconych wiadomości zawierają komunikaty, które nie mogą dotrzeć do kolejki docelowej z różnych powodów. Przyczyny problemów z łącznością uniemożliwiają przesłanie wiadomości do kolejki docelowej.  
  
 Zazwyczaj aplikacja może odczytywać komunikaty z kolejki utraconych wiadomości w całej systemie, określić, co poszło źle, i podjąć odpowiednie działania, takie jak poprawienie błędów i ponowne wysłanie komunikatu lub zanotowanie jego uwagi.  
  
## <a name="poison-message-queue-programming"></a>Programowanie w kolejce skażonych komunikatów  
 Po przeprowadzeniu przez komunikat do kolejki docelowej usługa może wielokrotnie nie przetwarzać komunikatu. Na przykład aplikacja odczytująca komunikat z kolejki w ramach transakcji i zaktualizowania bazy danych może spowodować, że baza danych jest tymczasowo odłączona. W takim przypadku transakcja zostanie wycofana, zostanie utworzona nowa transakcja, a komunikat zostanie odczytany z kolejki. Druga próba może zakończyć się powodzeniem lub niepowodzeniem. W niektórych przypadkach, w zależności od przyczyny błędu, komunikat może wielokrotnie przedostawać się do aplikacji. W takim przypadku komunikat jest uznawany za "trujące". Takie komunikaty są przenoszone do kolejki trującej, która może być odczytana przez aplikację do obsługi skażonej.  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie kolejek w programie WCF](queuing-in-wcf.md)
- [Sesje i kolejki](../samples/sessions-and-queues.md)
- [Kolejki utraconych komunikatów](../samples/dead-letter-queues.md)
- [Komunikacja za pomocą nietrwałych kolejek](../samples/volatile-queued-communication.md)
- [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../samples/wcf-to-message-queuing.md)
- [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Obsługa kolejek komunikatów programu Windows Communication Foundation](../samples/message-queuing-to-wcf.md)
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../samples/message-security-over-message-queuing.md)
