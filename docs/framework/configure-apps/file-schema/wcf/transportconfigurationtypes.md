---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 422de17f4c1b42579eadc16c7ec1a0037903d1a9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="65ee1-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="65ee1-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="65ee1-103">Reprezentuje kolekcję elementów konfiguracji, które określa rodzaj danego transportu.</span><span class="sxs-lookup"><span data-stu-id="65ee1-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="65ee1-104">Może to służyć do dodawania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="65ee1-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="65ee1-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="65ee1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="65ee1-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="65ee1-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="65ee1-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="65ee1-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ee1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="65ee1-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65ee1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="65ee1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="65ee1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="65ee1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65ee1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="65ee1-111">Attributes</span></span>  
  
|<span data-ttu-id="65ee1-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="65ee1-112">Attribute</span></span>|<span data-ttu-id="65ee1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="65ee1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65ee1-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="65ee1-114">name</span></span>|<span data-ttu-id="65ee1-115">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="65ee1-115">The name of the transport</span></span>|  
|<span data-ttu-id="65ee1-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="65ee1-116">transportConfigurationType</span></span>|<span data-ttu-id="65ee1-117">Typ, który implementuje transportu</span><span class="sxs-lookup"><span data-stu-id="65ee1-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65ee1-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65ee1-118">Child Elements</span></span>  
  
|<span data-ttu-id="65ee1-119">Element</span><span class="sxs-lookup"><span data-stu-id="65ee1-119">Element</span></span>|<span data-ttu-id="65ee1-120">Opis</span><span class="sxs-lookup"><span data-stu-id="65ee1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65ee1-121">\<add></span><span class="sxs-lookup"><span data-stu-id="65ee1-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="65ee1-122">Dodaje element konfiguracji, który identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="65ee1-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65ee1-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65ee1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="65ee1-124">Element</span><span class="sxs-lookup"><span data-stu-id="65ee1-124">Element</span></span>|<span data-ttu-id="65ee1-125">Opis</span><span class="sxs-lookup"><span data-stu-id="65ee1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65ee1-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="65ee1-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="65ee1-127">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="65ee1-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65ee1-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65ee1-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="65ee1-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="65ee1-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
