---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855110"
---
# <a name="mexendpoint"></a><span data-ttu-id="88196-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="88196-101">\<mexEndpoint></span></span>
<span data-ttu-id="88196-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="88196-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="88196-103">Ponieważ wszystkie punkty końcowe wymiany metadanych określają kontraktem IMetadataExchange jako kontrakt, można użyć tego standardowego punktu zamiast definiować go dla siebie.</span><span class="sxs-lookup"><span data-stu-id="88196-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
<span data-ttu-id="88196-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="88196-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="88196-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="88196-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="88196-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="88196-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="88196-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="88196-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88196-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="88196-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88196-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="88196-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88196-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="88196-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88196-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="88196-111">Attributes</span></span>  
  
|<span data-ttu-id="88196-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="88196-112">Attribute</span></span>|<span data-ttu-id="88196-113">Opis</span><span class="sxs-lookup"><span data-stu-id="88196-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88196-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="88196-114">name</span></span>|<span data-ttu-id="88196-115">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="88196-115">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="88196-116">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="88196-116">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88196-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="88196-117">Child Elements</span></span>  
 <span data-ttu-id="88196-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="88196-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88196-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="88196-119">Parent Elements</span></span>  
  
|<span data-ttu-id="88196-120">Element</span><span class="sxs-lookup"><span data-stu-id="88196-120">Element</span></span>|<span data-ttu-id="88196-121">Opis</span><span class="sxs-lookup"><span data-stu-id="88196-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88196-122">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="88196-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="88196-123">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="88196-123">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
