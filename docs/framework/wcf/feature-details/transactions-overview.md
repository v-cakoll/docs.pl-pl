---
title: "Omówienie transakcji WCF (Windows Communication Foundation)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 480c7ca971eeb7f232517057efe4033f177b26b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a>Omówienie transakcji WCF (Windows Communication Foundation)
Transakcje umożliwiają do grupowania zestawu działań lub operacji w pojedynczą jednostkę niepodzielnych wykonywania. Transakcja jest to kolekcja operacji z następującymi właściwościami:  
  
-   Niepodzielność. Dzięki temu, że wszystkie aktualizacje ukończone na podstawie określonej transakcji są zatwierdzone i zapewniana trwałość lub są one wszystkich zostało przerwane i z powrotem obniżyć do poprzedniego stanu.  
  
-   Spójność. Gwarantuje to, że zmiany wprowadzone w ramach transakcji reprezentują transformację z jednego spójnego stanu do innego. Na przykład przeniesienia pieniędzy z konta bankowego konta oszczędności transakcji nie zmienia kwotę w ogólnej konta bankowego.  
  
-   Izolacja. Zapobiega to transakcji z obserwowania niezatwierdzone zmiany należących do innych równoczesnych transakcji. Izolacja udostępnia abstrakcję współbieżności przy jednoczesnym zapewnieniu jednej transakcji nie mogą mieć nieoczekiwane wpływ na wykonywanie innej transakcji.  
  
-   Trwałość. Oznacza to, że po zatwierdzone, aktualizacje zarządzanych zasobów (takich jak rekordu bazy danych) będą trwałe w wypadku awarii.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zawiera bogaty zestaw funkcji, które umożliwiają tworzenie transakcji rozproszonych w aplikacji usługi sieci Web.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zapewnia obsługę protokołu WS-AtomicTransaction (WS-AT), która umożliwia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji przepływ transakcji na współdziałanie aplikacji, takich jak współdziałanie usług sieci Web utworzony za pomocą innych technologii. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje również obsługę protokołu transakcji OLE, którego można użyć w scenariuszach, w którym nie ma potrzeby międzyoperacyjnego funkcji umożliwiających przepływu transakcji.  
  
 Plik konfiguracji aplikacji służy do konfigurowania wiązania, aby włączyć lub wyłączyć przepływu transakcji, a także ustawić protokół transakcji odpowiednią dla wiązania. Ponadto można ustawić limity czasu transakcji na poziomie usługi przy użyciu pliku konfiguracji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Włączanie przepływu transakcji](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 Atrybuty transakcji w <xref:System.ServiceModel> przestrzeni nazw można wykonać następujące czynności:  
  
-   Konfigurowanie limitów czasu transakcji i poziom izolacji filtrowanie przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu.  
  
-   Włącz funkcje transakcji i skonfigurować za pomocą zachowania ukończenia transakcji <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu.  
  
-   Użyj <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybutów w metodzie kontraktu, aby wymagać, akceptować lub odrzucać przepływu transakcji.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Atrybuty transakcji elementu ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty transakcji elementu ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [Włączanie przepływu transakcji](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
