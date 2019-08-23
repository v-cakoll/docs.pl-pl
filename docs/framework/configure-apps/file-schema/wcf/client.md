---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7dce5984882e48c3e62efc44ef00b6256d9eb64e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919526"
---
# <a name="client"></a><span data-ttu-id="4e34e-101">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="4e34e-101">\<client></span></span>
<span data-ttu-id="4e34e-102">`client` Element definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="4e34e-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="4e34e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4e34e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4e34e-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="4e34e-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e34e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e34e-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e34e-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e34e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4e34e-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e34e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e34e-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e34e-108">Attributes</span></span>  
 <span data-ttu-id="4e34e-109">Brak</span><span class="sxs-lookup"><span data-stu-id="4e34e-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e34e-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e34e-110">Child Elements</span></span>  
  
|<span data-ttu-id="4e34e-111">Element</span><span class="sxs-lookup"><span data-stu-id="4e34e-111">Element</span></span>|<span data-ttu-id="4e34e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4e34e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e34e-113">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="4e34e-113">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="4e34e-114">Zawiera kolekcję elementów punktu końcowego, które określają punkty końcowe, z którymi ten klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="4e34e-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="4e34e-115">\<> metadanych</span><span class="sxs-lookup"><span data-stu-id="4e34e-115">\<metadata></span></span>](metadata.md)|<span data-ttu-id="4e34e-116">Zawiera ustawienia dotyczące przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="4e34e-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4e34e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e34e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4e34e-118">Element</span><span class="sxs-lookup"><span data-stu-id="4e34e-118">Element</span></span>|<span data-ttu-id="4e34e-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4e34e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e34e-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4e34e-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="4e34e-121">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4e34e-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e34e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e34e-122">Remarks</span></span>  
 <span data-ttu-id="4e34e-123">`client` Sekcja definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="4e34e-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="4e34e-124">Każdy punkt końcowy wymieniony w sekcji Client definiuje własne powiązanie, zachowanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4e34e-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="4e34e-125">Jest unikatowo identyfikowana przez kombinację `name` atrybutów i. `contract`</span><span class="sxs-lookup"><span data-stu-id="4e34e-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="4e34e-126">Kod klienta określa, `name` aby połączyć się z punktem końcowym usługi, którą implementuje klient.</span><span class="sxs-lookup"><span data-stu-id="4e34e-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="4e34e-127">`name` Jeśli atrybut zostanie pominięty, punkt końcowy działa jako domyślny punkt końcowy dla wdrażanego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4e34e-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="4e34e-128">Ponadto ta sekcja określa również ustawienia przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="4e34e-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e34e-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e34e-129">Example</span></span>  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a><span data-ttu-id="4e34e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e34e-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="4e34e-131">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="4e34e-131">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="4e34e-132">Klienci</span><span class="sxs-lookup"><span data-stu-id="4e34e-132">Clients</span></span>](../../../wcf/feature-details/clients.md)
