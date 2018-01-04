---
title: '&lt;obiektu workflowControlEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 443d23a3b0f73d2fd0a08112d51f745d1e1874fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="89ea0-102">&lt;obiektu workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="89ea0-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="89ea0-103">Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchom, zawieszenie, przerwanie, itp).</span><span class="sxs-lookup"><span data-stu-id="89ea0-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="89ea0-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="89ea0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="89ea0-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="89ea0-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ea0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="89ea0-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89ea0-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="89ea0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="89ea0-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="89ea0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89ea0-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="89ea0-109">Attributes</span></span>  
  
|<span data-ttu-id="89ea0-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="89ea0-110">Attribute</span></span>|<span data-ttu-id="89ea0-111">Opis</span><span class="sxs-lookup"><span data-stu-id="89ea0-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89ea0-112">nazwa</span><span class="sxs-lookup"><span data-stu-id="89ea0-112">name</span></span>|<span data-ttu-id="89ea0-113">Ciąg określający nazwę Konfiguracja standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="89ea0-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="89ea0-114">Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="89ea0-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89ea0-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="89ea0-115">Child Elements</span></span>  
 <span data-ttu-id="89ea0-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="89ea0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89ea0-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="89ea0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="89ea0-118">Element</span><span class="sxs-lookup"><span data-stu-id="89ea0-118">Element</span></span>|<span data-ttu-id="89ea0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="89ea0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89ea0-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="89ea0-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="89ea0-121">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="89ea0-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89ea0-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89ea0-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
