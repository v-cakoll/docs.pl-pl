---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 6cc8b80edb3206bb2ef3a8a1ffa34ab40af77612
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398151"
---
# <a name="client"></a><span data-ttu-id="6f807-101">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="6f807-101">\<client></span></span>
<span data-ttu-id="6f807-102">`client` Element definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="6f807-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
<span data-ttu-id="6f807-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f807-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6f807-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6f807-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6f807-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> klienta**</span><span class="sxs-lookup"><span data-stu-id="6f807-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f807-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f807-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f807-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6f807-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6f807-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6f807-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f807-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6f807-109">Attributes</span></span>  
 <span data-ttu-id="6f807-110">Brak</span><span class="sxs-lookup"><span data-stu-id="6f807-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f807-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6f807-111">Child Elements</span></span>  
  
|<span data-ttu-id="6f807-112">Element</span><span class="sxs-lookup"><span data-stu-id="6f807-112">Element</span></span>|<span data-ttu-id="6f807-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6f807-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f807-114">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="6f807-114">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="6f807-115">Zawiera kolekcję elementów punktu końcowego, które określają punkty końcowe, z którymi ten klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="6f807-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="6f807-116">\<> metadanych</span><span class="sxs-lookup"><span data-stu-id="6f807-116">\<metadata></span></span>](metadata.md)|<span data-ttu-id="6f807-117">Zawiera ustawienia dotyczące przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="6f807-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f807-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6f807-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6f807-119">Element</span><span class="sxs-lookup"><span data-stu-id="6f807-119">Element</span></span>|<span data-ttu-id="6f807-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6f807-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f807-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6f807-121">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="6f807-122">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6f807-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f807-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f807-123">Remarks</span></span>  
 <span data-ttu-id="6f807-124">`client` Sekcja definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="6f807-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="6f807-125">Każdy punkt końcowy wymieniony w sekcji Client definiuje własne powiązanie, zachowanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="6f807-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="6f807-126">Jest unikatowo identyfikowana przez kombinację `name` atrybutów i. `contract`</span><span class="sxs-lookup"><span data-stu-id="6f807-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="6f807-127">Kod klienta określa, `name` aby połączyć się z punktem końcowym usługi, którą implementuje klient.</span><span class="sxs-lookup"><span data-stu-id="6f807-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="6f807-128">`name` Jeśli atrybut zostanie pominięty, punkt końcowy działa jako domyślny punkt końcowy dla wdrażanego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6f807-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="6f807-129">Ponadto ta sekcja określa również ustawienia przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="6f807-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f807-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="6f807-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f807-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f807-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="6f807-132">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="6f807-132">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="6f807-133">Klienci</span><span class="sxs-lookup"><span data-stu-id="6f807-133">Clients</span></span>](../../../wcf/feature-details/clients.md)
