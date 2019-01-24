---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 37ce20c5fb0791596264bb7b6c03d5d0f2cc2388
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704920"
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="0fb6f-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="0fb6f-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="0fb6f-103">Reprezentuje kolekcję elementów konfiguracji, które identyfikują typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0fb6f-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="0fb6f-104">Może to służyć do dodawania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="0fb6f-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="0fb6f-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0fb6f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0fb6f-106">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="0fb6f-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="0fb6f-107">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="0fb6f-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb6f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fb6f-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fb6f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0fb6f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0fb6f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0fb6f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fb6f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0fb6f-111">Attributes</span></span>  
  
|<span data-ttu-id="0fb6f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0fb6f-112">Attribute</span></span>|<span data-ttu-id="0fb6f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0fb6f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0fb6f-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="0fb6f-114">name</span></span>|<span data-ttu-id="0fb6f-115">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="0fb6f-115">The name of the transport</span></span>|  
|<span data-ttu-id="0fb6f-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="0fb6f-116">transportConfigurationType</span></span>|<span data-ttu-id="0fb6f-117">Typ, który implementuje transportu</span><span class="sxs-lookup"><span data-stu-id="0fb6f-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fb6f-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0fb6f-118">Child Elements</span></span>  
  
|<span data-ttu-id="0fb6f-119">Element</span><span class="sxs-lookup"><span data-stu-id="0fb6f-119">Element</span></span>|<span data-ttu-id="0fb6f-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0fb6f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fb6f-121">\<add></span><span class="sxs-lookup"><span data-stu-id="0fb6f-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="0fb6f-122">Dodaje element konfiguracji, który identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0fb6f-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fb6f-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0fb6f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0fb6f-124">Element</span><span class="sxs-lookup"><span data-stu-id="0fb6f-124">Element</span></span>|<span data-ttu-id="0fb6f-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0fb6f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fb6f-126">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="0fb6f-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="0fb6f-127">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0fb6f-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fb6f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fb6f-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="0fb6f-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="0fb6f-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
