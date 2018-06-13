---
title: Modele transakcji
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499027"
---
# <a name="transaction-models"></a><span data-ttu-id="99250-102">Modele transakcji</span><span class="sxs-lookup"><span data-stu-id="99250-102">Transaction Models</span></span>
<span data-ttu-id="99250-103">W tym temacie opisuje relację między modele programowania transakcji i składników infrastruktury udostępniane przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="99250-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="99250-104">Używanie transakcji w systemie Windows Communication Foundation (WCF), jest pamiętać, że nie należy wybierać między różne modele transakcyjnych, ale raczej działające w różnych warstwach zintegrowanego i spójny model.</span><span class="sxs-lookup"><span data-stu-id="99250-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="99250-105">W poniższych sekcjach opisano trzy składniki podstawowe transakcji.</span><span class="sxs-lookup"><span data-stu-id="99250-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="99250-106">Windows Communication Foundation transakcji</span><span class="sxs-lookup"><span data-stu-id="99250-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="99250-107">Obsługa transakcji w programie WCF umożliwia pisanie transakcyjnych usług.</span><span class="sxs-lookup"><span data-stu-id="99250-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="99250-108">Ponadto jego obsługę protokołu WS-AtomicTransaction (WS-AT), aplikacje można przepływu transakcji usługi sieci Web utworzony za pomocą usługi WCF i technologia innych firm.</span><span class="sxs-lookup"><span data-stu-id="99250-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="99250-109">W aplikacji lub usługi WCF funkcje transakcji WCF zapewniają atrybutów i konfiguracja dla deklaratywnie określenie, kiedy infrastruktury należy utworzyć, przepływu i zsynchronizować transakcji.</span><span class="sxs-lookup"><span data-stu-id="99250-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="99250-110">System.Transactions transakcji</span><span class="sxs-lookup"><span data-stu-id="99250-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="99250-111"><xref:System.Transactions> Przestrzeń nazw obejmuje zarówno jawne programowania model na podstawie <xref:System.Transactions.Transaction> klasy, a także niejawne programowania modelu przy użyciu <xref:System.Transactions.TransactionScope> klasy, w którym infrastruktury automatycznie zarządza transakcji.</span><span class="sxs-lookup"><span data-stu-id="99250-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="99250-112">Aby uzyskać więcej informacji o sposobie tworzenia aplikacji transakcyjnej przy użyciu tych dwóch modeli, zobacz [zapisywania transakcyjnych aplikacji](http://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="99250-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="99250-113">W aplikacji lub usługi WCF <xref:System.Transactions> zapewnia model programowania do tworzenia transakcji w aplikacji klienta i do jawnie interakcji z transakcji, gdy jest to wymagane w ramach usługi.</span><span class="sxs-lookup"><span data-stu-id="99250-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="99250-114">Transakcji usługi MSDTC</span><span class="sxs-lookup"><span data-stu-id="99250-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="99250-115">Koordynator transakcji rozproszonych (MSDTC) firmy Microsoft jest Menedżera transakcji, która zapewnia obsługę transakcji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="99250-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="99250-116">Aby uzyskać więcej informacji, zobacz [Podręcznik programisty DTC](http://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="99250-116">For more information, see the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="99250-117">W aplikacji lub usługi WCF usługa MSDTC udostępnia infrastrukturę koordynacji transakcji utworzone w ramach klienta lub usługę.</span><span class="sxs-lookup"><span data-stu-id="99250-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
