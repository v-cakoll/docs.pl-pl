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
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="f5ee7-102">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f5ee7-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="f5ee7-103">Windows Communication Foundation (WCF) oferuje trzy atrybuty do konfigurowania transakcji dla usługi: `transactionFlow`, `transactionProtocol`i `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="f5ee7-104">Konfigurowanie transactionFlow</span><span class="sxs-lookup"><span data-stu-id="f5ee7-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="f5ee7-105">Większość wstępnie zdefiniowanych powiązań WCF zawiera atrybuty `transactionFlow` i `transactionProtocol`, dzięki czemu można skonfigurować powiązanie do akceptowania transakcji przychodzących dla określonego punktu końcowego przy użyciu określonego protokołu przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="f5ee7-106">Ponadto można użyć elementu `transactionFlow` i jego atrybutu `transactionProtocol` do utworzenia własnego powiązania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="f5ee7-107">Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [\<powiązywanie >](../../configure-apps/file-schema/wcf/bindings.md) i [Schemat konfiguracji WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5ee7-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="f5ee7-108">Atrybut `transactionFlow` określa, czy przepływ transakcji jest włączony dla punktów końcowych usługi korzystających z tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="f5ee7-109">Konfigurowanie element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="f5ee7-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="f5ee7-110">Atrybut `transactionProtocol` określa protokół transakcji, który ma być używany z punktami końcowymi usługi, które korzystają z tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="f5ee7-111">Poniżej znajduje się przykład sekcji konfiguracji, która służy do konfigurowania określonego powiązania do obsługi przepływu transakcji, a także korzystania z protokołu WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="f5ee7-112">Konfigurowanie transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="f5ee7-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="f5ee7-113">Atrybut `transactionTimeout` dla usługi WCF można skonfigurować w elemencie `behavior` pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="f5ee7-114">Poniższy kod demonstruje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f5ee7-115">Atrybut `transactionTimeout` określa czas, w którym należy zakończyć nową transakcję utworzoną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="f5ee7-116">Jest używany jako <xref:System.Transactions.TransactionScope> limit czasu dla każdej operacji, która ustanawia nową transakcję, a jeśli <xref:System.ServiceModel.OperationBehaviorAttribute> jest stosowany, właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="f5ee7-117">Limit czasu określa czas od utworzenia transakcji do zakończenia fazy 1 w protokole zatwierdzania dwufazowego.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="f5ee7-118">Jeśli ten atrybut jest ustawiony w sekcji konfiguracji `service`, należy zastosować co najmniej jedną metodę odpowiedniej usługi z <xref:System.ServiceModel.OperationBehaviorAttribute>, w której Właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="f5ee7-119">Należy zauważyć, że wartość limitu czasu jest mniejsza niż wartość tego ustawienia konfiguracji `transactionTimeout` i każdej właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5ee7-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ee7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5ee7-120">See also</span></span>

- [<span data-ttu-id="f5ee7-121">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="f5ee7-121">\<binding></span></span>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="f5ee7-122">Schemat konfiguracji programu WCF</span><span class="sxs-lookup"><span data-stu-id="f5ee7-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
