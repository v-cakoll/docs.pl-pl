---
title: Konfiguracja transakcji modelu ServiceModel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef1d8a9e749c06701aa0a187f81b5b345518c07b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-transaction-configuration"></a>Konfiguracja transakcji modelu ServiceModel
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zawiera trzy atrybuty konfigurowania transakcji usługi: `transactionFlow`, `transactionProtocol`, i `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>Konfigurowanie transactionFlow  
 Większość wstępnie zdefiniowanych powiązań [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia zawierają `transactionFlow` i `transactionProtocol` atrybutów, dzięki czemu można skonfigurować powiązania do akceptowania przychodzących transakcji dla określonego punktu końcowego za pomocą protokołu przepływu transakcji. Ponadto można użyć `transactionFlow` elementu i jego `transactionProtocol` atrybut do tworzenia własnego niestandardowego powiązania. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ustawianie elementów konfiguracji, zobacz [ \<powiązania >](../../../../docs/framework/misc/binding.md) i [schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
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
 Można skonfigurować `transactionTimeout` atrybutu dla Twojego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w `behavior` elementu w pliku konfiguracji. Poniższy kod przedstawia, jak to zrobić.  
  
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
