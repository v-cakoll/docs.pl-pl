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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75886c08d3e358d4ed6d3d3048594ef28f06a7af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="461b2-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="461b2-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="461b2-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="461b2-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="461b2-104">Ponieważ wszystkie punkty końcowe wymiany metadanych określić IMetadataExchange jako umowy, może użyć tego standardowego punktu, zamiast definiować jeden dla siebie.</span><span class="sxs-lookup"><span data-stu-id="461b2-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="461b2-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="461b2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="461b2-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="461b2-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461b2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="461b2-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="461b2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="461b2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="461b2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="461b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="461b2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="461b2-110">Attributes</span></span>  
  
|<span data-ttu-id="461b2-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="461b2-111">Attribute</span></span>|<span data-ttu-id="461b2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="461b2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="461b2-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="461b2-113">name</span></span>|<span data-ttu-id="461b2-114">Ciąg określający nazwę Konfiguracja standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="461b2-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="461b2-115">Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="461b2-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="461b2-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="461b2-116">Child Elements</span></span>  
 <span data-ttu-id="461b2-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="461b2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="461b2-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="461b2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="461b2-119">Element</span><span class="sxs-lookup"><span data-stu-id="461b2-119">Element</span></span>|<span data-ttu-id="461b2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="461b2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="461b2-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="461b2-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="461b2-122">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="461b2-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
