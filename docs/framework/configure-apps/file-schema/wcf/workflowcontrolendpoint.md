---
title: '&lt;workflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 9c641d4081d88b059e1d778f6383f85c064af7f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558673"
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="bd0c6-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="bd0c6-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="bd0c6-103">Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchamianie, wstrzymywanie, zakończenia itp).</span><span class="sxs-lookup"><span data-stu-id="bd0c6-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="bd0c6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bd0c6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd0c6-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="bd0c6-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd0c6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd0c6-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd0c6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bd0c6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bd0c6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd0c6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bd0c6-109">Attributes</span></span>  
  
|<span data-ttu-id="bd0c6-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bd0c6-110">Attribute</span></span>|<span data-ttu-id="bd0c6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="bd0c6-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd0c6-112">nazwa</span><span class="sxs-lookup"><span data-stu-id="bd0c6-112">name</span></span>|<span data-ttu-id="bd0c6-113">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="bd0c6-114">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd0c6-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bd0c6-115">Child Elements</span></span>  
 <span data-ttu-id="bd0c6-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd0c6-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bd0c6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bd0c6-118">Element</span><span class="sxs-lookup"><span data-stu-id="bd0c6-118">Element</span></span>|<span data-ttu-id="bd0c6-119">Opis</span><span class="sxs-lookup"><span data-stu-id="bd0c6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd0c6-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="bd0c6-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="bd0c6-121">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd0c6-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd0c6-122">See also</span></span>
- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
