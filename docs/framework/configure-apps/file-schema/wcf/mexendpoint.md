---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855110"
---
# \<mexEndpoint>
<span data-ttu-id="a08c0-101">Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="a08c0-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="a08c0-102">Ponieważ wszystkie punkty końcowe wymiany metadanych określają kontraktem IMetadataExchange jako kontrakt, można użyć tego standardowego punktu zamiast definiować go dla siebie.</span><span class="sxs-lookup"><span data-stu-id="a08c0-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="a08c0-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="a08c0-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a08c0-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a08c0-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a08c0-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a08c0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a08c0-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a08c0-106">Attributes</span></span>  
  
|<span data-ttu-id="a08c0-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a08c0-107">Attribute</span></span>|<span data-ttu-id="a08c0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a08c0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a08c0-109">name</span><span class="sxs-lookup"><span data-stu-id="a08c0-109">name</span></span>|<span data-ttu-id="a08c0-110">Ciąg określający nazwę konfiguracji standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a08c0-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="a08c0-111">Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="a08c0-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a08c0-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a08c0-112">Child Elements</span></span>  
 <span data-ttu-id="a08c0-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="a08c0-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a08c0-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a08c0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a08c0-115">Element</span><span class="sxs-lookup"><span data-stu-id="a08c0-115">Element</span></span>|<span data-ttu-id="a08c0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a08c0-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="a08c0-117">Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).</span><span class="sxs-lookup"><span data-stu-id="a08c0-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
