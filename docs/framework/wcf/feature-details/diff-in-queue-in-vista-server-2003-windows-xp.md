---
title: Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: d956a72c9413384176c10effefc0307b09744c4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492027"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP
Ten temat zawiera podsumowanie różnic w funkcji kolejek usługi Windows Communication Foundation (WCF) między [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
## <a name="application-specific-dead-letter-queue"></a>Kolejki utraconych wiadomości specyficzne dla aplikacji  
 Wiadomości w kolejce może pozostawać w kolejce przez czas nieokreślony, jeśli aplikacja odbierająca nie je czytać w odpowiednim czasie. To zachowanie nie jest zalecane, jeśli komunikaty są zależne od czasu. Wiadomości o określonym terminie ważności `TimeToLive` ustawiona w kolejce powiązania. Ta właściwość wskazuje, jak długo komunikaty może być w kolejce, zanim wygasną. Wygasłe komunikaty są wysyłane do specjalnego kolejki o nazwie Kolejka utraconych wiadomości. Wiadomość można także zakończyć w kolejce wiadomości utraconych z innych powodów, takich jak przekracza przydział kolejki lub wystąpił błąd uwierzytelniania.  
  
 Zazwyczaj pojedynczej kolejki utraconych wiadomości systemowe istnieje dla wszystkich aplikacji w kolejce, które współużytkują menedżera kolejek. Kolejki utraconych wiadomości dla każdej aplikacji umożliwia lepsze izolacja pomiędzy aplikacjami umieszczonych w kolejce, które współużytkują menedżera kolejek, zezwalając tych aplikacji określić własne kolejki utraconych wiadomości specyficzne dla aplikacji. Aplikacja, która udostępnia kolejki utraconych wiadomości z innymi aplikacjami ma Przeglądaj kolejki można znaleźć wiadomości, które mają zastosowanie do niej. Z kolejki utraconych wiadomości specyficzne dla aplikacji aplikacji mogą mieć pewność, że wszystkie wiadomości z kolejki utraconych wiadomości mają zastosowanie do niej.  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] zapewnia kolejki utraconych wiadomości specyficzne dla aplikacji. Specyficzne dla aplikacji kolejki utraconych wiadomości nie są dostępne w [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)], a kolejki utraconych wiadomości systemowe muszą korzystać z aplikacji.  
  
## <a name="poison-message-handling"></a>Poison komunikat — Obsługa  
 Trująca wiadomość jest komunikat, który przekracza maksymalną liczbę prób dostarczenia do aplikacji odbierającej. Taka sytuacja może wystąpić, gdy aplikacja, która odczytuje komunikat z kolejką transakcyjną nie może przetworzyć komunikatu natychmiast z powodu błędów. Jeśli aplikacja jest przerywana transakcji, w którym została odebrana wiadomość w kolejce, zwraca komunikat do kolejki. Następnie aplikacja spróbuje pobrać wiadomość ponownie w nowej transakcji. Jeśli ten problem, który powoduje błąd nie zostanie rozwiązany, aplikacja odbierająca może zostać zablokowane w pętli, otrzymywanie i przerywanie tę samą wiadomość do momentu jego rozmiar przekracza maksymalną liczbę prób dostarczenia i powoduje Trująca wiadomość.  
  
 Podstawowe różnice między usługi kolejkowania komunikatów (MSMQ) na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] istotnych do obsługi skażone są następujące:  
  
-   Usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje podkolejki, podczas gdy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie obsługują podkolejki. Kolejki podrzędne są używane w obsłudze poison komunikatów. Kolejki ponownych prób i skażone kolejki są podkolejki do kolejki aplikacji, która jest tworzona na podstawie ustawień poison komunikat — Obsługa. `MaxRetryCycles` Określa, ile ponów podkolejki do utworzenia. W związku z tym podczas uruchamiania [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` są ignorowane i `ReceiveErrorHandling.Move` jest niedozwolone.  
  
-   Usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje negatywną potwierdzenie, podczas gdy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie. Potwierdzenie negatywne z odbierającego menedżera kolejek powoduje wysyłanie menedżera kolejek można umieścić odrzucone wiadomości w kolejce wiadomości utraconych. W efekcie `ReceiveErrorHandling.Reject` jest niedozwolone w przypadku [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje nastąpiła właściwości wiadomości, które zlicza liczbę dostarczanie komunikatów. Ta właściwość count przerwania nie jest dostępny na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. WCF przechowuje liczby przerwania w pamięci, więc jest to możliwe, że ta właściwość nie może zawierać dokładne wartości, gdy ten sam komunikat jest odczytywany przez więcej niż jedna usługa WCF w kolektywie serwerów sieci Web.  
  
## <a name="remote-transactional-read"></a>Odczyt transakcyjne zdalny  
 Usługa MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje zdalne odczyty transakcyjnych. Dzięki temu aplikacja, która jest czytania z kolejki na komputerze, który jest inny niż komputer, na którym jest hostowany kolejki. Zapewnia to możliwość farmy usług czytania z kolejki centralnej, co zwiększa ogólną przepustowość sieci. Gwarantuje również, że jeśli wystąpi błąd podczas odczytywania i przetwarza wiadomość, transakcja wycofuje i pozostaje wiadomości w kolejce do późniejszego przetwarzania.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
