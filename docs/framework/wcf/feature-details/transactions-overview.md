---
title: "Omówienie transakcji WCF (Windows Communication Foundation)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2be5e7622c51da37c0f39c12258f50b74483fa53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="2f9b6-102">Omówienie transakcji WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="2f9b6-102">Windows Communication Foundation Transactions Overview</span></span>
<span data-ttu-id="2f9b6-103">Transakcje umożliwiają do grupowania zestawu działań lub operacji w pojedynczą jednostkę niepodzielnych wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="2f9b6-104">Transakcja jest to kolekcja operacji z następującymi właściwościami:</span><span class="sxs-lookup"><span data-stu-id="2f9b6-104">A transaction is a collection of operations with the following properties:</span></span>  
  
-   <span data-ttu-id="2f9b6-105">Niepodzielność.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-105">Atomicity.</span></span> <span data-ttu-id="2f9b6-106">Dzięki temu, że wszystkie aktualizacje ukończone na podstawie określonej transakcji są zatwierdzone i zapewniana trwałość lub są one wszystkich zostało przerwane i z powrotem obniżyć do poprzedniego stanu.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
-   <span data-ttu-id="2f9b6-107">Spójność.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-107">Consistency.</span></span> <span data-ttu-id="2f9b6-108">Gwarantuje to, że zmiany wprowadzone w ramach transakcji reprezentują transformację z jednego spójnego stanu do innego.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="2f9b6-109">Na przykład przeniesienia pieniędzy z konta bankowego konta oszczędności transakcji nie zmienia kwotę w ogólnej konta bankowego.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
-   <span data-ttu-id="2f9b6-110">Izolacja.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-110">Isolation.</span></span> <span data-ttu-id="2f9b6-111">Zapobiega to transakcji z obserwowania niezatwierdzone zmiany należących do innych równoczesnych transakcji.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="2f9b6-112">Izolacja udostępnia abstrakcję współbieżności przy jednoczesnym zapewnieniu jednej transakcji nie mogą mieć nieoczekiwane wpływ na wykonywanie innej transakcji.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
-   <span data-ttu-id="2f9b6-113">Trwałość.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-113">Durability.</span></span> <span data-ttu-id="2f9b6-114">Oznacza to, że po zatwierdzone, aktualizacje zarządzanych zasobów (takich jak rekordu bazy danych) będą trwałe w wypadku awarii.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="2f9b6-115">zawiera bogaty zestaw funkcji, które umożliwiają tworzenie transakcji rozproszonych w aplikacji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-115"> provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2f9b6-116">zapewnia obsługę protokołu WS-AtomicTransaction (WS-AT), która umożliwia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji przepływ transakcji na współdziałanie aplikacji, takich jak współdziałanie usług sieci Web utworzony za pomocą innych technologii.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-116"> implements support for the WS-AtomicTransaction (WS-AT) protocol that enables [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2f9b6-117">implementuje również obsługę protokołu transakcji OLE, którego można użyć w scenariuszach, w którym nie ma potrzeby międzyoperacyjnego funkcji umożliwiających przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-117"> also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="2f9b6-118">Plik konfiguracji aplikacji służy do konfigurowania wiązania, aby włączyć lub wyłączyć przepływu transakcji, a także ustawić protokół transakcji odpowiednią dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="2f9b6-119">Ponadto można ustawić limity czasu transakcji na poziomie usługi przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2f9b6-120">[Włączanie przepływu transakcji](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="2f9b6-120"> [Enabling Transaction Flow](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="2f9b6-121">Atrybuty transakcji w <xref:System.ServiceModel> przestrzeni nazw można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2f9b6-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
-   <span data-ttu-id="2f9b6-122">Konfigurowanie limitów czasu transakcji i poziom izolacji filtrowanie przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="2f9b6-123">Włącz funkcje transakcji i skonfigurować za pomocą zachowania ukończenia transakcji <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="2f9b6-124">Użyj <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybutów w metodzie kontraktu, aby wymagać, akceptować lub odrzucać przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="2f9b6-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="2f9b6-125">[Atrybuty transakcji elementu ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="2f9b6-125"> [ServiceModel Transaction Attributes](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9b6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f9b6-126">See Also</span></span>  
 [<span data-ttu-id="2f9b6-127">Atrybuty transakcji elementu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2f9b6-127">ServiceModel Transaction Attributes</span></span>](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [<span data-ttu-id="2f9b6-128">Włączanie przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="2f9b6-128">Enabling Transaction Flow</span></span>](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
