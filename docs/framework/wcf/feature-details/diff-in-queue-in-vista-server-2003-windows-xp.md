---
title: Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: 694d7af8e6e869a7a21a3414be6c69cf9f5e7c8f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626995"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP
Ten temat zawiera podsumowanie różnic w funkcji kolejek usługi Windows Communication Foundation (WCF) między [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
## <a name="application-specific-dead-letter-queue"></a>Application-Specific Dead-Letter Queue  
 Wiadomości w kolejce może pozostawać w kolejce przez czas nieokreślony, jeśli aplikacja odbierająca nie je odczytać w odpowiednim czasie. To zachowanie nie jest zalecane, jeśli komunikaty są zależne od czasu. Zależne od czasu komunikaty mają `TimeToLive` właściwością w powiązaniu umieszczonych w kolejce. Ta właściwość wskazuje, jak długo komunikaty mogą znajdować się w kolejce zanim wygasną. Wygasłe komunikaty są wysyłane do specjalnych kolejki o nazwie kolejki utraconych wiadomości. Komunikat może również znajdą się w kolejki utraconych wiadomości z innych przyczyn, takich jak przekroczenia przydziału kolejki lub wystąpił błąd uwierzytelniania.  
  
 Zazwyczaj pojedynczej kolejki utraconych wiadomości systemowe nie istnieje dla wszystkich umieszczonych w kolejce aplikacji, które współużytkują Menedżer kolejki. Kolejka utraconych wiadomości dla każdej aplikacji umożliwia lepsze izolacji między aplikacjami umieszczonych w kolejce, mających Menedżer kolejki, umożliwiając tych aplikacji określić własne kolejki utraconych wiadomości specyficzne dla aplikacji. Aplikacja, która udostępnia kolejki utraconych wiadomości z innymi aplikacjami musi Przeglądaj kolejki komunikatów, które mają zastosowanie do niej znaleźć. Przy użyciu kolejki utraconych wiadomości usługi specyficzne dla aplikacji aplikacji mogą mieć pewność, że wszystkie komunikaty w swojej kolejki utraconych wiadomości stosują się do niego.  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] zapewnia kolejki utraconych wiadomości specyficzne dla aplikacji. Kolejki utraconych wiadomości specyficzne dla aplikacji nie są dostępne w [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)], a aplikacje muszą używać kolejki utraconych wiadomości całego systemu.  
  
## <a name="poison-message-handling"></a>Obsługa komunikatów poison  
 Zarządzanie skażonymi komunikatami jest komunikat, który przekroczył maksymalną liczbę prób dostarczenia do aplikacji odbierającej. Ta sytuacja może wystąpić, gdy aplikacja, która odczytuje komunikat z kolejki transakcyjne nie może przetworzyć komunikatu natychmiast z powodu błędów. Jeśli aplikacja przerywa transakcji, w którym została odebrana wiadomość w kolejce, zwraca komunikat do kolejki. Następnie aplikacja podejmie próbę pobrania wiadomość ponownie w nowej transakcji. Jeśli ten problem, który powoduje, że błąd nie zostanie rozwiązany, aplikacja odbierająca może utknąć w pętli, odbierania i przerywanie ten sam komunikat, dopóki nie przekracza maksymalną liczbę prób dostarczenia i zarządzanie skażonymi komunikatami wyników.  
  
 Podstawowe różnice między usługi kolejkowania komunikatów (MSMQ) na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] istotne dla obsługi skażone obejmują następujące elementy:  
  
- Usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje podkolejkami, podczas gdy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie obsługują podkolejek. Podkolejki są używane w obsłudze poison komunikatów. Kolejki ponownych prób i skażone kolejki są podkolejkami do kolejki aplikacji, który jest tworzony na podstawie ustawień poison postępowanie. `MaxRetryCycles` Decyduje o ile ponów podkolejkami do utworzenia. W związku z tym podczas uruchamiania na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` są ignorowane i `ReceiveErrorHandling.Move` jest niedozwolone.  
  
- Usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje ujemne potwierdzenia, podczas gdy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie obsługują. Negatywnego potwierdzenia z Menedżera kolejki odbierającej powoduje, że Menedżer kolejki wysyłania umieścić odrzuconych komunikatów w kolejce wiadomości utraconych. W efekcie `ReceiveErrorHandling.Reject` nie jest dozwolona z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Usługa MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje podejmowana jest próba właściwości wiadomości, która utrzymuje liczbę razy dostarczanie komunikatów. Ta właściwość liczba przerwania nie jest dostępny na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. WCF przechowuje licznik przerwań w pamięci, dzięki czemu jest możliwe, że ta właściwość nie może zawierać dokładną wartość, gdy ten sam komunikat jest odczytywany przez więcej niż jednej usługi WCF w ramach farmy sieci Web.  
  
## <a name="remote-transactional-read"></a>Zdalne odczytu transakcyjnego  
 Usługa MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje zdalnego transakcyjne operacje odczytu. Dzięki temu aplikacja, która odczytuje z kolejki hostowane na komputerze, który różni się od komputera, na którym jest hostowany kolejki. Zapewnia to możliwość farmy usług odczytu z kolejki centralnej, co zwiększa ogólną przepustowość systemu. Gwarantuje również, że jeśli wystąpi błąd podczas odczytywania i przetwarzania wiadomości, wycofanie transakcji i komunikat pozostaje w kolejce do późniejszego przetwarzania.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
