---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 78788f9dfbf6cdf3439fd6e33eddfe721e49840d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931256"
---
# <a name="mexendpoint"></a><span data-ttu-id="a85f2-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="a85f2-101">\<mexEndpoint></span></span>
<span data-ttu-id="a85f2-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="a85f2-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="a85f2-103">Ponieważ wszystkie punkty końcowe wymiany metadanych określają kontraktem IMetadataExchange jako kontrakt, można użyć tego standardowego punktu zamiast definiować go dla siebie.</span><span class="sxs-lookup"><span data-stu-id="a85f2-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="a85f2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a85f2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a85f2-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a85f2-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a85f2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a85f2-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a85f2-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a85f2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a85f2-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a85f2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a85f2-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a85f2-109">Attributes</span></span>  
  
|<span data-ttu-id="a85f2-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a85f2-110">Attribute</span></span>|<span data-ttu-id="a85f2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a85f2-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a85f2-112">nazwa</span><span class="sxs-lookup"><span data-stu-id="a85f2-112">name</span></span>|<span data-ttu-id="a85f2-113">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a85f2-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="a85f2-114">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="a85f2-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a85f2-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a85f2-115">Child Elements</span></span>  
 <span data-ttu-id="a85f2-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="a85f2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a85f2-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a85f2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a85f2-118">Element</span><span class="sxs-lookup"><span data-stu-id="a85f2-118">Element</span></span>|<span data-ttu-id="a85f2-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a85f2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a85f2-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="a85f2-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="a85f2-121">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="a85f2-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
