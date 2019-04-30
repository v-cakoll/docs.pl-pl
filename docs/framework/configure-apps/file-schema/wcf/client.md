---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 2e0352efdd5b709984338fe4484b120bddb7d545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704300"
---
# <a name="client"></a><span data-ttu-id="24435-101">\<client></span><span class="sxs-lookup"><span data-stu-id="24435-101">\<client></span></span>
<span data-ttu-id="24435-102">`client` Element definiuje listę punktów końcowych, które klient może połączyć się z.</span><span class="sxs-lookup"><span data-stu-id="24435-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="24435-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="24435-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="24435-104">\<client></span><span class="sxs-lookup"><span data-stu-id="24435-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24435-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="24435-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24435-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24435-106">Attributes and Elements</span></span>  
 <span data-ttu-id="24435-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24435-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24435-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24435-108">Attributes</span></span>  
 <span data-ttu-id="24435-109">Brak</span><span class="sxs-lookup"><span data-stu-id="24435-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24435-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24435-110">Child Elements</span></span>  
  
|<span data-ttu-id="24435-111">Element</span><span class="sxs-lookup"><span data-stu-id="24435-111">Element</span></span>|<span data-ttu-id="24435-112">Opis</span><span class="sxs-lookup"><span data-stu-id="24435-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24435-113">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="24435-113">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="24435-114">Zawiera kolekcję elementów punktu końcowego, które określają punktów końcowych, które ten klient może połączyć się z.</span><span class="sxs-lookup"><span data-stu-id="24435-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="24435-115">\<metadata></span><span class="sxs-lookup"><span data-stu-id="24435-115">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="24435-116">Zawiera ustawienia dla przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="24435-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24435-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24435-117">Parent Elements</span></span>  
  
|<span data-ttu-id="24435-118">Element</span><span class="sxs-lookup"><span data-stu-id="24435-118">Element</span></span>|<span data-ttu-id="24435-119">Opis</span><span class="sxs-lookup"><span data-stu-id="24435-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24435-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="24435-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="24435-121">Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="24435-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24435-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24435-122">Remarks</span></span>  
 <span data-ttu-id="24435-123">`client` Sekcji definiuje listę punktów końcowych, które klient może nawiązać połączenia.</span><span class="sxs-lookup"><span data-stu-id="24435-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="24435-124">Każdy punkt końcowy na liście w sekcji klienta definiuje swój własny powiązania, zachowanie i umowy.</span><span class="sxs-lookup"><span data-stu-id="24435-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="24435-125">Jest unikatowo identyfikowana przez kombinację `name` i `contract` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="24435-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="24435-126">Określa kod klienta `name` połączyć się z punktem końcowym usługi, który implementuje klienta.</span><span class="sxs-lookup"><span data-stu-id="24435-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="24435-127">Jeśli `name` atrybut zostanie pominięty, punkt końcowy działa jako domyślny punkt końcowy dla kontraktu go implementuje.</span><span class="sxs-lookup"><span data-stu-id="24435-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="24435-128">Ponadto w tej sekcji określa również ustawienia dla przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="24435-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24435-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="24435-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24435-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24435-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="24435-131">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="24435-131">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="24435-132">Klienci</span><span class="sxs-lookup"><span data-stu-id="24435-132">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
