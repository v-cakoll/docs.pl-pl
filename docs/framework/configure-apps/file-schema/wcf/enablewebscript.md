---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400385"
---
# \<enableWebScript>
<span data-ttu-id="b408a-101">Ten element włącza zachowanie punktu końcowego, który umożliwia korzystanie z usługi z ASP.NET AJAX stron sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b408a-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="b408a-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="b408a-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b408a-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b408a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b408a-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b408a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b408a-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b408a-105">Attributes</span></span>  
 <span data-ttu-id="b408a-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="b408a-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b408a-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b408a-107">Child Elements</span></span>  
 <span data-ttu-id="b408a-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="b408a-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b408a-109">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b408a-109">Parent Elements</span></span>  
  
|<span data-ttu-id="b408a-110">Element</span><span class="sxs-lookup"><span data-stu-id="b408a-110">Element</span></span>|<span data-ttu-id="b408a-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b408a-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b408a-112">Określa zestaw zachowań punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="b408a-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b408a-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b408a-113">Remarks</span></span>  
 <span data-ttu-id="b408a-114">Tego zachowania należy używać tylko w połączeniu ze [\<webHttpBinding>](webhttpbinding.md) standardowym powiązaniem lub [\<webMessageEncoding>](webmessageencoding.md) elementem powiązania.</span><span class="sxs-lookup"><span data-stu-id="b408a-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="b408a-115">Aby uzyskać więcej informacji na temat tego zachowania, zobacz <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> .</span><span class="sxs-lookup"><span data-stu-id="b408a-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b408a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b408a-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="b408a-117">Obsługa integracji AJAX i notacji JSON</span><span class="sxs-lookup"><span data-stu-id="b408a-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
