---
title: '&lt;workflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 178ccc8ac35b0ac76d74c818dce43dcffc5c0835
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144954"
---
# <a name="ltworkflowcontrolendpointgt"></a><span data-ttu-id="abebf-102">&lt;workflowControlEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="abebf-102">&lt;workflowControlEndpoint&gt;</span></span>
<span data-ttu-id="abebf-103">Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchamianie, wstrzymywanie, zakończenia itp).</span><span class="sxs-lookup"><span data-stu-id="abebf-103">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="abebf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="abebf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="abebf-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="abebf-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abebf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="abebf-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abebf-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="abebf-107">Attributes and Elements</span></span>  
 <span data-ttu-id="abebf-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="abebf-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abebf-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="abebf-109">Attributes</span></span>  
  
|<span data-ttu-id="abebf-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="abebf-110">Attribute</span></span>|<span data-ttu-id="abebf-111">Opis</span><span class="sxs-lookup"><span data-stu-id="abebf-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abebf-112">nazwa</span><span class="sxs-lookup"><span data-stu-id="abebf-112">name</span></span>|<span data-ttu-id="abebf-113">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="abebf-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="abebf-114">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="abebf-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abebf-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="abebf-115">Child Elements</span></span>  
 <span data-ttu-id="abebf-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="abebf-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abebf-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="abebf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="abebf-118">Element</span><span class="sxs-lookup"><span data-stu-id="abebf-118">Element</span></span>|<span data-ttu-id="abebf-119">Opis</span><span class="sxs-lookup"><span data-stu-id="abebf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abebf-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="abebf-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="abebf-121">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="abebf-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abebf-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abebf-122">See Also</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
