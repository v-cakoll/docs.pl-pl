---
title: Konfiguracja transakcji modelu ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 79772d19ddaec041aa1fac936b9951731507b6e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184454"
---
# <a name="servicemodel-transaction-configuration"></a>Konfiguracja transakcji modelu ServiceModel
Windows Communication Foundation (WCF) udostępnia trzy atrybuty konfigurowania `transactionProtocol`transakcji `transactionTimeout`dla usługi: `transactionFlow`, , i .  
  
## <a name="configuring-transactionflow"></a>Konfigurowanie transactionFlow  
 Większość wstępnie zdefiniowanych powiązań WCF zapewnia `transactionFlow` `transactionProtocol` zawierają i atrybuty, dzięki czemu można skonfigurować powiązanie do akceptowania transakcji przychodzących dla określonego punktu końcowego przy użyciu określonego protokołu przepływu transakcji. Ponadto można użyć `transactionFlow` elementu i `transactionProtocol` jego atrybut do tworzenia własnych niestandardowych powiązania. Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [ \<powiązanie>](../../configure-apps/file-schema/wcf/bindings.md) i [schemat konfiguracji WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 Atrybut `transactionFlow` określa, czy przepływ transakcji jest włączony dla punktów końcowych usługi, które używają powiązania.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurowanie transakcjiProtocol  
 Atrybut `transactionProtocol` określa protokół transakcji do użycia z punktami końcowymi usługi, które używają powiązania.  
  
 Poniżej przedstawiono przykład sekcji konfiguracji, która konfiguruje określone powiązanie do obsługi przepływu transakcji, a także użyj protokołu WS-AtomicTransaction.  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a>Konfigurowanie limitu czasu transakcji  
 Atrybut usługi WCF można skonfigurować w `transactionTimeout` `behavior` elemencie pliku konfiguracyjnego. Poniższy kod pokazuje, jak to zrobić.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 Atrybut `transactionTimeout` określa okres, w którym musi zakończyć się nowa transakcja utworzona w usłudze. Jest on używany <xref:System.Transactions.TransactionScope> jako limit czasu dla każdej operacji, która <xref:System.ServiceModel.OperationBehaviorAttribute> ustanawia nową <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> transakcję, `true`a jeśli jest stosowana, właściwość jest ustawiona na .  
  
 Limit czasu określa czas od utworzenia transakcji do zakończenia fazy 1 w protokole zatwierdzania dwufazowego.  
  
 Jeśli ten atrybut jest `service` ustawiony w sekcji konfiguracji, należy zastosować co <xref:System.ServiceModel.OperationBehaviorAttribute>najmniej jedną <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> metodę odpowiedniej `true`usługi z , w którym właściwość jest ustawiona na .  
  
 Należy zauważyć, że używana wartość przesuwu czasu jest mniejszą wartością między tym `transactionTimeout` ustawieniem konfiguracji a dowolną <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwością.  
  
## <a name="see-also"></a>Zobacz też

- [\<wiążące>](../../configure-apps/file-schema/wcf/bindings.md)
- [Schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
