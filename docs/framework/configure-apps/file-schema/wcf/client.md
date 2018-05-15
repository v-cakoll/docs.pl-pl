---
title: '&lt;Klienta&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: b8a006d3dee4149569b3f5b573d9d765504b0d65
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltclientgt"></a><span data-ttu-id="14b68-102">&lt;Klienta&gt;</span><span class="sxs-lookup"><span data-stu-id="14b68-102">&lt;client&gt;</span></span>
<span data-ttu-id="14b68-103">`client` Element definiuje listę punktów końcowych, które klient może nawiązać połączenia.</span><span class="sxs-lookup"><span data-stu-id="14b68-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="14b68-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="14b68-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="14b68-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="14b68-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b68-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="14b68-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <endpoint>  
        </endpoint>  
                <metadata>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14b68-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="14b68-107">Attributes and Elements</span></span>  
 <span data-ttu-id="14b68-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="14b68-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14b68-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="14b68-109">Attributes</span></span>  
 <span data-ttu-id="14b68-110">Brak</span><span class="sxs-lookup"><span data-stu-id="14b68-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14b68-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="14b68-111">Child Elements</span></span>  
  
|<span data-ttu-id="14b68-112">Element</span><span class="sxs-lookup"><span data-stu-id="14b68-112">Element</span></span>|<span data-ttu-id="14b68-113">Opis</span><span class="sxs-lookup"><span data-stu-id="14b68-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14b68-114">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="14b68-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="14b68-115">Zawiera kolekcję elementów punktu końcowego, określające punkty końcowe, które ten klient może nawiązać połączenia.</span><span class="sxs-lookup"><span data-stu-id="14b68-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="14b68-116">\<metadane ></span><span class="sxs-lookup"><span data-stu-id="14b68-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="14b68-117">Zawiera ustawienia dla przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="14b68-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14b68-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="14b68-118">Parent Elements</span></span>  
  
|<span data-ttu-id="14b68-119">Element</span><span class="sxs-lookup"><span data-stu-id="14b68-119">Element</span></span>|<span data-ttu-id="14b68-120">Opis</span><span class="sxs-lookup"><span data-stu-id="14b68-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14b68-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="14b68-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="14b68-122">Element główny wszystkich elementów konfiguracji systemu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="14b68-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14b68-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14b68-123">Remarks</span></span>  
 <span data-ttu-id="14b68-124">`client` Sekcja definiuje listę punktów końcowych, które klient może nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="14b68-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="14b68-125">Każdy punkt końcowy wymienione w sekcji klienta definiuje własną powiązanie, zachowania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="14b68-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="14b68-126">Jest unikatowo identyfikowana przez kombinację `name` i `contract` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="14b68-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="14b68-127">Określa kod klienta `name` nawiązać połączenia z punktu końcowego usługi, który implementuje klienta.</span><span class="sxs-lookup"><span data-stu-id="14b68-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="14b68-128">Jeśli `name` atrybut nie jest określony, punkt końcowy działa jako domyślnego punktu końcowego dla kontraktu ją implementuje.</span><span class="sxs-lookup"><span data-stu-id="14b68-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="14b68-129">Ponadto w tej sekcji również określa ustawienia dla przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="14b68-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14b68-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="14b68-130">Example</span></span>  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14b68-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14b68-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="14b68-132">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="14b68-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="14b68-133">Klienci</span><span class="sxs-lookup"><span data-stu-id="14b68-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
