---
title: Konfiguracja transakcji modelu ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: e8c8c9ebff259ccd991768afb8cdf9925a66aad0
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141614"
---
# <a name="servicemodel-transaction-configuration"></a>Konfiguracja transakcji modelu ServiceModel
Windows Communication Foundation (WCF) oferuje trzy atrybuty do konfigurowania transakcji dla usługi: `transactionFlow`, `transactionProtocol`i `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Konfigurowanie transactionFlow  
 Większość wstępnie zdefiniowanych powiązań WCF zawiera atrybuty `transactionFlow` i `transactionProtocol`, dzięki czemu można skonfigurować powiązanie do akceptowania transakcji przychodzących dla określonego punktu końcowego przy użyciu określonego protokołu przepływu transakcji. Ponadto można użyć elementu `transactionFlow` i jego atrybutu `transactionProtocol` do utworzenia własnego powiązania niestandardowego. Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [\<powiązywanie >](../../configure-apps/file-schema/wcf/bindings.md) i [Schemat konfiguracji WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 Atrybut `transactionFlow` określa, czy przepływ transakcji jest włączony dla punktów końcowych usługi korzystających z tego powiązania.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurowanie element TransactionProtocol  
 Atrybut `transactionProtocol` określa protokół transakcji, który ma być używany z punktami końcowymi usługi, które korzystają z tego powiązania.  
  
 Poniżej znajduje się przykład sekcji konfiguracji, która służy do konfigurowania określonego powiązania do obsługi przepływu transakcji, a także korzystania z protokołu WS-AtomicTransaction.  
  
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
  
## <a name="configuring-transactiontimeout"></a>Konfigurowanie transactionTimeout  
 Atrybut `transactionTimeout` dla usługi WCF można skonfigurować w elemencie `behavior` pliku konfiguracji. Poniższy kod demonstruje, jak to zrobić.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 Atrybut `transactionTimeout` określa czas, w którym należy zakończyć nową transakcję utworzoną w usłudze. Jest używany jako <xref:System.Transactions.TransactionScope> limit czasu dla każdej operacji, która ustanawia nową transakcję, a jeśli <xref:System.ServiceModel.OperationBehaviorAttribute> jest stosowany, właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest ustawiona na `true`.  
  
 Limit czasu określa czas od utworzenia transakcji do zakończenia fazy 1 w protokole zatwierdzania dwufazowego.  
  
 Jeśli ten atrybut jest ustawiony w sekcji konfiguracji `service`, należy zastosować co najmniej jedną metodę odpowiedniej usługi z <xref:System.ServiceModel.OperationBehaviorAttribute>, w której Właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest ustawiona na `true`.  
  
 Należy zauważyć, że wartość limitu czasu jest mniejsza niż wartość tego ustawienia konfiguracji `transactionTimeout` i każdej właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [> powiązań \<](../../configure-apps/file-schema/wcf/bindings.md)
- [Schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
