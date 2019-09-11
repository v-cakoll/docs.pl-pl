---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854930"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="2759b-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="2759b-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="2759b-102">Reprezentuje kolekcję elementów konfiguracji, które identyfikują typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="2759b-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="2759b-103">Można go użyć do dodania niestandardowych protokołów WAS.</span><span class="sxs-lookup"><span data-stu-id="2759b-103">This can be used to add custom WAS protocols.</span></span>  
  
<span data-ttu-id="2759b-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2759b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2759b-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2759b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2759b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="2759b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="2759b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transportConfigurationTypes >**</span><span class="sxs-lookup"><span data-stu-id="2759b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2759b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2759b-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2759b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2759b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2759b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2759b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2759b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2759b-111">Attributes</span></span>  
  
|<span data-ttu-id="2759b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2759b-112">Attribute</span></span>|<span data-ttu-id="2759b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2759b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2759b-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="2759b-114">name</span></span>|<span data-ttu-id="2759b-115">Nazwa transportu</span><span class="sxs-lookup"><span data-stu-id="2759b-115">The name of the transport</span></span>|  
|<span data-ttu-id="2759b-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="2759b-116">transportConfigurationType</span></span>|<span data-ttu-id="2759b-117">Typ implementujący transport</span><span class="sxs-lookup"><span data-stu-id="2759b-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2759b-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2759b-118">Child Elements</span></span>  
  
|<span data-ttu-id="2759b-119">Element</span><span class="sxs-lookup"><span data-stu-id="2759b-119">Element</span></span>|<span data-ttu-id="2759b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2759b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2759b-121">\<add></span><span class="sxs-lookup"><span data-stu-id="2759b-121">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="2759b-122">Dodaje element konfiguracji, który identyfikuje typ określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="2759b-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2759b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2759b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2759b-124">Element</span><span class="sxs-lookup"><span data-stu-id="2759b-124">Element</span></span>|<span data-ttu-id="2759b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2759b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2759b-126">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="2759b-126">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="2759b-127">Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="2759b-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2759b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2759b-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="2759b-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="2759b-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
