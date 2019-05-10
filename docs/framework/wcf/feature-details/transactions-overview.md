---
title: Omówienie transakcji WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 1c3589b336ee8982cd6d694112e4c1f784f59ad2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585783"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Omówienie transakcji WCF (Windows Communication Foundation)
Transakcje zapewniają sposób grupowania zestawu akcji lub operacji w pojedynczą jednostkę niepodzielne wykonywania. Transakcja jest to kolekcja operacji z następującymi właściwościami:  
  
- Niepodzielność. Daje to gwarancję, że wszystkie aktualizacje ukończone na podstawie określonej transakcji są zatwierdzone i zapewniana trwałość lub są one wszystkie zostało przerwane i z powrotem obniżyć do poprzedniego stanu.  
  
- Spójność. Gwarantuje to, że zmiany wprowadzone w ramach transakcji reprezentuje przekształcenie z jednego spójnego stanu do drugiego. Na przykład transakcji, która przesyła pieniądze z konta bankowego na rachunek oszczędnościowy nie zmienia kwotę, w ramach ogólnej konta banku.  
  
- Izolacja. Zapobiega to transakcja może obserwować niezatwierdzone zmiany należących do innych równoczesnych transakcji. Izolacja zapewnia abstrakcję przy jednoczesnym zapewnieniu jedna transakcja współbieżności nie może mieć nieoczekiwane wpływ na wykonanie innej transakcji.  
  
- Trwałość. Oznacza to, że po zatwierdzeniu aktualizacji do zarządzanych zasobów (na przykład rekordem bazy danych) będą trwałe także w przypadku awarii.  
  
 Windows Communication Foundation (WCF) zapewnia bogaty zestaw funkcji, które umożliwiają tworzenie transakcje rozproszone w aplikacji usługi sieci Web.  
  
 Usługi WCF implementuje obsługę protokołu WS-AtomicTransaction (WS-AT), który umożliwia aplikacjom WCF przepływ transakcji do aplikacji międzyoperacyjnych, takich jak interoperacyjne usług sieci Web utworzone przy użyciu technologii innych firm. Usługi WCF implementuje również obsługę protokołu transakcji OLE, które mogą być używane w scenariuszach nie wymagających międzyoperacyjny funkcje przepływu transakcji.  
  
 Plik konfiguracji aplikacji umożliwiają skonfigurowanie powiązań, aby włączyć lub wyłączyć przepływ transakcji, a także ustawić protokół żądaną transakcji w powiązaniu. Ponadto można ustawić limity czasu transakcji na poziomie usługi przy użyciu pliku konfiguracji. Aby uzyskać więcej informacji, zobacz [Włączanie przepływu transakcji](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 Transakcja atrybutów w <xref:System.ServiceModel> przestrzeni nazw pozwala wykonać następujące czynności:  
  
- Konfigurowanie limitów czasu transakcji i poziom izolacji filtrowanie przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu.  
  
- Włączyć funkcję transakcji i skonfigurować za pomocą zachowania ukończenia transakcji <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu.  
  
- Użyj <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybutów w metodzie umowy, aby wymagać, zezwolenie lub zablokowanie przepływu transakcji.  
  
 Aby uzyskać więcej informacji, zobacz [atrybuty transakcji elementu ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Zobacz także

- [Atrybuty transakcji elementu ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)
- [Włączanie przepływu transakcji](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
