---
title: <add> dla <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850582"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="f6ca2-102">\<add> dla \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="f6ca2-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="f6ca2-103">Reprezentuje element konfiguracji, który określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="f6ca2-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="f6ca2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6ca2-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="f6ca2-105">Typ</span><span class="sxs-lookup"><span data-stu-id="f6ca2-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6ca2-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6ca2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f6ca2-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f6ca2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6ca2-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6ca2-108">Attributes</span></span>  
  
|<span data-ttu-id="f6ca2-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6ca2-109">Attribute</span></span>|<span data-ttu-id="f6ca2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f6ca2-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="f6ca2-111">Ciąg określający adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="f6ca2-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6ca2-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6ca2-112">Child Elements</span></span>  
 <span data-ttu-id="f6ca2-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="f6ca2-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6ca2-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6ca2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f6ca2-115">Element</span><span class="sxs-lookup"><span data-stu-id="f6ca2-115">Element</span></span>|<span data-ttu-id="f6ca2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f6ca2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="f6ca2-117">Kolekcja `baseAddress` elementów.</span><span class="sxs-lookup"><span data-stu-id="f6ca2-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6ca2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6ca2-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="f6ca2-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="f6ca2-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
