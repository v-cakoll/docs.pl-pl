---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854784"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="5bff6-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="5bff6-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="5bff6-102">Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (tworzenie, uruchamianie, wstrzymywanie, przerywanie itp.).</span><span class="sxs-lookup"><span data-stu-id="5bff6-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="5bff6-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5bff6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5bff6-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5bff6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5bff6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="5bff6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="5bff6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowControlEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="5bff6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bff6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bff6-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bff6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5bff6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5bff6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5bff6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bff6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5bff6-110">Attributes</span></span>  
  
|<span data-ttu-id="5bff6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5bff6-111">Attribute</span></span>|<span data-ttu-id="5bff6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5bff6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bff6-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="5bff6-113">name</span></span>|<span data-ttu-id="5bff6-114">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5bff6-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5bff6-115">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="5bff6-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bff6-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5bff6-116">Child Elements</span></span>  
 <span data-ttu-id="5bff6-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="5bff6-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bff6-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5bff6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5bff6-119">Element</span><span class="sxs-lookup"><span data-stu-id="5bff6-119">Element</span></span>|<span data-ttu-id="5bff6-120">Opis</span><span class="sxs-lookup"><span data-stu-id="5bff6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bff6-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5bff6-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="5bff6-122">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="5bff6-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bff6-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bff6-123">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
