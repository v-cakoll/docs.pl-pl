---
title: Funkcje oferowane przez bibliotekę System.Transactions
ms.date: 03/30/2017
ms.assetid: e458cef9-63b5-4401-b448-1536dcd9d9e5
ms.openlocfilehash: 6fc20f8249f37f69689fb3fc6b3144792badad3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793695"
---
# <a name="features-provided-by-systemtransactions"></a>Funkcje oferowane przez bibliotekę System.Transactions
W tej sekcji opisano sposób korzystania z funkcji oferowanych przez <xref:System.Transactions> nazw można zapisać własne transakcyjnych Menedżera zasobów i aplikacji. W szczególności w tej sekcji opisano sposób tworzenia i uczestniczyć w transakcji (lokalnego lub rozproszonej) z jednego lub wielu uczestników.  
  
## <a name="overview-of-systemtransactions"></a>Omówienie System.Transactions  
 Infrastruktury zapewnianej przez klasy w <xref:System.Transactions> nazw sprawia, że transakcyjnych programowania proste i wydajne dzięki obsłudze transakcji zainicjowanej przez program SQL Server, ADO.NET, kolejkowania wiadomości (MSMQ) i transakcji rozproszonych firmy Microsoft Koordynator (MSDTC). <xref:System.Transactions> Przestrzeń nazw zawiera zarówno wyraźne programowania model na podstawie <xref:System.Transactions.Transaction> klasy, a także niejawne programowania modelu przy użyciu <xref:System.Transactions.TransactionScope> klasy, w którym transakcje są automatycznie zarządzane przez infrastrukturę. Aby uzyskać więcej informacji na temat sposobu tworzenia transakcyjnych aplikacji za pomocą tych dwóch modeli, zobacz [zapisywanie aplikacji transakcyjnej](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
 <xref:System.Transactions> Przestrzeń nazw zawiera także typy można zaimplementować Menedżera zasobów. Menedżer zasobów zarządza trwałe lub nietrwała danych używane w transakcji, a działanie we współpracy z menedżerem transakcji, aby zapewnić aplikacji niepodzielność i izolację gwarancji. Menedżer transakcji, który jest dostarczany przez <xref:System.Transactions> infrastruktury obsługuje transakcje obejmujące wiele zasobów lotnych lub trwałe pojedynczy zasób. Aby uzyskać więcej informacji dotyczących implementowania Menedżera zasobów, zobacz [implementowania Menedżera zasobów](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md).  
  
 Menedżer transakcji również przezroczysty Eskalowanie transakcji lokalnych transakcje rozproszone przez koordynowanie z menedżerem transakcji na dysku, takich jak usługi, gdy Menedżer dodatkowych zasobów trwałe współdziała z transakcją. Istnieją dwie metody klucza który <xref:System.Transactions> infrastruktury zapewnia lepszą wydajność.  
  
- Eskalacja dynamiczne, który zapewnia, że <xref:System.Transactions> infrastruktury tylko uruchamia MSDTC, gdy transakcji obejmujących na wielu rozproszonych zasobów. Aby uzyskać więcej informacji o eskalacji dynamicznych. zobacz [Eskalacja zarządzania transakcjami](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tematu.  
  
- Awansowanie rejestracji, co umożliwia zasobu, takie jak bazy danych, przejęcie na własność transakcji, jeśli jest tylko typy jednostek uczestnictwa w transakcji. Później, jeśli to konieczne, <xref:System.Transactions> infrastruktury nadal może eskalować zarządzania transakcji MSDTC. Dodatkowo zmniejsza to ryzyko przy użyciu MSDTC. Awansowanie rejestracji są objęte głębokość w temacie[Optymalizacja za pomocą zatwierdzania jednofazowego i awansowanie powiadomienia jednofazowego](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 <xref:System.Transactions> Nazw definiuje trzy poziomy zaufania - AllowPartiallyTrustedCallers (APTCA), DistributedTransactionPermission(DTP) i pełną zaufania - ograniczenia dla typów zasobów do niego dostęp ujawnia. Aby uzyskać więcej informacji na temat różnych poziomów zaufania, zobacz [poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
### <a name="writing-a-transactional-application"></a>Zapisywanie aplikacji transakcyjnej  
 <xref:System.Transactions> Przestrzeń nazw zawiera dwa modele do tworzenia transakcyjnych aplikacji. [Implementowanie transakcji niejawnej przy użyciu zakresu transakcji](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) w tym artykule opisano sposób, w jaki <xref:System.Transactions> przestrzeń nazw obsługuje tworzenie niejawne transakcji za pomocą <xref:System.Transactions.TransactionScope> klasy.  
  
 [Implementowanie transakcji jawnej przy użyciu Commitabletransakction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md) w tym artykule opisano sposób, w jaki <xref:System.Transactions> przestrzeń nazw obsługuje tworzenie jawnego transakcji za pomocą <xref:System.Transactions.CommittableTransaction> klasy.  
  
 Dodatkowe tematy dotyczące zapisywania transakcyjnych aplikacji, zobacz [zapisywanie aplikacji transakcyjnej](../../../../docs/framework/data/transactions/writing-a-transactional-application.md).  
  
### <a name="implementing-a-resource-manager"></a>Implementowania Menedżera zasobów  
 Aby zaimplementować Menedżera zasobów, które mogą uczestniczyć w transakcji, zobacz [implementowania Menedżera zasobów](../../../../docs/framework/data/transactions/implementing-a-resource-manager.md). W tej sekcji opisano rejestracja zasobu, zatwierdzanie transakcji, odzyskiwania po awarii i optymalizacji najlepszych rozwiązań.
