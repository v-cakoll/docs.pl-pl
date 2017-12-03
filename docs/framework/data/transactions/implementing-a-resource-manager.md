---
title: "Implementowanie Menedżera zasobów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5c153f6-4419-49e3-a5f1-a50ae4c81bf3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d9fe72090de3722137c2b0c2190c11f190be5fbc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-a-resource-manager"></a>Implementowanie Menedżera zasobów
Poszczególne zasoby używane w transakcji jest zarządzane przez Menedżera zasobów, których działania są koordynowany przez Menedżera transakcji. Menedżer zasobów działa we współpracy z menedżerem transakcji, aby zapewnić aplikacji niepodzielność i izolacji. Microsoft SQL Server, kolejki komunikatów trwałe, tabelami skrótów w pamięci są wszystkie przykłady menedżerowie zasobów.  
  
 Menedżer zasobów zarządza trwałe lub nietrwała danych. Trwałość (lub odwrotnie niestabilności ich) zasobu menedżera odwołuje się do tego, czy Menedżera zasobów obsługuje odzyskiwanie po awarii. Jeśli Menedżera zasobów obsługuje odzyskiwanie po awarii, utrzymuje danych do trwałego magazynu podczas fazy 1. (przygotowanie) tak, aby w przypadku awarii Menedżera zasobów, można ponownie zarejestrować transakcji po odzyskiwania i wykonać odpowiednie akcje w oparciu o powiadomienia otrzymane z menedżerem transakcji. Ogólnie rzecz biorąc, menedżerów zasobów volatile zarządzania volatile zasoby, takie jak struktury danych w pamięci (na przykład w pamięci nietransakcyjnego hashtable) oraz menedżerowie zasobów trwałe zarządzania zasoby, które mają większą trwałość magazynu zapasowego (na przykład Baza danych, których magazynu zapasowego jest dysku).  
  
 Aby zasób, aby uczestniczyć w transakcji należy zarejestrować w transakcji. <xref:System.Transactions.Transaction> Klasa definiuje zestaw metod, których nazwy zaczynają się od **Enlist** zawierających tę funkcję. Różnych **Enlist** metody odpowiadają różne rodzaje rejestracji, który mógł zostać Menedżera zasobów. W szczególności użyj <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody dla lotnych zasoby i <xref:System.Transactions.Transaction.EnlistDurable%2A> metody dla trwałego zasobów. Dla uproszczenia po podjęcie decyzji o użyciu <xref:System.Transactions.Transaction.EnlistDurable%2A> lub <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody w zależności od obsługi trwałości z zasobów, należy zarejestrować zasobu do udziału w dwie fazy zatwierdzania (2PC) przez zaimplementowanie <xref:System.Transactions.IEnlistmentNotification> interfejs użytkownika Menedżer zasobów. Aby uzyskać więcej informacji dotyczących 2PC, zobacz [Zatwierdzanie transakcji w jednofazowy i wielu fazy](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md).  
  
 Przez wywołanie tej metody, Menedżer zasobów zapewnia ona pobiera wywołania zwrotne z menedżerem transakcji po zatwierdzeniu lub przerwaniu transakcji. Istnieje jedno wystąpienie <xref:System.Transactions.IEnlistmentNotification> na rejestracji. Zazwyczaj znajduje się jeden rejestracji na transakcję, ale można zarejestrować wielokrotnie w ramach jednej transakcji Menedżera zasobów.  
  
 Po rejestracji Menedżera zasobów odpowiada na żądania transakcji. Menedżer zasobów trwałe przechowuje wystarczających informacji do pozwalać na jego cofnąć lub ponowić transakcji pracy zasobów, że zarządza. Istnieje wiele sposobów, w tym; przechowywanie wersji danych lub utrzymywanie dziennika zmian są dwie metody wspólne.  
  
 Jeśli aplikacja została zatwierdzona transakcji, Menedżer transakcji inicjuje dwufazowego protokołu wykonania. Menedżer transakcji najpierw pyta, czy każdy Menedżera zasobów Jeśli jest gotowa do zatwierdzania transakcji. Menedżer zasobów musi przygotowania do zatwierdzenia — jej przygotowuje się do zatwierdzenia lub przerwania transakcji.  
  
 W fazie przygotowanie Menedżera zasobów trwałe rejestruje stara i Nowa danych w magazynie stabilna, dzięki czemu Menedżera zasobów można go odzyskać nawet w przypadku awarii systemu. Jeśli Menedżera zasobów można przygotować, informuje menedżera transakcji jego głos na zatwierdzenia lub przerwania transakcji. Jeśli wszystkie usługi resource manager zgłasza błąd do przygotowania, Menedżer transakcji wysyła polecenie wycofania do każdego Menedżera zasobów i wskazuje niepowodzenie zatwierdzenia do aplikacji.  
  
 Po przygotowaniu Menedżera zasobów musi czekać, aż otrzyma zatwierdzania lub przerwania wywołania zwrotnego z menedżerem transakcji w fazie 2. Zazwyczaj całego protokołu przygotowanie i zatwierdzania kończy w ułamku sekundy. Jeśli występują awarie systemu lub łączności, zatwierdzania lub przerwania powiadomień nie może pojawić się dla minuty lub godziny. W tym okresie Menedżera zasobów jest w stanie wątPLiwości wyniku transakcji. Nie wiedzieć, czy zatwierdzeniu lub przerwaniu transakcji. Menedżer zasobów jest w stanie wątPLiwości transakcji, zapewnia dane zmodyfikowany przez utrzymywanie transakcji zablokowane, a tym samym izolowanie te zmiany innych transakcji.  
  
 Gdy Menedżer zasobów nie powiodło się, wszystkich jej znajdujących się w wykazie transakcji zostało przerwane z wyjątkiem tych, które zostały przygotowane lub zadeklarowane przed awarii. Po ponownym uruchomieniu Menedżera zasobów trwałe rekonstruuje zatwierdzone stanu zasobów, którymi zarządza pobierając prepare informacje zapisane w fazie przygotowania i zatwierdzane lub przerywa daną transakcję.  
  
 Podsumowanie Protokół dwufazowego i menedżerów zasobów połączyć wykonywanie transakcji częściowych i trwałe.  
  
 <xref:System.Transactions.Transaction> Klasa udostępnia także <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodę, aby zarejestrować awansowanie jednego etapu rejestracji (PSPE). Dzięki temu trwałe zasobu manager (MB), hosta i "własnością" transakcji, która może zostać później przekazany do były zarządzane przez MSDTC, jeśli to konieczne. Aby uzyskać więcej informacji o tym, zobacz [Optymalizacja za pomocą pojedynczego zatwierdzić fazy i awansowanie pojedyncze powiadomienia fazy](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 W następujących tematach opisano kroki zwykle następuje Menedżera zasobów.  
  
 [Rejestrowanie zasobów jako uczestnicy transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)  
  
 Opisuje, jak trwałe zasobu można zarejestrować w transakcji.  
  
 [Zatwierdzanie transakcji w jednofazowy i wielu fazy](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)  
  
 Opisuje, jak Zatwierdź powiadomień i przygotowania zatwierdzanie z użytkownikiem odpowiada Menedżera zasobów.  
  
 [Odzyskiwanie systemu](../../../../docs/framework/data/transactions/performing-recovery.md)  
  
 Opisuje sposób trwałego menedżerem przywraca po awarii.  
  
 [Poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md)  
  
 Opisuje sposób trzy poziomy zaufania System.Transactions ograniczyć dostęp dla typów zasobów, które <xref:System.Transactions> przedstawia.  
  
 [Optymalizacja za pomocą pojedynczego zatwierdzić fazy i awansowanie pojedyncze powiadomienia fazy](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
  
 Zawiera wskazówki optymalizacji dostępne do implementacji menedżerowie zasobów.
