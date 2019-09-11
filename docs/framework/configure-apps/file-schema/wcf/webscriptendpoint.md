---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854816"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="bf93a-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="bf93a-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="bf93a-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze [ \<](enablewebscript.md) stałym [ \<powiązaniem WebHttpBinding >](webhttpbinding.md) , które automatycznie dodaje zachowanie > enableWebScript.</span><span class="sxs-lookup"><span data-stu-id="bf93a-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="bf93a-103">Użyj tego punktu końcowego podczas pisania usługi, która jest wywoływana z aplikacji ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="bf93a-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="bf93a-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf93a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bf93a-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bf93a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bf93a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="bf93a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="bf93a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webScriptEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="bf93a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf93a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf93a-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf93a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf93a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bf93a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf93a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf93a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf93a-111">Attributes</span></span>  
  
|<span data-ttu-id="bf93a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bf93a-112">Attribute</span></span>|<span data-ttu-id="bf93a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bf93a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf93a-114">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="bf93a-114">webEndpointType</span></span>|<span data-ttu-id="bf93a-115">Ciąg określający typ punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="bf93a-115">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf93a-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf93a-116">Child Elements</span></span>  
 <span data-ttu-id="bf93a-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf93a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf93a-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf93a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bf93a-119">Element</span><span class="sxs-lookup"><span data-stu-id="bf93a-119">Element</span></span>|<span data-ttu-id="bf93a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="bf93a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf93a-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="bf93a-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="bf93a-122">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="bf93a-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf93a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf93a-123">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
