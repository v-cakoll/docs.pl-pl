---
title: "Podstawowe informacje dotyczące transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa26531b1d2573b4bef49ec93f4205716227e25b
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="transaction-fundamentals"></a>Podstawowe informacje dotyczące transakcji
Transakcje powiązania wielu zadań jednocześnie. Na przykład załóżmy, że aplikacja wykonuje dwa zadania. Najpierw tworzy nową tabelę w bazie danych. Następnie wywołuje obiekt specjalne do zbierania, formatowania i wstawianie danych w nowej tabeli. Te dwa zadania są powiązane i wzajemnie nawet wtedy, w taki sposób, że ma zostać Unikaj tworzenia nowej tabeli, o ile nie można wypełniać danych. Wykonywanie zadania, zarówno w zakresie pojedynczą transakcję wymusza połączenie między nimi. Jeśli drugie zadanie nie powiedzie się, pierwsze zadanie jest przywrócenie punkt przed utworzeniem nowej tabeli.  
  
 Aby zapewnić zachowanie przewidywalne, wszystkie transakcje musi mieć podstawowe właściwości ACID (częściowych, spójne, izolowane i trwałe). Te właściwości wymuszać stosowanie rolę transakcji krytycznym wykonywanie oferty. Aby uzyskać więcej informacji na kwasu, zobacz [właściwości ACID](http://go.microsoft.com/fwlink/?LinkId=98791). Podsumowanie kwas gwarantuje zadania powodzenie lub niepowodzenie jako jednostki związane z zestawu. W transakcji albo przetwarzania terminologii transakcji zatwierdza lub przerywa. Można zatwierdzić transakcji wszyscy uczestnicy należy zagwarantować, wszelkie zmiany w danych będą trwałe. Zmiany muszą zostać zachowane niezależnie awarie systemu lub inne nieprzewidziane zdarzenia. Jeśli pojedynczego uczestnika nie powiedzie się gwarancji, cała transakcja nie powiedzie się. Wszystkie zmiany danych w zakresie transakcji zostaną przywrócone do określonego punktu zestawu.  
  
 Transakcja może zostać ograniczona do zasobu pojedynczej danych, takich jak kolejki bazy danych lub wiadomość. W tym scenariuszu transakcji lokalnej jest zarządzany przez Menedżera transakcji udostępnione przez <xref:System.Transactions> , który generuje wydajność. Kontrolowane przez zasób danych, transakcje te są wydajne i łatwy w zarządzaniu.  
  
 Transakcje mogą obejmować wielu zasobów danych. Transakcje rozproszone zapewnić możliwość zawierać kilka różnych operacji występujących na różnych systemów w jednym przebiegu lub niepowodzenie akcji. W tym scenariuszu transakcji są koordynowany przez transakcję Koordynator MSDTC (Microsoft Distributed), który znajduje się w każdym systemie.  
  
 Podczas opracowywania transakcyjnych aplikacji przy użyciu klas dostarczonych przez <xref:System.Transactions>, nie trzeba martwić się o rodzaju transakcji należy lub związane z Menedżera transakcji. <xref:System.Transactions> Infrastruktury automatycznie zarządza to dla Ciebie.  
  
 Podczas tworzenia transakcji można określić poziom izolacji, która ma zastosowanie do transakcji. Poziom izolacji, zdefiniowane przez <xref:System.Transactions.IsolationLevel> wyliczenia, określa poziom dostępu inne transakcje będzie mieć danych dotyczy transakcji.  
  
 Można utworzyć transakcji za pomocą ADO.NET, <xref:System.EnterpriseServices>, lub transakcyjnych modelu programowania pochodzącymi <xref:System.Transactions> przestrzeni nazw. [Funkcje oferowane przez bibliotekę System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) temacie opisano funkcje, które służy do pisania aplikacji transakcyjnej przy użyciu <xref:System.Transactions> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje oferowane przez bibliotekę System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)
