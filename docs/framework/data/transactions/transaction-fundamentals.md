---
title: Podstawowe informacje dotyczące transakcji
description: Przejrzyj podstawy transakcji w programie .NET. Wszystkie transakcje muszą mieć podstawowe właściwości kwasu (niepodzielne, spójne, izolowane i trwałe).
ms.date: 03/30/2017
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
ms.openlocfilehash: 49292172b07985d379bfa5d520798d7d97af5749
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141942"
---
# <a name="transaction-fundamentals"></a>Podstawowe informacje dotyczące transakcji
Transakcje wiążą wiele zadań jednocześnie. Załóżmy na przykład, że aplikacja wykonuje dwa zadania. Najpierw tworzy nową tabelę w bazie danych. Następnie wywołuje obiekt specjalne do zbierania, formatowania i wstawianie danych w nowej tabeli. Te dwa zadania są powiązane i wzajemnie nawet wtedy, w taki sposób, że ma zostać Unikaj tworzenia nowej tabeli, o ile nie można wypełniać danych. Wykonywanie zadania, zarówno w zakresie pojedynczą transakcję wymusza połączenie między nimi. Jeśli drugie zadanie nie powiedzie się, pierwsze zadanie jest przywrócenie punkt przed utworzeniem nowej tabeli.  
  
 Aby zapewnić zachowanie przewidywalne, wszystkie transakcje musi mieć podstawowe właściwości ACID (częściowych, spójne, izolowane i trwałe). Te właściwości wymuszać stosowanie rolę transakcji krytycznym wykonywanie oferty. Aby uzyskać więcej informacji o KWASie, zobacz [właściwości ACID](/windows/win32/cossdk/acid-properties). Podsumowanie kwas gwarantuje zadania powodzenie lub niepowodzenie jako jednostki związane z zestawu. W transakcji albo przetwarzania terminologii transakcji zatwierdza lub przerywa. Można zatwierdzić transakcji wszyscy uczestnicy należy zagwarantować, wszelkie zmiany w danych będą trwałe. Zmiany muszą zostać zachowane niezależnie awarie systemu lub inne nieprzewidziane zdarzenia. Jeśli pojedynczego uczestnika nie powiedzie się gwarancji, cała transakcja nie powiedzie się. Wszystkie zmiany danych w zakresie transakcji zostaną przywrócone do określonego punktu zestawu.  
  
 Transakcja może zostać ograniczona do zasobu pojedynczej danych, takich jak kolejki bazy danych lub wiadomość. W tym scenariuszu transakcji lokalnej jest zarządzany przez Menedżera transakcji udostępnione przez <xref:System.Transactions> , który generuje wydajność. Kontrolowane przez zasób danych, transakcje te są wydajne i łatwy w zarządzaniu.  
  
 Transakcje mogą również obejmować wiele zasobów danych. Transakcje rozproszone zapewnić możliwość zawierać kilka różnych operacji występujących na różnych systemów w jednym przebiegu lub niepowodzenie akcji. W tym scenariuszu transakcji są koordynowany przez transakcję Koordynator MSDTC (Microsoft Distributed), który znajduje się w każdym systemie.  
  
 Gdy opracowujesz aplikację transakcyjną przy użyciu klas dostarczonych przez <xref:System.Transactions> program, nie musisz martwić się o Rodzaj transakcji, których potrzebujesz, lub Menedżera transakcji. <xref:System.Transactions> Infrastruktury automatycznie zarządza to dla Ciebie.  
  
 Podczas tworzenia transakcji można określić poziom izolacji, który ma zastosowanie do transakcji. Poziom izolacji, zdefiniowany przez <xref:System.Transactions.IsolationLevel> Wyliczenie, określa poziom dostępu innych transakcji do danych, na które wpłynie transakcja.  
  
 Transakcje można tworzyć przy użyciu ADO.NET, <xref:System.EnterpriseServices> lub transakcyjnego modelu programowania dostarczonego przez <xref:System.Transactions> przestrzeń nazw. [Funkcje dostępne w temacie system. Transactions](features-provided-by-system-transactions.md) omawiają funkcje, których można użyć do pisania aplikacji transakcyjnej przy użyciu <xref:System.Transactions> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też

- [Funkcje oferowane przez bibliotekę System.Transactions](features-provided-by-system-transactions.md)
