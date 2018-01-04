---
title: "Podstawowy cykl życia programowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f5c45cad0b1e4ae1aa6b1963e9acdab47cd9203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="078e1-102">Podstawowy cykl życia programowania</span><span class="sxs-lookup"><span data-stu-id="078e1-102">Basic Programming Lifecycle</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="078e1-103">Umożliwia aplikacjom komunikowanie się, czy znajdują się na tym samym komputerze, przez Internet, lub na platformach inną aplikację.</span><span class="sxs-lookup"><span data-stu-id="078e1-103"> enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="078e1-104">W tym temacie omówiono zadania, które są wymagane do utworzenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="078e1-104">This topic outlines the tasks that are required to build a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="078e1-105">Przykładową aplikację pracy, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="078e1-105">For a working sample application, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="078e1-106">Podstawowe zadania</span><span class="sxs-lookup"><span data-stu-id="078e1-106">The Basic Tasks</span></span>  
 <span data-ttu-id="078e1-107">Podstawowe zadania do wykonania znajdują się w kolejności:</span><span class="sxs-lookup"><span data-stu-id="078e1-107">The basic tasks to perform are, in order:</span></span>  
  
1.  <span data-ttu-id="078e1-108">Definiowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="078e1-108">Define the service contract.</span></span> <span data-ttu-id="078e1-109">Kontrakt usługi Określa podpis usługi, danych, który wymienia i innych podstawie umowy wymaganych danych.</span><span class="sxs-lookup"><span data-stu-id="078e1-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="078e1-110">[Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="078e1-110"> [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="078e1-111">Implementuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="078e1-111">Implement the contract.</span></span> <span data-ttu-id="078e1-112">Aby zaimplementować kontrakt usługi, Utwórz klasę, która implementuje kontrakt i określ niestandardowe zachowania, które powinny mieć środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="078e1-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="078e1-113">[Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="078e1-113"> [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
3.  <span data-ttu-id="078e1-114">Skonfiguruj usługę, określając punktów końcowych i innych informacji o zachowanie.</span><span class="sxs-lookup"><span data-stu-id="078e1-114">Configure the service by specifying endpoints and other behavior information.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="078e1-115">[Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="078e1-115"> [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
4.  <span data-ttu-id="078e1-116">Host usługi.</span><span class="sxs-lookup"><span data-stu-id="078e1-116">Host the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="078e1-117">[Usług hostingu](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="078e1-117"> [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
5.  <span data-ttu-id="078e1-118">Tworzenie aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="078e1-118">Build a client application.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="078e1-119">[Tworzenia klientów](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="078e1-119"> [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
 <span data-ttu-id="078e1-120">Chociaż w tematach w tej sekcji należy wykonać to zamówienie, niektóre scenariusze nie są uruchamiane na początku.</span><span class="sxs-lookup"><span data-stu-id="078e1-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="078e1-121">Na przykład jeśli chcesz skompilować klienta istniejące usługi, możesz uruchomić w kroku 5.</span><span class="sxs-lookup"><span data-stu-id="078e1-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="078e1-122">Lub jeśli tworzysz usługi, który będzie używany przez inne osoby, możesz pominąć krok 5.</span><span class="sxs-lookup"><span data-stu-id="078e1-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="078e1-123">Po zapoznaniu się z projektowanie kontraktów usług, możesz przeczytać [wprowadzenie do rozszerzalności](../../../docs/framework/wcf/introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="078e1-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md).</span></span> <span data-ttu-id="078e1-124">Jeśli masz problemy z usługą, sprawdź [szybkiego startu WCF Rozwiązywanie problemów z](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) aby zobaczyć, czy inne osoby mają takie same lub podobne problemy.</span><span class="sxs-lookup"><span data-stu-id="078e1-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078e1-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="078e1-125">See Also</span></span>  
 [<span data-ttu-id="078e1-126">Implementowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="078e1-126">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
