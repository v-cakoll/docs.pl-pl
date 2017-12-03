---
title: "Powiązania WCF (Windows Communication Foundation)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bindings [WCF]
ms.assetid: 845df323-be53-4848-92ef-ba67a406484d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36924bdc79a9789a991befb53c0025b7ea1fd601
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="c7b9e-102">Powiązania WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="c7b9e-102">Windows Communication Foundation Bindings</span></span>
<span data-ttu-id="c7b9e-103">Określ powiązania jak [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] punktu końcowego usługi komunikuje się z innych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-103">Bindings specify how a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service endpoint communicates with other endpoints.</span></span> <span data-ttu-id="c7b9e-104">W jego najbardziej podstawową powiązanie należy określić transportu (na przykład HTTP lub TCP) do użycia.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-104">At its most basic, a binding must specify the transport (for example, HTTP or TCP) to use.</span></span> <span data-ttu-id="c7b9e-105">Można również ustawić inne właściwości, takie jak zabezpieczenia i transakcji obsługuje za pośrednictwem powiązania.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-105">You can also set other characteristics, such as security and transaction support, through bindings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7b9e-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c7b9e-106">In This Section</span></span>  
 [<span data-ttu-id="c7b9e-107">Omówienie powiązań WCF</span><span class="sxs-lookup"><span data-stu-id="c7b9e-107">WCF Bindings Overview</span></span>](../../../docs/framework/wcf/bindings-overview.md)  
 <span data-ttu-id="c7b9e-108">Omówienie co [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] wiązania należy powiązań, jakie zapewnia system i jak można zdefiniować lub modyfikować.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-108">Overview of what [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bindings do, what bindings the system provides, and how you can define or modify them.</span></span>  
  
 [<span data-ttu-id="c7b9e-109">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="c7b9e-109">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 <span data-ttu-id="c7b9e-110">Lista powiązań dołączonego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7b9e-110">A list of bindings included with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="c7b9e-111">Te powiązania obejmuje większość zabezpieczeń i wymagania dotyczące wzorca wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-111">These bindings cover the majority of security and message pattern requirements.</span></span>  
  
 [<span data-ttu-id="c7b9e-112">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c7b9e-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="c7b9e-113">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] powiązanie zawiera ważne informacje, które klienci muszą używać nawiązać połączenia z punktami końcowymi usług.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-113">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] binding contains important information that clients must use to connect to service endpoints.</span></span>  
  
 [<span data-ttu-id="c7b9e-114">Konfigurowanie powiązań dla usług</span><span class="sxs-lookup"><span data-stu-id="c7b9e-114">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 <span data-ttu-id="c7b9e-115">Konfiguracja pozwala Administratorzy i instalatorów dostosować powiązań dla punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="c7b9e-115">Configuration enables administrators and installers to customize the bindings for service endpoints.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c7b9e-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c7b9e-116">Reference</span></span>  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="c7b9e-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c7b9e-117">Related Sections</span></span>  
 [<span data-ttu-id="c7b9e-118">Punkty końcowe: Adresy powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="c7b9e-118">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 [<span data-ttu-id="c7b9e-119">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c7b9e-119">Bindings</span></span>](../../../docs/framework/wcf/feature-details/bindings.md)  
  
## <a name="see-also"></a><span data-ttu-id="c7b9e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7b9e-120">See Also</span></span>  
 [<span data-ttu-id="c7b9e-121">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c7b9e-121">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
