---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854930"
---
# \<transportConfigurationTypes>
<span data-ttu-id="8013f-101">Reprezentuje kolekcję elementów konfiguracji, które identyfikują typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="8013f-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="8013f-102">Można go użyć do dodania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="8013f-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="8013f-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="8013f-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8013f-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8013f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="8013f-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8013f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8013f-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8013f-106">Attributes</span></span>  
  
|<span data-ttu-id="8013f-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8013f-107">Attribute</span></span>|<span data-ttu-id="8013f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="8013f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8013f-109">name</span><span class="sxs-lookup"><span data-stu-id="8013f-109">name</span></span>|<span data-ttu-id="8013f-110">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="8013f-110">The name of the transport</span></span>|  
|<span data-ttu-id="8013f-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="8013f-111">transportConfigurationType</span></span>|<span data-ttu-id="8013f-112">Typ implementujący transport</span><span class="sxs-lookup"><span data-stu-id="8013f-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8013f-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8013f-113">Child Elements</span></span>  
  
|<span data-ttu-id="8013f-114">Element</span><span class="sxs-lookup"><span data-stu-id="8013f-114">Element</span></span>|<span data-ttu-id="8013f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8013f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="8013f-116">Dodaje element konfiguracji, który identyfikuje typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="8013f-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8013f-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8013f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8013f-118">Element</span><span class="sxs-lookup"><span data-stu-id="8013f-118">Element</span></span>|<span data-ttu-id="8013f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8013f-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="8013f-120">Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="8013f-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8013f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8013f-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="8013f-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="8013f-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
