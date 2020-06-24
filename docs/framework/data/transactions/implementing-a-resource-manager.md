---
title: Implementowanie Menedżera zasobów
description: Implementowanie Menedżera zasobów w programie .NET. Menedżer zasobów zarządza zasobami używanymi w transakcjach. Menedżer transakcji koordynuje akcje Menedżera zasobów.
ms.date: 03/30/2017
ms.assetid: d5c153f6-4419-49e3-a5f1-a50ae4c81bf3
ms.openlocfilehash: bf40c6eaee35a5a548c6de4a286e46c4d4a66aca
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141852"
---
# <a name="implementing-a-resource-manager"></a>Implementowanie Menedżera zasobów
Poszczególne zasoby używane w transakcji jest zarządzane przez Menedżera zasobów, których działania są koordynowany przez Menedżera transakcji. Menedżerowie zasobów pracują we współpracy z menedżerem transakcji w celu zapewnienia aplikacji z gwarancją niepodzielności i izolacji. Microsoft SQL Server, trwałe kolejki komunikatów, tabele skrótów w pamięci to wszystkie przykłady menedżerów zasobów.  
  
 Menedżer zasobów zarządza trwałe lub nietrwała danych. Trwałość (lub odwrotnie niestabilności ich) zasobu menedżera odwołuje się do tego, czy Menedżera zasobów obsługuje odzyskiwanie po awarii. Jeśli Menedżera zasobów obsługuje odzyskiwanie po awarii, utrzymuje danych do trwałego magazynu podczas fazy 1. (przygotowanie) tak, aby w przypadku awarii Menedżera zasobów, można ponownie zarejestrować transakcji po odzyskiwania i wykonać odpowiednie akcje w oparciu o powiadomienia otrzymane z menedżerem transakcji. Ogólnie rzecz biorąc Menedżerowie zasobów lotnych zarządzają zasobami nietrwałymi, takimi jak struktura danych w pamięci (na przykład w pamięci podręcznej), a trwałe Menedżerowie zasobów zarządzają zasobami, które mają bardziej trwały magazyn zapasowy (na przykład baza danych, której magazyn zapasowy jest dyskiem).  
  
 Aby zasób, aby uczestniczyć w transakcji należy zarejestrować w transakcji. <xref:System.Transactions.Transaction>Klasa definiuje zestaw metod, których nazwy zaczynają się od **rejestracji** , która zapewnia tę funkcję. Różne metody **rejestracji** odnoszą się do różnych typów rejestracji, które może mieć Menedżer zasobów. W szczególności użyj <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody dla lotnych zasoby i <xref:System.Transactions.Transaction.EnlistDurable%2A> metody dla trwałego zasobów. Aby zapewnić prostotę, po podjęciu decyzji o tym, czy użyć <xref:System.Transactions.Transaction.EnlistDurable%2A> <xref:System.Transactions.Transaction.EnlistVolatile%2A> metody lub w oparciu o wsparcie trwałości zasobu, należy zarejestrować zasób do wzięcia udziału w dwóch fazach zatwierdzania (2PC) przez implementację <xref:System.Transactions.IEnlistmentNotification> interfejsu dla Menedżera zasobów. Aby uzyskać więcej informacji na temat 2PC, zobacz temat [zatwierdzanie transakcji w ramach jednej fazy i wielofazowej](committing-a-transaction-in-single-phase-and-multi-phase.md).  
  
 Przez wywołanie tej metody, Menedżer zasobów zapewnia ona pobiera wywołania zwrotne z menedżerem transakcji po zatwierdzeniu lub przerwaniu transakcji. Istnieje jedno wystąpienie <xref:System.Transactions.IEnlistmentNotification> na rejestracji. Zwykle istnieje jedna Rejestracja na transakcję, ale Menedżer zasobów może wybrać wiele razy w tej samej transakcji.  
  
 Po rejestracji Menedżera zasobów odpowiada na żądania transakcji. Menedżer zasobów trwałe przechowuje wystarczających informacji do pozwalać na jego cofnąć lub ponowić transakcji pracy zasobów, że zarządza. Istnieje wiele sposobów, w tym; przechowywanie wersji danych lub utrzymywanie dziennika zmian są dwie metody wspólne.  
  
 Gdy aplikacja zatwierdzi transakcję, Menedżer transakcji inicjuje dwufazowego protokołu zatwierdzania. Menedżer transakcji najpierw pyta, czy każdy Menedżera zasobów Jeśli jest gotowa do zatwierdzania transakcji. Menedżer zasobów musi przygotowania do zatwierdzenia — jej przygotowuje się do zatwierdzenia lub przerwania transakcji.  
  
 W fazie przygotowanie Menedżera zasobów trwałe rejestruje stara i Nowa danych w magazynie stabilna, dzięki czemu Menedżera zasobów można go odzyskać nawet w przypadku awarii systemu. Jeśli Menedżera zasobów można przygotować, informuje menedżera transakcji jego głos na zatwierdzenia lub przerwania transakcji. Jeśli którykolwiek z menedżerów zasobów zgłosi błąd przygotowania, Menedżer transakcji wysyła polecenie wycofania do każdego Menedżera zasobów i wskazuje niepowodzenie zatwierdzenia aplikacji.  
  
 Po przygotowaniu Menedżera zasobów musi czekać, aż otrzyma zatwierdzania lub przerwania wywołania zwrotnego z menedżerem transakcji w fazie 2. Zwykle cały protokół przygotowywania i zatwierdzania kończy się w części sekundy. Jeśli występują awarie systemu lub łączności, zatwierdzania lub przerwania powiadomień nie może pojawić się dla minuty lub godziny. W tym okresie Menedżera zasobów jest w stanie wątPLiwości wyniku transakcji. Nie wiedzieć, czy zatwierdzeniu lub przerwaniu transakcji. Menedżer zasobów jest w stanie wątPLiwości transakcji, zapewnia dane zmodyfikowany przez utrzymywanie transakcji zablokowane, a tym samym izolowanie te zmiany innych transakcji.  
  
 Gdy Menedżer zasobów nie powiodło się, wszystkich jej znajdujących się w wykazie transakcji zostało przerwane z wyjątkiem tych, które zostały przygotowane lub zadeklarowane przed awarii. Po ponownym uruchomieniu Menedżera zasobów trwałe rekonstruuje zatwierdzone stanu zasobów, którymi zarządza pobierając prepare informacje zapisane w fazie przygotowania i zatwierdzane lub przerywa daną transakcję.  
  
 Podsumowanie Protokół dwufazowego i menedżerów zasobów połączyć wykonywanie transakcji częściowych i trwałe.  
  
 <xref:System.Transactions.Transaction> Klasa udostępnia także <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> metodę, aby zarejestrować awansowanie jednego etapu rejestracji (PSPE). Dzięki temu trwałe zasobu manager (MB), hosta i "własnością" transakcji, która może zostać później przekazany do były zarządzane przez MSDTC, jeśli to konieczne. Aby uzyskać więcej informacji na ten temat, zobacz [Optymalizacja przy użyciu jednej fazy zatwierdzania i powiadomienia o pojedynczej fazie](optimization-spc-and-promotable-spn.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 W następujących tematach opisano kroki zwykle następuje Menedżera zasobów.  
  
 [Rejestrowanie zasobów jako uczestników transakcji](enlisting-resources-as-participants-in-a-transaction.md)  
  
 Opisuje, jak trwałe zasobu można zarejestrować w transakcji.  
  
 [Zatwierdzanie transakcji jednofazowe i wielofazowe](committing-a-transaction-in-single-phase-and-multi-phase.md)  
  
 Opisuje, jak Zatwierdź powiadomień i przygotowania zatwierdzanie z użytkownikiem odpowiada Menedżera zasobów.  
  
 [Odzyskiwanie systemu](performing-recovery.md)  
  
 Opisuje sposób trwałego menedżerem przywraca po awarii.  
  
 [Poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów](security-trust-levels-in-accessing-resources.md)  
  
 Opisuje sposób trzy poziomy zaufania System.Transactions ograniczyć dostęp dla typów zasobów, które <xref:System.Transactions> przedstawia.  
  
 [Optymalizacja za pomocą zatwierdzania jednofazowego i umożliwiającego awansowanie powiadomienia jednofazowego](optimization-spc-and-promotable-spn.md)  
  
 Opisuje praktyki optymalizacji dostępne dla implementacji menedżerów zasobów.
