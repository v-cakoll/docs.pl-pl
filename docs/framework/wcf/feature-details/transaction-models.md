---
title: Modele transakcji
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43474229"
---
# <a name="transaction-models"></a><span data-ttu-id="988c6-102">Modele transakcji</span><span class="sxs-lookup"><span data-stu-id="988c6-102">Transaction Models</span></span>
<span data-ttu-id="988c6-103">W tym temacie opisano relację między modele programowania transakcji i składników infrastruktury, zawierane z firmą Microsoft.</span><span class="sxs-lookup"><span data-stu-id="988c6-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="988c6-104">Za pomocą transakcji w Windows Communication Foundation (WCF), jest ważne dowiedzieć się, że są nie wybierzesz różnych modelach transakcyjnych, ale raczej działające w różnych warstwach zintegrowane i spójny model.</span><span class="sxs-lookup"><span data-stu-id="988c6-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="988c6-105">W poniższych sekcjach opisano trzy składniki podstawowe transakcji.</span><span class="sxs-lookup"><span data-stu-id="988c6-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="988c6-106">Windows Communication Foundation transakcji</span><span class="sxs-lookup"><span data-stu-id="988c6-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="988c6-107">Obsługa transakcji w programie WCF umożliwia pisanie transakcyjnych usług.</span><span class="sxs-lookup"><span data-stu-id="988c6-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="988c6-108">Ponadto obsługa protokołu WS-AtomicTransaction (WS-AT), aplikacje może przepływać transakcji usługi sieci Web utworzone przy użyciu usługi WCF i technologia firm.</span><span class="sxs-lookup"><span data-stu-id="988c6-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="988c6-109">Usługa WCF lub aplikacji funkcje transakcji programu WCF zawiera atrybuty i konfiguracja deklaratywne określenie sposobem i czasem infrastruktury należy utworzyć, flow i zsynchronizować transakcji.</span><span class="sxs-lookup"><span data-stu-id="988c6-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="988c6-110">Transakcje System.Transactions</span><span class="sxs-lookup"><span data-stu-id="988c6-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="988c6-111"><xref:System.Transactions> Przestrzeń nazw zawiera zarówno wyraźne programowania model na podstawie <xref:System.Transactions.Transaction> klasy, a także niejawne programowania modelu przy użyciu <xref:System.Transactions.TransactionScope> klasy, w którym infrastruktury automatycznie zarządza transakcji.</span><span class="sxs-lookup"><span data-stu-id="988c6-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="988c6-112">Aby uzyskać więcej informacji na temat sposobu tworzenia transakcyjnych aplikacji za pomocą tych dwóch modeli, zobacz [zapisywanie aplikacji transakcyjnej](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="988c6-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="988c6-113">W aplikacji lub usługi WCF <xref:System.Transactions> zapewnia model programowania do tworzenia transakcji w ramach aplikacji klienta i do jawnie wchodzenie w interakcje z transakcji, gdy jest to wymagane w ramach usługi.</span><span class="sxs-lookup"><span data-stu-id="988c6-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="988c6-114">Usługa MSDTC transakcji</span><span class="sxs-lookup"><span data-stu-id="988c6-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="988c6-115">Koordynator transakcji rozproszonych (MSDTC) firmy Microsoft jest Menedżer transakcji, który zapewnia obsługę transakcji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="988c6-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="988c6-116">Aby uzyskać więcej informacji, zobacz [Podręcznik programisty usługi DTC](https://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="988c6-116">For more information, see the [DTC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="988c6-117">W usłudze WCF lub aplikacji usługi MSDTC udostępnia infrastrukturę koordynacji transakcji utworzone w ramach klienta lub usługę.</span><span class="sxs-lookup"><span data-stu-id="988c6-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
