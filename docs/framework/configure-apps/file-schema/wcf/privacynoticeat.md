---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738766"
---
# \<privacyNoticeAt>
<span data-ttu-id="f77f6-101">Reprezentuje element konfiguracji, który określa powiadomienie o prywatności użyte w `wsFederationHttp` powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="f77f6-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="f77f6-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="f77f6-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f77f6-103">Typ</span><span class="sxs-lookup"><span data-stu-id="f77f6-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f77f6-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f77f6-104">Attributes and Elements</span></span>  
 <span data-ttu-id="f77f6-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f77f6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f77f6-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f77f6-106">Attributes</span></span>  
  
|<span data-ttu-id="f77f6-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f77f6-107">Attribute</span></span>|<span data-ttu-id="f77f6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f77f6-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="f77f6-109">Ciąg określający identyfikator URI, w którym znajduje się powiadomienie o prywatności.</span><span class="sxs-lookup"><span data-stu-id="f77f6-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="f77f6-110">Liczba całkowita określająca wersję tego powiadomienia o ochronie prywatności.</span><span class="sxs-lookup"><span data-stu-id="f77f6-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f77f6-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f77f6-111">Child Elements</span></span>  
 <span data-ttu-id="f77f6-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="f77f6-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f77f6-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f77f6-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f77f6-114">Element</span><span class="sxs-lookup"><span data-stu-id="f77f6-114">Element</span></span>|<span data-ttu-id="f77f6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f77f6-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f77f6-116">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f77f6-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f77f6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f77f6-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f77f6-118">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f77f6-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f77f6-119">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f77f6-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f77f6-120">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f77f6-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
