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
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="dfb4c-102">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dfb4c-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="dfb4c-103">Windows Communication Foundation (WCF) udostępnia trzy atrybuty konfigurowania `transactionProtocol`transakcji `transactionTimeout`dla usługi: `transactionFlow`, , i .</span><span class="sxs-lookup"><span data-stu-id="dfb4c-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="dfb4c-104">Konfigurowanie transactionFlow</span><span class="sxs-lookup"><span data-stu-id="dfb4c-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="dfb4c-105">Większość wstępnie zdefiniowanych powiązań WCF zapewnia `transactionFlow` `transactionProtocol` zawierają i atrybuty, dzięki czemu można skonfigurować powiązanie do akceptowania transakcji przychodzących dla określonego punktu końcowego przy użyciu określonego protokołu przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="dfb4c-106">Ponadto można użyć `transactionFlow` elementu i `transactionProtocol` jego atrybut do tworzenia własnych niestandardowych powiązania.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="dfb4c-107">Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [ \<powiązanie>](../../configure-apps/file-schema/wcf/bindings.md) i [schemat konfiguracji WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="dfb4c-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="dfb4c-108">Atrybut `transactionFlow` określa, czy przepływ transakcji jest włączony dla punktów końcowych usługi, które używają powiązania.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="dfb4c-109">Konfigurowanie transakcjiProtocol</span><span class="sxs-lookup"><span data-stu-id="dfb4c-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="dfb4c-110">Atrybut `transactionProtocol` określa protokół transakcji do użycia z punktami końcowymi usługi, które używają powiązania.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="dfb4c-111">Poniżej przedstawiono przykład sekcji konfiguracji, która konfiguruje określone powiązanie do obsługi przepływu transakcji, a także użyj protokołu WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="dfb4c-112">Konfigurowanie limitu czasu transakcji</span><span class="sxs-lookup"><span data-stu-id="dfb4c-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="dfb4c-113">Atrybut usługi WCF można skonfigurować w `transactionTimeout` `behavior` elemencie pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="dfb4c-114">Poniższy kod pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="dfb4c-115">Atrybut `transactionTimeout` określa okres, w którym musi zakończyć się nowa transakcja utworzona w usłudze.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="dfb4c-116">Jest on używany <xref:System.Transactions.TransactionScope> jako limit czasu dla każdej operacji, która <xref:System.ServiceModel.OperationBehaviorAttribute> ustanawia nową <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> transakcję, `true`a jeśli jest stosowana, właściwość jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="dfb4c-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="dfb4c-117">Limit czasu określa czas od utworzenia transakcji do zakończenia fazy 1 w protokole zatwierdzania dwufazowego.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="dfb4c-118">Jeśli ten atrybut jest `service` ustawiony w sekcji konfiguracji, należy zastosować co <xref:System.ServiceModel.OperationBehaviorAttribute>najmniej jedną <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> metodę odpowiedniej `true`usługi z , w którym właściwość jest ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="dfb4c-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="dfb4c-119">Należy zauważyć, że używana wartość przesuwu czasu jest mniejszą wartością między tym `transactionTimeout` ustawieniem konfiguracji a dowolną <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwością.</span><span class="sxs-lookup"><span data-stu-id="dfb4c-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb4c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfb4c-120">See also</span></span>

- [<span data-ttu-id="dfb4c-121">\<wiążące></span><span class="sxs-lookup"><span data-stu-id="dfb4c-121">\<binding></span></span>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="dfb4c-122">Schemat konfiguracji programu WCF</span><span class="sxs-lookup"><span data-stu-id="dfb4c-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
