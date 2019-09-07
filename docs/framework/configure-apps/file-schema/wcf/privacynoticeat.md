---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 624b52c0618362f48063c8f7e7c53c5a68d7de8f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400031"
---
# <a name="privacynoticeat"></a><span data-ttu-id="a6273-101">\<privacyNoticeAt></span><span class="sxs-lookup"><span data-stu-id="a6273-101">\<privacyNoticeAt></span></span>
<span data-ttu-id="a6273-102">Reprezentuje element konfiguracji, który określa powiadomienie o prywatności użyte w `wsFederationHttp` powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="a6273-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
<span data-ttu-id="a6273-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6273-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6273-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a6273-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a6273-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a6273-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a6273-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="a6273-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="a6273-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="a6273-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a6273-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<privacyNotice >**</span><span class="sxs-lookup"><span data-stu-id="a6273-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6273-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6273-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="a6273-110">Typ</span><span class="sxs-lookup"><span data-stu-id="a6273-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6273-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6273-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6273-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a6273-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6273-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6273-113">Attributes</span></span>  
  
|<span data-ttu-id="a6273-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a6273-114">Attribute</span></span>|<span data-ttu-id="a6273-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a6273-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="a6273-116">Ciąg określający identyfikator URI, w którym znajduje się powiadomienie o prywatności.</span><span class="sxs-lookup"><span data-stu-id="a6273-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="a6273-117">Liczba całkowita określająca wersję tego powiadomienia o ochronie prywatności.</span><span class="sxs-lookup"><span data-stu-id="a6273-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6273-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6273-118">Child Elements</span></span>  
 <span data-ttu-id="a6273-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="a6273-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6273-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6273-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a6273-121">Element</span><span class="sxs-lookup"><span data-stu-id="a6273-121">Element</span></span>|<span data-ttu-id="a6273-122">Opis</span><span class="sxs-lookup"><span data-stu-id="a6273-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6273-123">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="a6273-123">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="a6273-124">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a6273-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6273-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6273-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a6273-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a6273-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a6273-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="a6273-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a6273-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a6273-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a6273-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a6273-129">\<customBinding></span></span>](custombinding.md)
