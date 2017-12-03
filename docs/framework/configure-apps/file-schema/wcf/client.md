---
title: '&lt;klienta&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 260408bd168246b67830637ca53e78b78758b849
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientgt"></a><span data-ttu-id="e4500-102">&lt;klienta&gt;</span><span class="sxs-lookup"><span data-stu-id="e4500-102">&lt;client&gt;</span></span>
<span data-ttu-id="e4500-103">`client` Element definiuje listę punktów końcowych, które klient może nawiązać połączenia.</span><span class="sxs-lookup"><span data-stu-id="e4500-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="e4500-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e4500-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4500-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="e4500-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4500-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4500-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4500-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e4500-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e4500-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e4500-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4500-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e4500-109">Attributes</span></span>  
 <span data-ttu-id="e4500-110">Brak</span><span class="sxs-lookup"><span data-stu-id="e4500-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4500-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e4500-111">Child Elements</span></span>  
  
|<span data-ttu-id="e4500-112">Element</span><span class="sxs-lookup"><span data-stu-id="e4500-112">Element</span></span>|<span data-ttu-id="e4500-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e4500-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4500-114">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="e4500-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="e4500-115">Zawiera kolekcję elementów punktu końcowego, określające punkty końcowe, które ten klient może nawiązać połączenia.</span><span class="sxs-lookup"><span data-stu-id="e4500-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="e4500-116">\<metadane ></span><span class="sxs-lookup"><span data-stu-id="e4500-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="e4500-117">Zawiera ustawienia dla przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="e4500-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4500-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e4500-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e4500-119">Element</span><span class="sxs-lookup"><span data-stu-id="e4500-119">Element</span></span>|<span data-ttu-id="e4500-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e4500-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4500-121">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e4500-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="e4500-122">Element główny wszystkich elementów konfiguracji systemu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e4500-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4500-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4500-123">Remarks</span></span>  
 <span data-ttu-id="e4500-124">`client` Sekcja definiuje listę punktów końcowych, które klient może nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="e4500-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="e4500-125">Każdy punkt końcowy wymienione w sekcji klienta definiuje własną powiązanie, zachowania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e4500-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="e4500-126">Jest unikatowo identyfikowana przez kombinację `name` i `contract` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e4500-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="e4500-127">Określa kod klienta `name` nawiązać połączenia z punktu końcowego usługi, który implementuje klienta.</span><span class="sxs-lookup"><span data-stu-id="e4500-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="e4500-128">Jeśli `name` atrybut nie jest określony, punkt końcowy działa jako domyślnego punktu końcowego dla kontraktu ją implementuje.</span><span class="sxs-lookup"><span data-stu-id="e4500-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="e4500-129">Ponadto w tej sekcji również określa ustawienia dla przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="e4500-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4500-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4500-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4500-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4500-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="e4500-132">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="e4500-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="e4500-133">Klienci</span><span class="sxs-lookup"><span data-stu-id="e4500-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
