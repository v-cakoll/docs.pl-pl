---
title: Modele transakcji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c68a23e9ee86050a9db4c63c8c97d017794bce8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="transaction-models"></a><span data-ttu-id="9f4d4-102">Modele transakcji</span><span class="sxs-lookup"><span data-stu-id="9f4d4-102">Transaction Models</span></span>
<span data-ttu-id="9f4d4-103">W tym temacie opisuje relację między modele programowania transakcji i składników infrastruktury udostępniane przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="9f4d4-104">Podczas korzystania z transakcji w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], ważne jest, aby zrozumieć, że nie należy wybierać między różne modele transakcyjnych, ale raczej działające w różnych warstwach zintegrowanego i spójny model.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-104">When using transactions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="9f4d4-105">W poniższych sekcjach opisano trzy składniki podstawowe transakcji.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="9f4d4-106">Windows Communication Foundation transakcji</span><span class="sxs-lookup"><span data-stu-id="9f4d4-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="9f4d4-107">Obsługa transakcji w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umożliwia pisanie transakcyjnych usług.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-107">The transaction support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows you write transactional services.</span></span> <span data-ttu-id="9f4d4-108">Ponadto z jego obsługę protokołu WS-AtomicTransaction (WS-AT), aplikacje można przepływu transakcji usługi sieci Web utworzony za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lub innych technologii.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or third-party technology.</span></span>  
  
 <span data-ttu-id="9f4d4-109">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługę lub aplikację, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje transakcji zapewniają atrybutów i konfiguracja dla deklaratywnie określenie, kiedy infrastruktury należy utworzyć, przepływu i zsynchronizować transakcji.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-109">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="9f4d4-110">System.Transactions transakcji</span><span class="sxs-lookup"><span data-stu-id="9f4d4-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="9f4d4-111"><xref:System.Transactions> Przestrzeń nazw obejmuje zarówno jawne programowania model na podstawie <xref:System.Transactions.Transaction> klasy, a także niejawne programowania modelu przy użyciu <xref:System.Transactions.TransactionScope> klasy, w którym infrastruktury automatycznie zarządza transakcji.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="9f4d4-112">Aby uzyskać więcej informacji o sposobie tworzenia aplikacji transakcyjnej przy użyciu tych dwóch modeli, zobacz [zapisywania transakcyjnych aplikacji](http://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="9f4d4-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="9f4d4-113">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługę lub aplikację, <xref:System.Transactions> zapewnia model programowania do tworzenia transakcji w aplikacji klienta i do jawnie interakcji z transakcji, gdy jest to wymagane w ramach usługi.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-113">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="9f4d4-114">Transakcji usługi MSDTC</span><span class="sxs-lookup"><span data-stu-id="9f4d4-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="9f4d4-115">Koordynator transakcji rozproszonych (MSDTC) firmy Microsoft jest Menedżera transakcji, która zapewnia obsługę transakcji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="9f4d4-116">Aby uzyskać więcej informacji, zobacz [Podręcznik programisty DTC](http://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="9f4d4-116">For more information, see the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="9f4d4-117">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi lub aplikacji, usługi MSDTC zapewnia infrastrukturę do koordynacji transakcji utworzone w ramach klienta lub usługę.</span><span class="sxs-lookup"><span data-stu-id="9f4d4-117">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
