---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399709"
---
# \<serviceAuthenticationManager>
<span data-ttu-id="643df-101">Zawiera element konfiguracji przepływu pracy, który ustala na poziomie usługi ważność transmisji, wiadomości lub nadawcy.</span><span class="sxs-lookup"><span data-stu-id="643df-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="643df-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="643df-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="643df-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="643df-103">Attributes and Elements</span></span>  
 <span data-ttu-id="643df-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="643df-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="643df-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="643df-105">Attributes</span></span>  
  
|<span data-ttu-id="643df-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="643df-106">Attribute</span></span>|<span data-ttu-id="643df-107">Opis</span><span class="sxs-lookup"><span data-stu-id="643df-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="643df-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="643df-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="643df-109">Ciąg określający typ zasad uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="643df-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="643df-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="643df-110">Child Elements</span></span>  
 <span data-ttu-id="643df-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="643df-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="643df-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="643df-112">Parent Elements</span></span>  
  
|<span data-ttu-id="643df-113">Element</span><span class="sxs-lookup"><span data-stu-id="643df-113">Element</span></span>|<span data-ttu-id="643df-114">Opis</span><span class="sxs-lookup"><span data-stu-id="643df-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="643df-115">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="643df-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="643df-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="643df-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
