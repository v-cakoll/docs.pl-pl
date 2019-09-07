---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399709"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="d9492-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="d9492-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="d9492-102">Zawiera element konfiguracji przepływu pracy, który ustala na poziomie usługi ważność transmisji, wiadomości lub nadawcy.</span><span class="sxs-lookup"><span data-stu-id="d9492-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="d9492-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d9492-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d9492-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d9492-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d9492-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9492-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="d9492-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9492-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="d9492-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9492-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="d9492-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> ServiceAuthenticationManager**</span><span class="sxs-lookup"><span data-stu-id="d9492-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9492-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9492-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9492-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d9492-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d9492-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d9492-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9492-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d9492-112">Attributes</span></span>  
  
|<span data-ttu-id="d9492-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d9492-113">Attribute</span></span>|<span data-ttu-id="d9492-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d9492-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9492-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="d9492-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="d9492-116">Ciąg określający typ zasad uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="d9492-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9492-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d9492-117">Child Elements</span></span>  
 <span data-ttu-id="d9492-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="d9492-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9492-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d9492-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d9492-120">Element</span><span class="sxs-lookup"><span data-stu-id="d9492-120">Element</span></span>|<span data-ttu-id="d9492-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d9492-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9492-122">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="d9492-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d9492-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="d9492-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9492-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9492-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
