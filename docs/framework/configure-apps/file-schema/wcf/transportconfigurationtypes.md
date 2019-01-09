---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 5a51450d198ea395098f8a6a38d9104d0fe8538b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145474"
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="0811c-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="0811c-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="0811c-103">Reprezentuje kolekcję elementów konfiguracji, które identyfikują typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0811c-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="0811c-104">Może to służyć do dodawania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="0811c-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="0811c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0811c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0811c-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="0811c-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="0811c-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="0811c-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0811c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="0811c-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0811c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0811c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0811c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0811c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0811c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0811c-111">Attributes</span></span>  
  
|<span data-ttu-id="0811c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0811c-112">Attribute</span></span>|<span data-ttu-id="0811c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0811c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0811c-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="0811c-114">name</span></span>|<span data-ttu-id="0811c-115">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="0811c-115">The name of the transport</span></span>|  
|<span data-ttu-id="0811c-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="0811c-116">transportConfigurationType</span></span>|<span data-ttu-id="0811c-117">Typ, który implementuje transportu</span><span class="sxs-lookup"><span data-stu-id="0811c-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0811c-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0811c-118">Child Elements</span></span>  
  
|<span data-ttu-id="0811c-119">Element</span><span class="sxs-lookup"><span data-stu-id="0811c-119">Element</span></span>|<span data-ttu-id="0811c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0811c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0811c-121">\<add></span><span class="sxs-lookup"><span data-stu-id="0811c-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="0811c-122">Dodaje element konfiguracji, który identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0811c-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0811c-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0811c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0811c-124">Element</span><span class="sxs-lookup"><span data-stu-id="0811c-124">Element</span></span>|<span data-ttu-id="0811c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0811c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0811c-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="0811c-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="0811c-127">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="0811c-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0811c-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0811c-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="0811c-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="0811c-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
