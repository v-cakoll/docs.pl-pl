---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400385"
---
# <a name="enablewebscript"></a><span data-ttu-id="45e3c-101">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="45e3c-101">\<enableWebScript></span></span>
<span data-ttu-id="45e3c-102">Ten element włącza zachowanie punktu końcowego, który umożliwia korzystanie z usługi z ASP.NET AJAX stron sieci Web.</span><span class="sxs-lookup"><span data-stu-id="45e3c-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
<span data-ttu-id="45e3c-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45e3c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45e3c-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="45e3c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="45e3c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="45e3c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="45e3c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="45e3c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="45e3c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="45e3c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="45e3c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<enableWebScript >**</span><span class="sxs-lookup"><span data-stu-id="45e3c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e3c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="45e3c-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45e3c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="45e3c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="45e3c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="45e3c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45e3c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="45e3c-112">Attributes</span></span>  
 <span data-ttu-id="45e3c-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="45e3c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="45e3c-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="45e3c-114">Child Elements</span></span>  
 <span data-ttu-id="45e3c-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="45e3c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45e3c-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="45e3c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="45e3c-117">Element</span><span class="sxs-lookup"><span data-stu-id="45e3c-117">Element</span></span>|<span data-ttu-id="45e3c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="45e3c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45e3c-119">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="45e3c-119">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="45e3c-120">Określa zestaw zachowań punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="45e3c-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45e3c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45e3c-121">Remarks</span></span>  
 <span data-ttu-id="45e3c-122">Tego zachowania należy używać tylko w połączeniu z [ \<elementem WebHttpBinding >](webhttpbinding.md) [ \<](webmessageencoding.md) powiązanie standardowe lub webMessageEncoding > powiązania.</span><span class="sxs-lookup"><span data-stu-id="45e3c-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="45e3c-123">Aby uzyskać więcej informacji na temat tego zachowania <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="45e3c-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e3c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45e3c-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="45e3c-125">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="45e3c-125">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="45e3c-126">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="45e3c-126">\<webHttp></span></span>](webhttp.md)
