---
title: Konfiguracja transakcji modelu ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: d5bb81c618e3b27df32763948dbe56c9b37995e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188978"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="f4ff4-102">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f4ff4-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="f4ff4-103">Windows Communication Foundation (WCF) zawiera trzy atrybuty dotyczące konfigurowania transakcje dla usługi: `transactionFlow`, `transactionProtocol`, i `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="f4ff4-104">Konfigurowanie transactionFlow</span><span class="sxs-lookup"><span data-stu-id="f4ff4-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="f4ff4-105">Większość wstępnie zdefiniowanych powiązań WCF zapewnia zawierają `transactionFlow` i `transactionProtocol` atrybutów, tak aby można skonfigurować powiązania do akceptowania przychodzących transakcji dla określonego punktu końcowego przy użyciu protokołu przepływu określonej transakcji.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="f4ff4-106">Ponadto można użyć `transactionFlow` elementu i jego `transactionProtocol` atrybutów do tworzenia własnego niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="f4ff4-107">Aby uzyskać więcej informacji na temat ustawiania elementów konfiguracji, zobacz [ \<powiązania >](../../../../docs/framework/misc/binding.md) i [schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4ff4-107">For more information about setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="f4ff4-108">`transactionFlow` Atrybut określa, czy przepływ transakcji jest włączona dla punktów końcowych usługi korzystające z wiązania.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="f4ff4-109">Konfigurowanie element transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="f4ff4-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="f4ff4-110">`transactionProtocol` Atrybut określa protokół transakcji do użycia z punktami końcowymi usługi korzystające z wiązania.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="f4ff4-111">Oto przykład sekcji konfiguracji, które konfiguruje określone powiązanie do obsługi przepływu transakcji, a także korzystanie z protokołu WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="f4ff4-112">Konfigurowanie transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="f4ff4-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="f4ff4-113">Można skonfigurować `transactionTimeout` atrybutu dla usługi WCF w `behavior` element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="f4ff4-114">Poniższy kod pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f4ff4-115">`transactionTimeout` Atrybut określa okres czasu, w którym należy wykonać nową transakcję utworzono usługę.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="f4ff4-116">Jest ona używana jako <xref:System.Transactions.TransactionScope> limit czasu dla każdej operacji, która ustanawia nową transakcję i, jeśli <xref:System.ServiceModel.OperationBehaviorAttribute> zastosowania <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="f4ff4-117">Limit czasu określa czas trwania od czasu utworzenia transakcji do wykonania fazy 1 w dwufazowy protokół zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="f4ff4-118">Jeśli ten atrybut jest ustawiony w ramach `service` sekcji konfiguracji, należy zastosować co najmniej jedną metodę odpowiedniej usługi za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute>, w którym <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="f4ff4-119">Należy pamiętać, że wartość limitu czasu mniejszą wartość między tą `transactionTimeout` ustawień konfiguracji oraz wszelkie <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4ff4-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ff4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4ff4-120">See also</span></span>

- [<span data-ttu-id="f4ff4-121">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f4ff4-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="f4ff4-122">Schemat konfiguracji programu WCF</span><span class="sxs-lookup"><span data-stu-id="f4ff4-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
