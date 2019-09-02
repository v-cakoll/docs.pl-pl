---
title: Podstawowe informacje dotyczące transakcji
ms.date: 03/30/2017
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
ms.openlocfilehash: 2df782a40c74c69981e7c25300acdf18f9de3cde
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205856"
---
# <a name="transaction-fundamentals"></a>Podstawowe informacje dotyczące transakcji
Transakcje wiążą wiele zadań jednocześnie. Załóżmy na przykład, że aplikacja wykonuje dwa zadania. Najpierw tworzy nową tabelę w bazie danych. Następnie wywołuje obiekt specjalne do zbierania, formatowania i wstawianie danych w nowej tabeli. Te dwa zadania są powiązane i wzajemnie nawet wtedy, w taki sposób, że ma zostać Unikaj tworzenia nowej tabeli, o ile nie można wypełniać danych. Wykonywanie zadania, zarówno w zakresie pojedynczą transakcję wymusza połączenie między nimi. Jeśli drugie zadanie nie powiedzie się, pierwsze zadanie jest przywrócenie punkt przed utworzeniem nowej tabeli.  
  
 Aby zapewnić zachowanie przewidywalne, wszystkie transakcje musi mieć podstawowe właściwości ACID (częściowych, spójne, izolowane i trwałe). Te właściwości wymuszać stosowanie rolę transakcji krytycznym wykonywanie oferty. Aby uzyskać więcej informacji o KWASie, zobacz [właściwości ACID](https://go.microsoft.com/fwlink/?LinkId=98791). Podsumowanie kwas gwarantuje zadania powodzenie lub niepowodzenie jako jednostki związane z zestawu. W transakcji albo przetwarzania terminologii transakcji zatwierdza lub przerywa. Można zatwierdzić transakcji wszyscy uczestnicy należy zagwarantować, wszelkie zmiany w danych będą trwałe. Zmiany muszą zostać zachowane niezależnie awarie systemu lub inne nieprzewidziane zdarzenia. Jeśli pojedynczego uczestnika nie powiedzie się gwarancji, cała transakcja nie powiedzie się. Wszystkie zmiany danych w zakresie transakcji zostaną przywrócone do określonego punktu zestawu.  
  
 Transakcja może zostać ograniczona do zasobu pojedynczej danych, takich jak kolejki bazy danych lub wiadomość. W tym scenariuszu transakcji lokalnej jest zarządzany przez Menedżera transakcji udostępnione przez <xref:System.Transactions> , który generuje wydajność. Kontrolowane przez zasób danych, transakcje te są wydajne i łatwy w zarządzaniu.  
  
 Transakcje mogą również obejmować wiele zasobów danych. Transakcje rozproszone zapewnić możliwość zawierać kilka różnych operacji występujących na różnych systemów w jednym przebiegu lub niepowodzenie akcji. W tym scenariuszu transakcji są koordynowany przez transakcję Koordynator MSDTC (Microsoft Distributed), który znajduje się w każdym systemie.  
  
 Gdy opracowujesz aplikację transakcyjną przy użyciu klas dostarczonych przez <xref:System.Transactions>program, nie musisz martwić się o Rodzaj transakcji, których potrzebujesz, lub Menedżera transakcji. <xref:System.Transactions> Infrastruktury automatycznie zarządza to dla Ciebie.  
  
 Podczas tworzenia transakcji można określić poziom izolacji, który ma zastosowanie do transakcji. Poziom izolacji, zdefiniowany przez <xref:System.Transactions.IsolationLevel> Wyliczenie, określa poziom dostępu innych transakcji do danych, na które wpłynie transakcja.  
  
 Transakcje można tworzyć przy użyciu ADO.NET, <xref:System.EnterpriseServices>lub transakcyjnego modelu programowania dostarczonego <xref:System.Transactions> przez przestrzeń nazw. [Funkcje dostępne w temacie system.](features-provided-by-system-transactions.md) Transactions omawiają funkcje, których można użyć do pisania aplikacji transakcyjnej przy <xref:System.Transactions> użyciu przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje oferowane przez bibliotekę System.Transactions](features-provided-by-system-transactions.md)
