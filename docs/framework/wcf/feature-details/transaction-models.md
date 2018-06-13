---
title: Modele transakcji
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499027"
---
# <a name="transaction-models"></a>Modele transakcji
W tym temacie opisuje relację między modele programowania transakcji i składników infrastruktury udostępniane przez firmę Microsoft.  
  
 Używanie transakcji w systemie Windows Communication Foundation (WCF), jest pamiętać, że nie należy wybierać między różne modele transakcyjnych, ale raczej działające w różnych warstwach zintegrowanego i spójny model.  
  
 W poniższych sekcjach opisano trzy składniki podstawowe transakcji.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation transakcji  
 Obsługa transakcji w programie WCF umożliwia pisanie transakcyjnych usług. Ponadto jego obsługę protokołu WS-AtomicTransaction (WS-AT), aplikacje można przepływu transakcji usługi sieci Web utworzony za pomocą usługi WCF i technologia innych firm.  
  
 W aplikacji lub usługi WCF funkcje transakcji WCF zapewniają atrybutów i konfiguracja dla deklaratywnie określenie, kiedy infrastruktury należy utworzyć, przepływu i zsynchronizować transakcji.  
  
## <a name="systemtransactions-transactions"></a>System.Transactions transakcji  
 <xref:System.Transactions> Przestrzeń nazw obejmuje zarówno jawne programowania model na podstawie <xref:System.Transactions.Transaction> klasy, a także niejawne programowania modelu przy użyciu <xref:System.Transactions.TransactionScope> klasy, w którym infrastruktury automatycznie zarządza transakcji.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia aplikacji transakcyjnej przy użyciu tych dwóch modeli, zobacz [zapisywania transakcyjnych aplikacji](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 W aplikacji lub usługi WCF <xref:System.Transactions> zapewnia model programowania do tworzenia transakcji w aplikacji klienta i do jawnie interakcji z transakcji, gdy jest to wymagane w ramach usługi.  
  
## <a name="msdtc-transactions"></a>Transakcji usługi MSDTC  
 Koordynator transakcji rozproszonych (MSDTC) firmy Microsoft jest Menedżera transakcji, która zapewnia obsługę transakcji rozproszonych.  
  
 Aby uzyskać więcej informacji, zobacz [Podręcznik programisty DTC](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 W aplikacji lub usługi WCF usługa MSDTC udostępnia infrastrukturę koordynacji transakcji utworzone w ramach klienta lub usługę.
