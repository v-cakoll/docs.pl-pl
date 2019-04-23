---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: a9c16d1036a8177120cd152d4ac211ad084d588e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150387"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="5caf7-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="5caf7-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="5caf7-102">Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchamianie, wstrzymywanie, zakończenia itp).</span><span class="sxs-lookup"><span data-stu-id="5caf7-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="5caf7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5caf7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5caf7-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5caf7-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5caf7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5caf7-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5caf7-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5caf7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5caf7-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5caf7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5caf7-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5caf7-108">Attributes</span></span>  
  
|<span data-ttu-id="5caf7-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5caf7-109">Attribute</span></span>|<span data-ttu-id="5caf7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5caf7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5caf7-111">nazwa</span><span class="sxs-lookup"><span data-stu-id="5caf7-111">name</span></span>|<span data-ttu-id="5caf7-112">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="5caf7-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5caf7-113">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5caf7-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5caf7-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5caf7-114">Child Elements</span></span>  
 <span data-ttu-id="5caf7-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="5caf7-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5caf7-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5caf7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5caf7-117">Element</span><span class="sxs-lookup"><span data-stu-id="5caf7-117">Element</span></span>|<span data-ttu-id="5caf7-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5caf7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5caf7-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5caf7-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5caf7-120">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="5caf7-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5caf7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5caf7-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
