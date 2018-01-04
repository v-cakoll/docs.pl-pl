---
title: Modele transakcji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 782a6b5bdb206d285d619b8085993b591785aca5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-models"></a>Modele transakcji
W tym temacie opisuje relację między modele programowania transakcji i składników infrastruktury udostępniane przez firmę Microsoft.  
  
 Podczas korzystania z transakcji w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], ważne jest, aby zrozumieć, że nie należy wybierać między różne modele transakcyjnych, ale raczej działające w różnych warstwach zintegrowanego i spójny model.  
  
 W poniższych sekcjach opisano trzy składniki podstawowe transakcji.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation transakcji  
 Obsługa transakcji w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umożliwia pisanie transakcyjnych usług. Ponadto z jego obsługę protokołu WS-AtomicTransaction (WS-AT), aplikacje można przepływu transakcji usługi sieci Web utworzony za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lub innych technologii.  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługę lub aplikację, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje transakcji zapewniają atrybutów i konfiguracja dla deklaratywnie określenie, kiedy infrastruktury należy utworzyć, przepływu i zsynchronizować transakcji.  
  
## <a name="systemtransactions-transactions"></a>System.Transactions transakcji  
 <xref:System.Transactions> Przestrzeń nazw obejmuje zarówno jawne programowania model na podstawie <xref:System.Transactions.Transaction> klasy, a także niejawne programowania modelu przy użyciu <xref:System.Transactions.TransactionScope> klasy, w którym infrastruktury automatycznie zarządza transakcji.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie aplikacji transakcyjnej przy użyciu tych dwóch modeli, zobacz [zapisywania transakcyjnych aplikacji](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługę lub aplikację, <xref:System.Transactions> zapewnia model programowania do tworzenia transakcji w aplikacji klienta i do jawnie interakcji z transakcji, gdy jest to wymagane w ramach usługi.  
  
## <a name="msdtc-transactions"></a>Transakcji usługi MSDTC  
 Koordynator transakcji rozproszonych (MSDTC) firmy Microsoft jest Menedżera transakcji, która zapewnia obsługę transakcji rozproszonych.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Podręcznik programisty DTC](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi lub aplikacji, usługi MSDTC zapewnia infrastrukturę do koordynacji transakcji utworzone w ramach klienta lub usługę.
