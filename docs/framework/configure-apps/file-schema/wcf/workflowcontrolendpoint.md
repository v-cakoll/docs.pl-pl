---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: de0a51ed6f2a878ab3a6ebe15863f1f2925034ce
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272602"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="5c1e9-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="5c1e9-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="5c1e9-102">Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchamianie, wstrzymywanie, zakończenia itp).</span><span class="sxs-lookup"><span data-stu-id="5c1e9-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="5c1e9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5c1e9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5c1e9-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5c1e9-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c1e9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c1e9-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c1e9-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5c1e9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5c1e9-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5c1e9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c1e9-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5c1e9-108">Attributes</span></span>  
  
|<span data-ttu-id="5c1e9-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5c1e9-109">Attribute</span></span>|<span data-ttu-id="5c1e9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="5c1e9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c1e9-111">nazwa</span><span class="sxs-lookup"><span data-stu-id="5c1e9-111">name</span></span>|<span data-ttu-id="5c1e9-112">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="5c1e9-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5c1e9-113">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5c1e9-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c1e9-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5c1e9-114">Child Elements</span></span>  
 <span data-ttu-id="5c1e9-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="5c1e9-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c1e9-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5c1e9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5c1e9-117">Element</span><span class="sxs-lookup"><span data-stu-id="5c1e9-117">Element</span></span>|<span data-ttu-id="5c1e9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5c1e9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c1e9-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="5c1e9-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5c1e9-120">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="5c1e9-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c1e9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c1e9-121">See also</span></span>
- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
