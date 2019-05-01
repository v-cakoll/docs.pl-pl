---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 8fffcc05d5f53f719efce182083fbf103b1230ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772479"
---
# <a name="mexendpoint"></a><span data-ttu-id="9c4a3-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="9c4a3-101">\<mexEndpoint></span></span>
<span data-ttu-id="9c4a3-102">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="9c4a3-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="9c4a3-103">Ponieważ wszystkie punkty końcowe wymiany metadanych określić IMetadataExchange jako ich kontraktu, możesz użyć tego standardowego punktu, zamiast definiować po jednym dla siebie.</span><span class="sxs-lookup"><span data-stu-id="9c4a3-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="9c4a3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9c4a3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9c4a3-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="9c4a3-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4a3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c4a3-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c4a3-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c4a3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9c4a3-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9c4a3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c4a3-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c4a3-109">Attributes</span></span>  
  
|<span data-ttu-id="9c4a3-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9c4a3-110">Attribute</span></span>|<span data-ttu-id="9c4a3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4a3-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c4a3-112">nazwa</span><span class="sxs-lookup"><span data-stu-id="9c4a3-112">name</span></span>|<span data-ttu-id="9c4a3-113">Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="9c4a3-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="9c4a3-114">Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9c4a3-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c4a3-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c4a3-115">Child Elements</span></span>  
 <span data-ttu-id="9c4a3-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c4a3-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c4a3-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c4a3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9c4a3-118">Element</span><span class="sxs-lookup"><span data-stu-id="9c4a3-118">Element</span></span>|<span data-ttu-id="9c4a3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="9c4a3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c4a3-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="9c4a3-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="9c4a3-121">Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.</span><span class="sxs-lookup"><span data-stu-id="9c4a3-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
