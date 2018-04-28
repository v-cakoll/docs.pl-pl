---
title: Używanie elementu WS-AtomicTransaction
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d437b0bf3b14b60899028e293feecf5b1e36f766
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="using-ws-atomictransaction"></a><span data-ttu-id="90749-102">Używanie elementu WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="90749-102">Using WS-AtomicTransaction</span></span>
<span data-ttu-id="90749-103">WS-AtomicTransaction (WS-AT) to protokół interoperacyjne transakcji.</span><span class="sxs-lookup"><span data-stu-id="90749-103">WS-AtomicTransaction (WS-AT) is an interoperable transaction protocol.</span></span> <span data-ttu-id="90749-104">Umożliwia ona przepływu transakcji rozproszonych za pomocą komunikatów usługi sieci Web oraz koordynować w sposób współpraca między infrastruktury heterogenicznych transakcji.</span><span class="sxs-lookup"><span data-stu-id="90749-104">It enables you to flow distributed transactions by using Web service messages, and coordinate in an interoperable manner between heterogeneous transaction infrastructures.</span></span> <span data-ttu-id="90749-105">WS-AT Protokół dwufazowego dysków wyników częściowych między aplikacji rozproszonych, menedżerów transakcji i menedżerów zasobów.</span><span class="sxs-lookup"><span data-stu-id="90749-105">WS-AT uses the two-phase commit protocol to drive an atomic outcome between distributed applications, transaction managers, and resource managers.</span></span>  
  
 <span data-ttu-id="90749-106">Implementacja protokołu WS-AT [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zapewnia obejmują usługę protokołu wbudowane w Menedżera transakcji koordynatora transakcji rozproszonych (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="90749-106">The WS-AT implementation [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides includes a protocol service built into the Microsoft Distributed Transaction Coordinator (MSDTC) transaction manager.</span></span> <span data-ttu-id="90749-107">Za pomocą usługi WS-AT [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji przepływ transakcji do innych aplikacji, takich jak współdziałanie usługi sieci Web utworzony za pomocą innych technologii.</span><span class="sxs-lookup"><span data-stu-id="90749-107">Using WS-AT, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can flow transactions to other applications, including interoperable Web services built using third-party technology.</span></span>  
  
 <span data-ttu-id="90749-108">Podczas przepływu transakcji od aplikacji klienckiej i aplikacji serwera, protokół transakcji używany jest określana przez powiązanie, czy serwer udostępnia w punkcie końcowym klienta wybrana.</span><span class="sxs-lookup"><span data-stu-id="90749-108">When flowing a transaction between a client application and a server application, the transaction protocol used is determined by the binding that the server exposes on the endpoint the client selected.</span></span> <span data-ttu-id="90749-109">Niektóre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] domyślne powiązania dostarczane przez system do określania `OleTransactions` protokołu formacie propagacji transakcji, podczas gdy inne domyślne do określania WS-AT.</span><span class="sxs-lookup"><span data-stu-id="90749-109">Some [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided bindings default to specifying the `OleTransactions` protocol as the transaction propagation format, while others default to specifying WS-AT.</span></span> <span data-ttu-id="90749-110">Wybór protokół transakcji wewnątrz podane powiązanie również programowo można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="90749-110">You can also programmatically modify the choice of transaction protocol inside a given binding.</span></span>  
  
 <span data-ttu-id="90749-111">Wybór protokołu wpływ:</span><span class="sxs-lookup"><span data-stu-id="90749-111">The choice of protocol influences:</span></span>  
  
-   <span data-ttu-id="90749-112">Format nagłówki komunikatów używane w celu przekazania transakcji od klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="90749-112">The format of the message headers used to flow the transaction from client to server.</span></span>  
  
-   <span data-ttu-id="90749-113">Protokół używany do uruchomienia dwufazowego protokołu wykonania Menedżera transakcji klienta i serwera transakcji, aby rozwiązać wyniku transakcji.</span><span class="sxs-lookup"><span data-stu-id="90749-113">The network protocol used to run the two-phase commit protocol between the client's transaction manager and the server's transaction, in order to resolve the outcome of the transaction.</span></span>  
  
 <span data-ttu-id="90749-114">Jeśli serwera i klienta są napisane przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], nie trzeba używać protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="90749-114">If the server and client are written using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you do not need to use WS-AT.</span></span> <span data-ttu-id="90749-115">Zamiast tego można użyć ustawień domyślnych `NetTcpBinding` z `TransactionFlow` włączone, atrybut, który będzie używany `OleTransactions` zamiast tego protokołu.</span><span class="sxs-lookup"><span data-stu-id="90749-115">Instead, you can use the default settings of `NetTcpBinding` with the `TransactionFlow` attribute enabled, which will use the `OleTransactions` protocol instead.</span></span> <span data-ttu-id="90749-116">Aby uzyskać więcej informacji, zobacz [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="90749-116">For more information, see [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span> <span data-ttu-id="90749-117">W przeciwnym razie są przepływy transakcji do usług sieci Web oparty na technologii innych firm, należy użyć protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="90749-117">Otherwise, if you are flowing transactions to Web services built on third-party technologies, you must use WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90749-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90749-118">See Also</span></span>  
 [<span data-ttu-id="90749-119">Konfigurowanie obsługi protokołu WS-Atomic Transaction</span><span class="sxs-lookup"><span data-stu-id="90749-119">Configuring WS-Atomic Transaction Support</span></span>](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
