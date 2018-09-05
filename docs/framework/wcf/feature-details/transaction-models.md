---
title: Modele transakcji
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517786"
---
# <a name="transaction-models"></a>Modele transakcji
W tym temacie opisano relację między modele programowania transakcji i składników infrastruktury, zawierane z firmą Microsoft.  
  
 Za pomocą transakcji w Windows Communication Foundation (WCF), jest ważne dowiedzieć się, że są nie wybierzesz różnych modelach transakcyjnych, ale raczej działające w różnych warstwach zintegrowane i spójny model.  
  
 W poniższych sekcjach opisano trzy składniki podstawowe transakcji.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation transakcji  
 Obsługa transakcji w programie WCF umożliwia pisanie transakcyjnych usług. Ponadto obsługa protokołu WS-AtomicTransaction (WS-AT), aplikacje może przepływać transakcji usługi sieci Web utworzone przy użyciu usługi WCF i technologia firm.  
  
 Usługa WCF lub aplikacji funkcje transakcji programu WCF zawiera atrybuty i konfiguracja deklaratywne określenie sposobem i czasem infrastruktury należy utworzyć, flow i zsynchronizować transakcji.  
  
## <a name="systemtransactions-transactions"></a>Transakcje System.Transactions  
 <xref:System.Transactions> Przestrzeń nazw zawiera zarówno wyraźne programowania model na podstawie <xref:System.Transactions.Transaction> klasy, a także niejawne programowania modelu przy użyciu <xref:System.Transactions.TransactionScope> klasy, w którym infrastruktury automatycznie zarządza transakcji.  
  
 Aby uzyskać więcej informacji na temat sposobu tworzenia transakcyjnych aplikacji za pomocą tych dwóch modeli, zobacz [zapisywanie aplikacji transakcyjnej](https://go.microsoft.com/fwlink/?LinkId=94947).  
  
 W aplikacji lub usługi WCF <xref:System.Transactions> zapewnia model programowania do tworzenia transakcji w ramach aplikacji klienta i do jawnie wchodzenie w interakcje z transakcji, gdy jest to wymagane w ramach usługi.  
  
## <a name="msdtc-transactions"></a>Usługa MSDTC transakcji  
 Koordynator transakcji rozproszonych (MSDTC) firmy Microsoft jest Menedżer transakcji, który zapewnia obsługę transakcji rozproszonych.  
  
 Aby uzyskać więcej informacji, zobacz [Podręcznik programisty usługi DTC](https://go.microsoft.com/fwlink/?LinkId=94948).  
  
 W usłudze WCF lub aplikacji usługi MSDTC udostępnia infrastrukturę koordynacji transakcji utworzone w ramach klienta lub usługę.
