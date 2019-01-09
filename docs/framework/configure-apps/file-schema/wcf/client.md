---
title: '&lt;Klient&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 24defe7e01603f1b1be3023d07854091335d6c60
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148646"
---
# <a name="ltclientgt"></a><span data-ttu-id="52535-102">&lt;Klient&gt;</span><span class="sxs-lookup"><span data-stu-id="52535-102">&lt;client&gt;</span></span>
<span data-ttu-id="52535-103">`client` Element definiuje listę punktów końcowych, które klient może połączyć się z.</span><span class="sxs-lookup"><span data-stu-id="52535-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="52535-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="52535-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="52535-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="52535-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52535-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="52535-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52535-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="52535-107">Attributes and Elements</span></span>  
 <span data-ttu-id="52535-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="52535-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52535-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="52535-109">Attributes</span></span>  
 <span data-ttu-id="52535-110">Brak</span><span class="sxs-lookup"><span data-stu-id="52535-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="52535-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="52535-111">Child Elements</span></span>  
  
|<span data-ttu-id="52535-112">Element</span><span class="sxs-lookup"><span data-stu-id="52535-112">Element</span></span>|<span data-ttu-id="52535-113">Opis</span><span class="sxs-lookup"><span data-stu-id="52535-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52535-114">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="52535-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="52535-115">Zawiera kolekcję elementów punktu końcowego, które określają punktów końcowych, które ten klient może połączyć się z.</span><span class="sxs-lookup"><span data-stu-id="52535-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="52535-116">\<metadane ></span><span class="sxs-lookup"><span data-stu-id="52535-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="52535-117">Zawiera ustawienia dla przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="52535-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52535-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="52535-118">Parent Elements</span></span>  
  
|<span data-ttu-id="52535-119">Element</span><span class="sxs-lookup"><span data-stu-id="52535-119">Element</span></span>|<span data-ttu-id="52535-120">Opis</span><span class="sxs-lookup"><span data-stu-id="52535-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52535-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="52535-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="52535-122">Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="52535-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52535-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52535-123">Remarks</span></span>  
 <span data-ttu-id="52535-124">`client` Sekcji definiuje listę punktów końcowych, które klient może nawiązać połączenia.</span><span class="sxs-lookup"><span data-stu-id="52535-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="52535-125">Każdy punkt końcowy na liście w sekcji klienta definiuje swój własny powiązania, zachowanie i umowy.</span><span class="sxs-lookup"><span data-stu-id="52535-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="52535-126">Jest unikatowo identyfikowana przez kombinację `name` i `contract` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="52535-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="52535-127">Określa kod klienta `name` połączyć się z punktem końcowym usługi, który implementuje klienta.</span><span class="sxs-lookup"><span data-stu-id="52535-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="52535-128">Jeśli `name` atrybut zostanie pominięty, punkt końcowy działa jako domyślny punkt końcowy dla kontraktu go implementuje.</span><span class="sxs-lookup"><span data-stu-id="52535-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="52535-129">Ponadto w tej sekcji określa również ustawienia dla przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="52535-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52535-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="52535-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="52535-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52535-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="52535-132">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="52535-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="52535-133">Klienci</span><span class="sxs-lookup"><span data-stu-id="52535-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
