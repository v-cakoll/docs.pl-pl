---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 2c9774217b835acdb9ebf7374b964d838497fc9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915337"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="749d1-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="749d1-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="749d1-102">Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (tworzenie, uruchamianie, wstrzymywanie, przerywanie itp.).</span><span class="sxs-lookup"><span data-stu-id="749d1-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="749d1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="749d1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="749d1-104">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="749d1-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="749d1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="749d1-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="749d1-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="749d1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="749d1-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="749d1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="749d1-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="749d1-108">Attributes</span></span>  
  
|<span data-ttu-id="749d1-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="749d1-109">Attribute</span></span>|<span data-ttu-id="749d1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="749d1-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="749d1-111">nazwa</span><span class="sxs-lookup"><span data-stu-id="749d1-111">name</span></span>|<span data-ttu-id="749d1-112">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="749d1-112">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="749d1-113">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="749d1-113">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="749d1-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="749d1-114">Child Elements</span></span>  
 <span data-ttu-id="749d1-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="749d1-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="749d1-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="749d1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="749d1-117">Element</span><span class="sxs-lookup"><span data-stu-id="749d1-117">Element</span></span>|<span data-ttu-id="749d1-118">Opis</span><span class="sxs-lookup"><span data-stu-id="749d1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="749d1-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="749d1-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="749d1-120">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="749d1-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="749d1-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="749d1-121">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
