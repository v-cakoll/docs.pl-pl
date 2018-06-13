---
title: Konfiguracja transakcji modelu ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 2c724e3f67bbf6554abffb44f101d2f28f748023
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498348"
---
# <a name="servicemodel-transaction-configuration"></a>Konfiguracja transakcji modelu ServiceModel
Windows Communication Foundation (WCF) zawiera trzy atrybuty dotyczące konfigurowania transakcji usługi: `transactionFlow`, `transactionProtocol`, i `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Konfigurowanie transactionFlow  
 Większość wstępnie zdefiniowanych powiązań WCF zapewnia zawierają `transactionFlow` i `transactionProtocol` atrybutów, dzięki czemu można skonfigurować powiązania do akceptowania przychodzących transakcji dla określonego punktu końcowego za pomocą protokołu przepływu transakcji. Ponadto można użyć `transactionFlow` elementu i jego `transactionProtocol` atrybut do tworzenia własnego niestandardowego powiązania. Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [ \<powiązania >](../../../../docs/framework/misc/binding.md) i [schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow` Atrybut określa, czy przepływ transakcji jest włączona dla punktów końcowych usługi, które używają powiązania.  
  
## <a name="configuring-transactionprotocol"></a>Konfigurowanie element transactionProtocol  
 `transactionProtocol` Atrybut określa protokół transakcji do użycia z punktów końcowych usługi, które używają powiązania.  
  
 Oto przykład sekcji konfiguracji, który konfiguruje określone powiązanie do obsługi przepływu transakcji, jak również użycie protokołu WS-AtomicTransaction.  
  
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
 Można skonfigurować `transactionTimeout` atrybutu dla usługi WCF w `behavior` elementu w pliku konfiguracji. Poniższy kod przedstawia, jak to zrobić.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` Atrybut określa okres czasu, w którym należy wykonać nową transakcję utworzono usługę. Jest on używany jako <xref:System.Transactions.TransactionScope> limit czasu dla żadnej operacji, który określa nowej transakcji, i w razie <xref:System.ServiceModel.OperationBehaviorAttribute> zostanie zastosowana, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwość jest ustawiona na `true`.  
  
 Limit czasu określa czas od czasu utworzenia transakcji do wykonania fazy 1 w dwufazowego protokołu wykonania.  
  
 Jeśli ten atrybut zostanie ustawiony w ramach `service` sekcji konfiguracji, należy zastosować w przypadku co najmniej jedną metodę odpowiedniej usługi z <xref:System.ServiceModel.OperationBehaviorAttribute>, w którym <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwość jest ustawiona na `true`.  
  
 Należy pamiętać, że wartość limitu czasu mniejszą wartość między tą `transactionTimeout` ustawienia konfiguracji i wszystkie <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [\<Powiązanie >](../../../../docs/framework/misc/binding.md)  
 [Schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
