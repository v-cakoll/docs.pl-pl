---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: bfd2147a8e772848fc98cab7a875a51bdb53b5cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941161"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="a03d5-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="a03d5-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="a03d5-102">Reprezentuje kolekcję elementów konfiguracji, które identyfikują typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="a03d5-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="a03d5-103">Można go użyć do dodania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="a03d5-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="a03d5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a03d5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a03d5-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="a03d5-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="a03d5-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="a03d5-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a03d5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a03d5-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a03d5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a03d5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a03d5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a03d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a03d5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a03d5-110">Attributes</span></span>  
  
|<span data-ttu-id="a03d5-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a03d5-111">Attribute</span></span>|<span data-ttu-id="a03d5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a03d5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a03d5-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="a03d5-113">name</span></span>|<span data-ttu-id="a03d5-114">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="a03d5-114">The name of the transport</span></span>|  
|<span data-ttu-id="a03d5-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="a03d5-115">transportConfigurationType</span></span>|<span data-ttu-id="a03d5-116">Typ implementujący transport</span><span class="sxs-lookup"><span data-stu-id="a03d5-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a03d5-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a03d5-117">Child Elements</span></span>  
  
|<span data-ttu-id="a03d5-118">Element</span><span class="sxs-lookup"><span data-stu-id="a03d5-118">Element</span></span>|<span data-ttu-id="a03d5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a03d5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a03d5-120">\<add></span><span class="sxs-lookup"><span data-stu-id="a03d5-120">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="a03d5-121">Dodaje element konfiguracji, który identyfikuje typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="a03d5-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a03d5-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a03d5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a03d5-123">Element</span><span class="sxs-lookup"><span data-stu-id="a03d5-123">Element</span></span>|<span data-ttu-id="a03d5-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a03d5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a03d5-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="a03d5-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="a03d5-126">Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="a03d5-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a03d5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a03d5-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="a03d5-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="a03d5-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
