---
title: '&lt;mexEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6eefecb696c88d160e56c7f12a1b03ea67e531b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="5631e-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="5631e-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="5631e-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="5631e-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="5631e-104">Ponieważ wszystkie punkty końcowe wymiany metadanych określić IMetadataExchange jako umowy, może użyć tego standardowego punktu, zamiast definiować jeden dla siebie.</span><span class="sxs-lookup"><span data-stu-id="5631e-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="5631e-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5631e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5631e-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5631e-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5631e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5631e-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5631e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5631e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5631e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5631e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5631e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5631e-110">Attributes</span></span>  
  
|<span data-ttu-id="5631e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5631e-111">Attribute</span></span>|<span data-ttu-id="5631e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5631e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5631e-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="5631e-113">name</span></span>|<span data-ttu-id="5631e-114">Ciąg określający nazwę Konfiguracja standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5631e-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5631e-115">Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5631e-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5631e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5631e-116">Child Elements</span></span>  
 <span data-ttu-id="5631e-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="5631e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5631e-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5631e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5631e-119">Element</span><span class="sxs-lookup"><span data-stu-id="5631e-119">Element</span></span>|<span data-ttu-id="5631e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="5631e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5631e-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5631e-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5631e-122">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="5631e-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
