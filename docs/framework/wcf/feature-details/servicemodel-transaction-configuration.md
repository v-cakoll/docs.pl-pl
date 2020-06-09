---
title: Konfiguracja transakcji modelu ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 1d04a7bb756cccb33b436c1f57decc0249764828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600338"
---
# <a name="servicemodel-transaction-configuration"></a>Konfiguracja transakcji modelu ServiceModel
Windows Communication Foundation (WCF) oferuje trzy atrybuty do konfigurowania transakcji dla usługi: `transactionFlow` , `transactionProtocol` , i `transactionTimeout` .  
  
## <a name="configuring-transactionflow"></a>Konfigurowanie transactionFlow  
 Większość wstępnie zdefiniowanych powiązań WCF zawiera `transactionFlow` `transactionProtocol` atrybuty i, dzięki czemu można skonfigurować powiązanie do akceptowania transakcji przychodzących dla określonego punktu końcowego przy użyciu określonego protokołu przepływu transakcji. Ponadto można użyć `transactionFlow` elementu i jego `transactionProtocol` atrybutu do utworzenia własnego powiązania niestandardowego. Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) i [Schemat konfiguracji WCF](../../configure-apps/file-schema/wcf/index.md).  
  
 Ten `transactionFlow` atrybut określa, czy przepływ transakcji jest włączony dla punktów końcowych usługi korzystających z tego powiązania.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurowanie element TransactionProtocol  
 Ten `transactionProtocol` atrybut określa protokół transakcji, który ma być używany z punktami końcowymi usługi, które korzystają z tego powiązania.  
  
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
 `transactionTimeout`Atrybut dla usługi WCF można skonfigurować w `behavior` elemencie pliku konfiguracji. Poniższy kod demonstruje, jak to zrobić.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 Ten `transactionTimeout` atrybut określa przedział czasu, w którym należy zakończyć nową transakcję utworzoną w usłudze. Jest używany jako <xref:System.Transactions.TransactionScope> limit czasu dla każdej operacji, która ustanawia nową transakcję, a jeśli <xref:System.ServiceModel.OperationBehaviorAttribute> jest stosowana, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Właściwość jest ustawiona na `true` .  
  
 Limit czasu określa czas od utworzenia transakcji do zakończenia fazy 1 w protokole zatwierdzania dwufazowego.  
  
 Jeśli ten atrybut jest ustawiony w `service` sekcji konfiguracji, należy zastosować co najmniej jedną metodę odpowiedniej usługi przy użyciu <xref:System.ServiceModel.OperationBehaviorAttribute> , w której <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Właściwość jest ustawiona na `true` .  
  
 Należy zauważyć, że wartość limitu czasu jest mniejsza niż wartość tego `transactionTimeout` Ustawienia konfiguracji i każdej <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [Schemat konfiguracji programu WCF](../../configure-apps/file-schema/wcf/index.md)
