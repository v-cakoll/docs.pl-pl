---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 560da96c50e99461d25c1fd65def2dc10c284470
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261675"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="0047c-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="0047c-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="0047c-102">Reprezentuje kolekcję elementów konfiguracji, które identyfikują typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0047c-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="0047c-103">Może to służyć do dodawania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="0047c-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="0047c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0047c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0047c-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="0047c-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="0047c-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="0047c-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0047c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0047c-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0047c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0047c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0047c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0047c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0047c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0047c-110">Attributes</span></span>  
  
|<span data-ttu-id="0047c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0047c-111">Attribute</span></span>|<span data-ttu-id="0047c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0047c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0047c-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="0047c-113">name</span></span>|<span data-ttu-id="0047c-114">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="0047c-114">The name of the transport</span></span>|  
|<span data-ttu-id="0047c-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="0047c-115">transportConfigurationType</span></span>|<span data-ttu-id="0047c-116">Typ, który implementuje transportu</span><span class="sxs-lookup"><span data-stu-id="0047c-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0047c-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0047c-117">Child Elements</span></span>  
  
|<span data-ttu-id="0047c-118">Element</span><span class="sxs-lookup"><span data-stu-id="0047c-118">Element</span></span>|<span data-ttu-id="0047c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="0047c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0047c-120">\<add></span><span class="sxs-lookup"><span data-stu-id="0047c-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="0047c-121">Dodaje element konfiguracji, który identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0047c-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0047c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0047c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0047c-123">Element</span><span class="sxs-lookup"><span data-stu-id="0047c-123">Element</span></span>|<span data-ttu-id="0047c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="0047c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0047c-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="0047c-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="0047c-126">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0047c-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0047c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0047c-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="0047c-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="0047c-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
