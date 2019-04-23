---
title: Podstawowe informacje dotyczące transakcji
ms.date: 03/30/2017
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
ms.openlocfilehash: 49e44ce1112a44c105f47560017331afe4454a0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076761"
---
# <a name="transaction-fundamentals"></a>Podstawowe informacje dotyczące transakcji
Transakcje powiązać wielu zadań jednocześnie. Na przykład załóżmy, że aplikacja wykonuje dwa zadania. Najpierw tworzy nową tabelę w bazie danych. Następnie wywołuje obiekt specjalne do zbierania, formatowania i wstawianie danych w nowej tabeli. Te dwa zadania są powiązane i wzajemnie nawet wtedy, w taki sposób, że ma zostać Unikaj tworzenia nowej tabeli, o ile nie można wypełniać danych. Wykonywanie zadania, zarówno w zakresie pojedynczą transakcję wymusza połączenie między nimi. Jeśli drugie zadanie nie powiedzie się, pierwsze zadanie jest przywrócenie punkt przed utworzeniem nowej tabeli.  
  
 Aby zapewnić zachowanie przewidywalne, wszystkie transakcje musi mieć podstawowe właściwości ACID (częściowych, spójne, izolowane i trwałe). Te właściwości wymuszać stosowanie rolę transakcji krytycznym wykonywanie oferty. Aby uzyskać więcej informacji na kwasu, zobacz [właściwości ACID](https://go.microsoft.com/fwlink/?LinkId=98791). Podsumowanie kwas gwarantuje zadania powodzenie lub niepowodzenie jako jednostki związane z zestawu. W transakcji albo przetwarzania terminologii transakcji zatwierdza lub przerywa. Można zatwierdzić transakcji wszyscy uczestnicy należy zagwarantować, wszelkie zmiany w danych będą trwałe. Zmiany muszą zostać zachowane niezależnie awarie systemu lub inne nieprzewidziane zdarzenia. Jeśli pojedynczego uczestnika nie powiedzie się gwarancji, cała transakcja nie powiedzie się. Wszystkie zmiany danych w zakresie transakcji zostaną przywrócone do określonego punktu zestawu.  
  
 Transakcja może zostać ograniczona do zasobu pojedynczej danych, takich jak kolejki bazy danych lub wiadomość. W tym scenariuszu transakcji lokalnej jest zarządzany przez Menedżera transakcji udostępnione przez <xref:System.Transactions> , który generuje wydajność. Kontrolowane przez zasób danych, transakcje te są wydajne i łatwy w zarządzaniu.  
  
 Transakcje mogą obejmować wiele zasobów danych. Transakcje rozproszone zapewnić możliwość zawierać kilka różnych operacji występujących na różnych systemów w jednym przebiegu lub niepowodzenie akcji. W tym scenariuszu transakcji są koordynowany przez transakcję Koordynator MSDTC (Microsoft Distributed), który znajduje się w każdym systemie.  
  
 Podczas opracowywania transakcyjnych aplikacji przy użyciu klas dostarczonych przez <xref:System.Transactions>, nie trzeba już martwić się o jakiego rodzaju transakcji należy lub stanowiącymi Menedżera transakcji. <xref:System.Transactions> Infrastruktury automatycznie zarządza to dla Ciebie.  
  
 Po utworzeniu transakcji można określić poziom izolacji, który ma zastosowanie do transakcji. Poziom izolacji, zdefiniowane przez <xref:System.Transactions.IsolationLevel> wyliczenia, określa poziom dostępu do innych transakcji będzie mieć danych wpływ transakcji.  
  
 Można utworzyć transakcji za pomocą programu ADO.NET, <xref:System.EnterpriseServices>, lub model programowania transakcyjnych udostępnione przez <xref:System.Transactions> przestrzeni nazw. [Funkcje oferowane przez bibliotekę System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) temacie opisano funkcje, których można użyć do zapisania transakcyjnych aplikacji za pomocą <xref:System.Transactions> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje oferowane przez bibliotekę System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)
