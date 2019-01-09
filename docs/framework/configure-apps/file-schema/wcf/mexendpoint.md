---
title: '&lt;mexEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 4e2fb4946ee68b3cbd5bd6bfbafe6bb5e9c9106f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149153"
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="9bd9e-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="9bd9e-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="9bd9e-103">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="9bd9e-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="9bd9e-104">Ponieważ wszystkie punkty końcowe wymiany metadanych określić IMetadataExchange jako ich kontraktu, możesz użyć tego standardowego punktu, zamiast definiować po jednym dla siebie.</span><span class="sxs-lookup"><span data-stu-id="9bd9e-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="9bd9e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9bd9e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9bd9e-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9bd9e-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd9e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bd9e-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bd9e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9bd9e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9bd9e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9bd9e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bd9e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9bd9e-110">Attributes</span></span>  
  
|<span data-ttu-id="9bd9e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9bd9e-111">Attribute</span></span>|<span data-ttu-id="9bd9e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9bd9e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bd9e-113">nazwa</span><span class="sxs-lookup"><span data-stu-id="9bd9e-113">name</span></span>|<span data-ttu-id="9bd9e-114">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="9bd9e-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="9bd9e-115">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9bd9e-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bd9e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9bd9e-116">Child Elements</span></span>  
 <span data-ttu-id="9bd9e-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="9bd9e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bd9e-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9bd9e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9bd9e-119">Element</span><span class="sxs-lookup"><span data-stu-id="9bd9e-119">Element</span></span>|<span data-ttu-id="9bd9e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9bd9e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bd9e-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9bd9e-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9bd9e-122">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="9bd9e-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
