---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: b3683a198ec403fb9966bb902c936108fd043bfa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083650"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="d3f20-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="d3f20-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="d3f20-102">Reprezentuje kolekcję elementów konfiguracji, które identyfikują typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="d3f20-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="d3f20-103">Może to służyć do dodawania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="d3f20-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="d3f20-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d3f20-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d3f20-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="d3f20-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="d3f20-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="d3f20-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f20-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3f20-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3f20-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d3f20-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d3f20-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d3f20-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3f20-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d3f20-110">Attributes</span></span>  
  
|<span data-ttu-id="d3f20-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d3f20-111">Attribute</span></span>|<span data-ttu-id="d3f20-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d3f20-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3f20-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="d3f20-113">name</span></span>|<span data-ttu-id="d3f20-114">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="d3f20-114">The name of the transport</span></span>|  
|<span data-ttu-id="d3f20-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="d3f20-115">transportConfigurationType</span></span>|<span data-ttu-id="d3f20-116">Typ, który implementuje transportu</span><span class="sxs-lookup"><span data-stu-id="d3f20-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3f20-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d3f20-117">Child Elements</span></span>  
  
|<span data-ttu-id="d3f20-118">Element</span><span class="sxs-lookup"><span data-stu-id="d3f20-118">Element</span></span>|<span data-ttu-id="d3f20-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d3f20-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3f20-120">\<add></span><span class="sxs-lookup"><span data-stu-id="d3f20-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="d3f20-121">Dodaje element konfiguracji, który identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="d3f20-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3f20-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d3f20-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d3f20-123">Element</span><span class="sxs-lookup"><span data-stu-id="d3f20-123">Element</span></span>|<span data-ttu-id="d3f20-124">Opis</span><span class="sxs-lookup"><span data-stu-id="d3f20-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3f20-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="d3f20-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="d3f20-126">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="d3f20-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3f20-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3f20-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="d3f20-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="d3f20-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
