---
title: Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: abd81b5e7bf611fc6b4f446a82628b83130f2d54
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599207"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP
Ten temat zawiera podsumowanie różnic między systemem Windows Vista, Windows Server 2003 i Windows XP w ramach funkcji kolejek programu Windows Communication Foundation (WCF).  
  
## <a name="application-specific-dead-letter-queue"></a>Kolejka utraconych wiadomości specyficznych dla aplikacji  
 Komunikaty w kolejce mogą pozostawać w kolejce w nieskończoność, jeśli aplikacja otrzymująca nie odczytuje ich w odpowiednim czasie. Takie zachowanie nie jest zalecane, Jeśli komunikaty są zależne od czasu. Komunikaty z uwzględnieniem czasu mają `TimeToLive` ustawioną właściwość w powiązaniu umieszczonym w kolejce. Ta właściwość wskazuje, jak długo komunikaty mogą znajdować się w kolejce przed ich wygaśnięciem. Wygasłe komunikaty są wysyłane do kolejki specjalnej zwanej kolejką utraconych wiadomości. Komunikat może również kończyć się w kolejce utraconych wiadomości z innych powodów, takich jak przekroczenie limitu przydziału kolejki lub wystąpił błąd uwierzytelniania.  
  
 Zazwyczaj jedna kolejka utraconych wiadomości w całym systemie istnieje dla wszystkich aplikacji umieszczonych w kolejce, które współużytkują menedżera kolejek. Kolejka utraconych wiadomości dla każdej aplikacji umożliwia lepszą izolację aplikacji w kolejce, które współużytkują menedżera kolejek, umożliwiając tym aplikacjom określenie własnej kolejki utraconych wiadomości specyficznych dla aplikacji. Aplikacja, która współużytkuje kolejkę utraconych wiadomości z innymi aplikacjami, musi przeglądać kolejkę, aby znaleźć komunikaty, które mają do nich zastosowanie. W przypadku kolejki utraconych wiadomości specyficznych dla aplikacji można mieć pewność, że wszystkie komunikaty w kolejce wiadomości utraconych mają do nich zastosowanie.  
  
 System Windows Vista zapewnia kolejki utraconych wiadomości specyficznych dla aplikacji. Kolejki utraconych wiadomości specyficznych dla aplikacji nie są dostępne w systemach Windows Server 2003 i Windows XP, a aplikacje muszą korzystać z kolejki utraconych wiadomości w całej system.  
  
## <a name="poison-message-handling"></a>Obsługa komunikatów trujących  
 Trująca wiadomość jest komunikatem, który przekroczył maksymalną liczbę prób dostarczenia do aplikacji odbiorczej. Taka sytuacja może wystąpić, gdy aplikacja, która odczytuje komunikat z kolejki transakcyjnej, nie może przetworzyć komunikatu natychmiast z powodu błędów. Jeśli aplikacja przerywa transakcję, w której został odebrany komunikat w kolejce, zwraca komunikat do kolejki. Następnie aplikacja próbuje pobrać komunikat ponownie w nowej transakcji. Jeśli problem powodujący błąd nie zostanie poprawiony, aplikacja otrzymująca może zostać zablokowana przez pętlę, która odbiera i przerywa ten sam komunikat do momentu przekroczenia maksymalnej liczby prób dostarczenia oraz zatrucie wyniki komunikatów.  
  
 Najważniejsze różnice między usługą kolejkowania komunikatów (MSMQ) w systemach Windows Vista, Windows Server 2003 i Windows XP, które mają zastosowanie do obsługi zatrucia, obejmują następujące elementy:  
  
- Usługa MSMQ w systemie Windows Vista obsługuje podkolejki, a systemy Windows Server 2003 i Windows XP nie obsługują kolejek. Kolejki podrzędne są używane w obsłudze komunikatów trujących. Kolejki ponawiania prób i kolejka Trująca są podkolejkami do kolejki aplikacji utworzonej na podstawie ustawień obsługi komunikatów trujących. `MaxRetryCycles`Określa liczbę podkolejek ponowień do utworzenia. W związku z tym, gdy działa w systemie Windows Server 2003 lub Windows XP, `MaxRetryCycles` są ignorowane i `ReceiveErrorHandling.Move` nie jest dozwolone.  
  
- Usługa MSMQ w systemie Windows Vista obsługuje Potwierdzanie negatywne, natomiast systemy Windows Server 2003 i Windows XP nie. Negatywne potwierdzenie od Menedżera kolejki odbiorczej powoduje, że Menedżer kolejki wysyłania umieszcza odrzucony komunikat w kolejce utraconych wiadomości. W związku `ReceiveErrorHandling.Reject` z tym nie jest dozwolone w przypadku systemów Windows Server 2003 i Windows XP.  
  
- Usługa MSMQ w systemie Windows Vista obsługuje Właściwość komunikatu, która zachowuje liczbę prób dostarczenia komunikatu. Ta właściwość liczby przerwań nie jest dostępna w systemach Windows Server 2003 i Windows XP. Funkcja WCF zachowuje liczbę przerwań w pamięci, dlatego jest możliwe, że ta właściwość nie może zawierać dokładnej wartości, gdy ten sam komunikat jest odczytywany przez więcej niż jedną usługę WCF w kolektywie serwerów sieci Web.  
  
## <a name="remote-transactional-read"></a>Zdalne odczytywanie transakcyjne  
 Usługa MSMQ w systemie Windows Vista obsługuje zdalne odczyty transakcyjne. Umożliwia to aplikacji odczytującej z kolejki, która ma być hostowana na komputerze innym niż komputer, na którym znajduje się kolejka. Zapewnia to możliwość odczytywania farmy usług z kolejki centralnej, co zwiększa ogólną przepływność systemu. Gwarantuje również, że w przypadku wystąpienia błędu podczas odczytywania i przetwarzania wiadomości transakcja zostanie wycofana, a komunikat pozostaje w kolejce do późniejszego przetwarzania.  
  
## <a name="see-also"></a>Zobacz też

- [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Obsługa komunikatów zanieczyszczonych](poison-message-handling.md)
