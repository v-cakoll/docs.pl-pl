---
title: '&lt;transportConfigurationTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa136f75fda4a87171a8ca3e369e7cb8621ac398
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="a4c8a-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="a4c8a-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="a4c8a-103">Reprezentuje kolekcję elementów konfiguracji, które określa rodzaj danego transportu.</span><span class="sxs-lookup"><span data-stu-id="a4c8a-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="a4c8a-104">Może to służyć do dodawania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="a4c8a-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="a4c8a-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a4c8a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4c8a-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="a4c8a-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="a4c8a-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="a4c8a-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c8a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4c8a-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4c8a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a4c8a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a4c8a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a4c8a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4c8a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a4c8a-111">Attributes</span></span>  
  
|<span data-ttu-id="a4c8a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a4c8a-112">Attribute</span></span>|<span data-ttu-id="a4c8a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a4c8a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4c8a-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="a4c8a-114">name</span></span>|<span data-ttu-id="a4c8a-115">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="a4c8a-115">The name of the transport</span></span>|  
|<span data-ttu-id="a4c8a-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="a4c8a-116">transportConfigurationType</span></span>|<span data-ttu-id="a4c8a-117">Typ, który implementuje transportu</span><span class="sxs-lookup"><span data-stu-id="a4c8a-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4c8a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a4c8a-118">Child Elements</span></span>  
  
|<span data-ttu-id="a4c8a-119">Element</span><span class="sxs-lookup"><span data-stu-id="a4c8a-119">Element</span></span>|<span data-ttu-id="a4c8a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a4c8a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4c8a-121">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="a4c8a-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="a4c8a-122">Dodaje element konfiguracji, który identyfikuje typ danego transportu.</span><span class="sxs-lookup"><span data-stu-id="a4c8a-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4c8a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a4c8a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a4c8a-124">Element</span><span class="sxs-lookup"><span data-stu-id="a4c8a-124">Element</span></span>|<span data-ttu-id="a4c8a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a4c8a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4c8a-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="a4c8a-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="a4c8a-127">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="a4c8a-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4c8a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4c8a-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="a4c8a-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="a4c8a-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
