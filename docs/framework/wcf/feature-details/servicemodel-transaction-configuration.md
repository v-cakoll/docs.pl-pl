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
ms.workload: dotnet
ms.openlocfilehash: 650f34c37917a7f7ce407df1a3af42d177593c33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="ef111-102">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ef111-102">ServiceModel Transaction Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ef111-103">zawiera trzy atrybuty konfigurowania transakcji usługi: `transactionFlow`, `transactionProtocol`, i `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="ef111-103"> provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="ef111-104">Konfigurowanie transactionFlow</span><span class="sxs-lookup"><span data-stu-id="ef111-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="ef111-105">Większość wstępnie zdefiniowanych powiązań [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia zawierają `transactionFlow` i `transactionProtocol` atrybutów, dzięki czemu można skonfigurować powiązania do akceptowania przychodzących transakcji dla określonego punktu końcowego za pomocą protokołu przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="ef111-105">Most of the predefined bindings [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="ef111-106">Ponadto można użyć `transactionFlow` elementu i jego `transactionProtocol` atrybut do tworzenia własnego niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ef111-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ef111-107">Ustawianie elementów konfiguracji, zobacz [ \<powiązania >](../../../../docs/framework/misc/binding.md) i [schemat konfiguracji programu WCF](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef111-107"> setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="ef111-108">`transactionFlow` Atrybut określa, czy przepływ transakcji jest włączona dla punktów końcowych usługi, które używają powiązania.</span><span class="sxs-lookup"><span data-stu-id="ef111-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="ef111-109">Konfigurowanie element transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="ef111-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="ef111-110">`transactionProtocol` Atrybut określa protokół transakcji do użycia z punktów końcowych usługi, które używają powiązania.</span><span class="sxs-lookup"><span data-stu-id="ef111-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="ef111-111">Oto przykład sekcji konfiguracji, który konfiguruje określone powiązanie do obsługi przepływu transakcji, jak również użycie protokołu WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="ef111-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="ef111-112">Konfigurowanie transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="ef111-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="ef111-113">Można skonfigurować `transactionTimeout` atrybutu dla Twojego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] w `behavior` elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ef111-113">You can configure the `transactionTimeout` attribute for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="ef111-114">Poniższy kod przedstawia, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="ef111-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ef111-115">`transactionTimeout` Atrybut określa okres czasu, w którym należy wykonać nową transakcję utworzono usługę.</span><span class="sxs-lookup"><span data-stu-id="ef111-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="ef111-116">Jest on używany jako <xref:System.Transactions.TransactionScope> limit czasu dla żadnej operacji, który określa nowej transakcji, i w razie <xref:System.ServiceModel.OperationBehaviorAttribute> zostanie zastosowana, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="ef111-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="ef111-117">Limit czasu określa czas od czasu utworzenia transakcji do wykonania fazy 1 w dwufazowego protokołu wykonania.</span><span class="sxs-lookup"><span data-stu-id="ef111-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="ef111-118">Jeśli ten atrybut zostanie ustawiony w ramach `service` sekcji konfiguracji, należy zastosować w przypadku co najmniej jedną metodę odpowiedniej usługi z <xref:System.ServiceModel.OperationBehaviorAttribute>, w którym <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> właściwość jest ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="ef111-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="ef111-119">Należy pamiętać, że wartość limitu czasu mniejszą wartość między tą `transactionTimeout` ustawienia konfiguracji i wszystkie <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef111-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef111-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef111-120">See Also</span></span>  
 [<span data-ttu-id="ef111-121">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ef111-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="ef111-122">Schemat konfiguracji programu WCF</span><span class="sxs-lookup"><span data-stu-id="ef111-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
