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
ms.openlocfilehash: 741968e160683ab38f79effdfa0bdf56053cfb93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="c6f8c-102">&lt;obiektu workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="c6f8c-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="c6f8c-103">Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchom, zawieszenie, przerwanie, itp).</span><span class="sxs-lookup"><span data-stu-id="c6f8c-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="c6f8c-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c6f8c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c6f8c-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c6f8c-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6f8c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6f8c-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6f8c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c6f8c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c6f8c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c6f8c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6f8c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c6f8c-109">Attributes</span></span>  
  
|<span data-ttu-id="c6f8c-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c6f8c-110">Attribute</span></span>|<span data-ttu-id="c6f8c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c6f8c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6f8c-112">nazwa</span><span class="sxs-lookup"><span data-stu-id="c6f8c-112">name</span></span>|<span data-ttu-id="c6f8c-113">Ciąg określający nazwę Konfiguracja standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c6f8c-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="c6f8c-114">Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c6f8c-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6f8c-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c6f8c-115">Child Elements</span></span>  
 <span data-ttu-id="c6f8c-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="c6f8c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6f8c-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c6f8c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c6f8c-118">Element</span><span class="sxs-lookup"><span data-stu-id="c6f8c-118">Element</span></span>|<span data-ttu-id="c6f8c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c6f8c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6f8c-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c6f8c-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="c6f8c-121">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="c6f8c-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6f8c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6f8c-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
