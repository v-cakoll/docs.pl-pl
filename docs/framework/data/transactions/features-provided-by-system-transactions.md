---
title: Funkcje oferowane przez bibliotekę System.Transactions
description: Zapoznaj się z funkcjami dostarczanymi przez przestrzeń nazw System. Transactions w programie .NET, aby napisać własną aplikację transakcji i Menedżera zasobów.
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 0278e9248305572c6156c6500f1fe51a8b3f3338
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141865"
---
# <a name="features-provided-by-systemtransactions"></a>Funkcje oferowane przez bibliotekę System.Transactions
W tej sekcji opisano, jak za pomocą funkcji udostępnionych przez <xref:System.Transactions> przestrzeń nazw napisać własną transakcyjną aplikację i Menedżera zasobów. W tej sekcji opisano sposób tworzenia i uczestniczenia w transakcji (lokalnej lub rozproszonej) z jednym lub wieloma uczestnikami.  
  
## <a name="overview-of-systemtransactions"></a>Omówienie System.Transactions  
 Infrastruktura dostarczana przez klasy w <xref:System.Transactions> przestrzeni nazw sprawia, że programowanie transakcyjne jest proste i wydajne dzięki obsłudze transakcji zainicjowanych w SQL Server, ADO.NET, kolejkowania komunikatów (MSMQ) i Microsoft Distributed Transaction Coordinator (MSDTC). <xref:System.Transactions>Przestrzeń nazw zapewnia jawny model programowania oparty na <xref:System.Transactions.Transaction> klasie, a także niejawny model programowania korzystający z <xref:System.Transactions.TransactionScope> klasy, w którym transakcje są automatycznie zarządzane przez infrastrukturę. Aby uzyskać więcej informacji na temat tworzenia aplikacji transakcyjnej przy użyciu tych dwóch modeli, zobacz [pisanie aplikacji transakcyjnej](writing-a-transactional-application.md).  
  
 <xref:System.Transactions>Przestrzeń nazw udostępnia również typy umożliwiające zaimplementowanie Menedżera zasobów. Menedżer zasobów zarządza trwałymi lub nietrwałymi danymi używanymi w transakcji i współpracuje z menedżerem transakcji w celu zapewnienia aplikacji z gwarancją niepodzielności i izolacji. Menedżer transakcji, który jest dostarczany przez <xref:System.Transactions> infrastrukturę, obsługuje transakcje obejmujące wiele zasobów trwałych lub pojedynczy zasób trwały. Aby uzyskać więcej informacji na temat implementowania Menedżera zasobów, zobacz [implementowanie Menedżer zasobów](implementing-a-resource-manager.md).  
  
 Menedżer transakcji również przezroczysty Eskalowanie transakcji lokalnych transakcje rozproszone przez koordynowanie z menedżerem transakcji na dysku, takich jak usługi, gdy Menedżer dodatkowych zasobów trwałe współdziała z transakcją. Istnieją dwie metody klucza który <xref:System.Transactions> infrastruktury zapewnia lepszą wydajność.  
  
- Eskalacja dynamiczna, dzięki czemu <xref:System.Transactions> infrastruktura angażuje usługę MSDTC tylko wtedy, gdy transakcja obejmuje wiele zasobów rozproszonych. Aby uzyskać więcej informacji o eskalacji dynamicznych. Zobacz temat [Eskalacja zarządzania transakcjami](transaction-management-escalation.md) .  
  
- Awansowanie rejestracji, co umożliwia zasobu, takie jak bazy danych, przejęcie na własność transakcji, jeśli jest tylko typy jednostek uczestnictwa w transakcji. Później, jeśli to konieczne, <xref:System.Transactions> infrastruktury nadal może eskalować zarządzania transakcji MSDTC. Dodatkowo zmniejsza to ryzyko przy użyciu MSDTC. Rejestracje promocji są szczegółowo omówione w temacie Optymalizacja tematu[przy użyciu jednofazowego zatwierdzania i powiadomienia o pojedynczej fazie](optimization-spc-and-promotable-spn.md).  
  
 <xref:System.Transactions> Nazw definiuje trzy poziomy zaufania - AllowPartiallyTrustedCallers (APTCA), DistributedTransactionPermission(DTP) i pełną zaufania - ograniczenia dla typów zasobów do niego dostęp ujawnia. Aby uzyskać więcej informacji na temat różnych poziomów zaufania, zobacz [zabezpieczenia poziomów zaufania w temacie dostęp do zasobów](security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
### <a name="writing-a-transactional-application"></a>Pisanie aplikacji transakcyjnej  
 <xref:System.Transactions>Przestrzeń nazw zawiera dwa modele do tworzenia aplikacji transakcyjnych. [Implementacja niejawnej transakcji przy użyciu zakresu transakcji](implementing-an-implicit-transaction-using-transaction-scope.md) opisuje sposób, w jaki <xref:System.Transactions> przestrzeń nazw obsługuje tworzenie niejawnych transakcji przy użyciu <xref:System.Transactions.TransactionScope> klasy.  
  
 [Implementacja jawnej transakcji przy użyciu CommittableTransaction](implementing-an-explicit-transaction-using-committabletransaction.md) opisuje sposób, w jaki <xref:System.Transactions> przestrzeń nazw obsługuje tworzenie jawnych transakcji przy użyciu <xref:System.Transactions.CommittableTransaction> klasy.  
  
 Aby uzyskać dodatkowe tematy dotyczące pisania aplikacji transakcyjnej, zobacz [pisanie aplikacji transakcyjnej](writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Implementowanie Menedżer zasobów  
 Aby zaimplementować Menedżera zasobów, który może uczestniczyć w transakcji, zobacz [implementowanie Menedżer zasobów](implementing-a-resource-manager.md). W tej sekcji opisano rejestracja zasobu, zatwierdzanie transakcji, odzyskiwania po awarii i optymalizacji najlepszych rozwiązań.
