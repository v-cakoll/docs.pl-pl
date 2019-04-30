---
title: Konfiguracja transakcji modelu ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: d5bb81c618e3b27df32763948dbe56c9b37995e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747709"
---
# <a name="servicemodel-transaction-configuration"></a>Konfiguracja transakcji modelu ServiceModel
Windows Communication Foundation (WCF) zawiera trzy atrybuty dotyczące konfigurowania transakcje dla usługi: `transactionFlow`, `transactionProtocol`, i `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Konfigurowanie transactionFlow  
 Większość wstępnie zdefiniowanych powiązań WCF zapewnia zawierają `transactionFlow` i `transactionProtocol` atrybutów, tak aby można skonfigurować powiązania do akceptowania przychodzących transakcji dla określonego punktu końcowego przy użyciu protokołu przepływu określonej transakcji. Ponadto można użyć `transactionFlow` elementu i jego `transactionProtocol` atrybutów do tworzenia własnego niestandardowego powiązania. Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [ \<powiązania >](../../../../docs/framework/misc/binding.md) i [schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow` Atrybut określa, czy przepływ transakcji jest włączona dla punktów końcowych usługi korzystające z wiązania.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurowanie element transactionProtocol  
 `transactionProtocol` Atrybut określa protokół transakcji do użycia z punktami końcowymi usługi korzystające z wiązania.  
  
 Oto przykład sekcji konfiguracji, które konfiguruje określone powiązanie do obsługi przepływu transakcji, a także korzystanie z protokołu WS-AtomicTransaction.  
  
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
 Można skonfigurować `transactionTimeout` atrybutu dla usługi WCF w `behavior` element pliku konfiguracji. Poniższy kod pokazuje, jak to zrobić.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` Atrybut określa okres czasu, w którym należy wykonać nową transakcję utworzono usługę. Jest ona używana jako <xref:System.Transactions.TransactionScope> limit czasu dla każdej operacji, która ustanawia nową transakcję i, jeśli <xref:System.ServiceModel.OperationBehaviorAttribute> zastosowania <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwość jest ustawiona na `true`.  
  
 Limit czasu określa czas trwania od czasu utworzenia transakcji do wykonania fazy 1 w dwufazowy protokół zatwierdzania.  
  
 Jeśli ten atrybut jest ustawiony w ramach `service` sekcji konfiguracji, należy zastosować co najmniej jedną metodę odpowiedniej usługi za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute>, w którym <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwość jest ustawiona na `true`.  
  
 Należy pamiętać, że wartość limitu czasu mniejszą wartość między tą `transactionTimeout` ustawień konfiguracji oraz wszelkie <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [\<Powiązanie >](../../../../docs/framework/misc/binding.md)
- [Schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
