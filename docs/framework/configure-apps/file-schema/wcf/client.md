---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773944"
---
# <a name="client"></a><span data-ttu-id="b3f01-101">\<client ></span><span class="sxs-lookup"><span data-stu-id="b3f01-101">\<client></span></span>
<span data-ttu-id="b3f01-102">Element `client` definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="b3f01-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>

<span data-ttu-id="b3f01-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b3f01-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b3f01-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b3f01-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b3f01-105">&nbsp; &nbsp; &nbsp; &nbsp; **\<client >**</span><span class="sxs-lookup"><span data-stu-id="b3f01-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b3f01-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3f01-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b3f01-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b3f01-107">Attributes and Elements</span></span>
 <span data-ttu-id="b3f01-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b3f01-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b3f01-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3f01-109">Attributes</span></span>
 <span data-ttu-id="b3f01-110">Brak</span><span class="sxs-lookup"><span data-stu-id="b3f01-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b3f01-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b3f01-111">Child Elements</span></span>

|<span data-ttu-id="b3f01-112">Element</span><span class="sxs-lookup"><span data-stu-id="b3f01-112">Element</span></span>|<span data-ttu-id="b3f01-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b3f01-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3f01-114">\<endpoint ></span><span class="sxs-lookup"><span data-stu-id="b3f01-114">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="b3f01-115">Zawiera kolekcję elementów punktu końcowego, które określają punkty końcowe, z którymi ten klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="b3f01-115">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[<span data-ttu-id="b3f01-116">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="b3f01-116">\<metadata></span></span>](metadata.md)|<span data-ttu-id="b3f01-117">Zawiera ustawienia dotyczące przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="b3f01-117">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b3f01-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b3f01-118">Parent Elements</span></span>

|<span data-ttu-id="b3f01-119">Element</span><span class="sxs-lookup"><span data-stu-id="b3f01-119">Element</span></span>|<span data-ttu-id="b3f01-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b3f01-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3f01-121">\<system. serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b3f01-121">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="b3f01-122">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b3f01-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b3f01-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3f01-123">Remarks</span></span>
 <span data-ttu-id="b3f01-124">Sekcja `client` definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="b3f01-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="b3f01-125">Każdy punkt końcowy wymieniony w sekcji Client definiuje własne powiązanie, zachowanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="b3f01-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="b3f01-126">Jest on jednoznacznie identyfikowany przez kombinację atrybutów `name` i `contract`.</span><span class="sxs-lookup"><span data-stu-id="b3f01-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="b3f01-127">Kod klienta określa `name`, aby połączyć się z punktem końcowym dla usługi implementującej przez klienta.</span><span class="sxs-lookup"><span data-stu-id="b3f01-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="b3f01-128">Jeśli atrybut `name` zostanie pominięty, punkt końcowy działa jako domyślny punkt końcowy dla wdrażanego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b3f01-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="b3f01-129">Ponadto ta sekcja określa również ustawienia przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="b3f01-129">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="b3f01-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3f01-130">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b3f01-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3f01-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="b3f01-132">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="b3f01-132">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="b3f01-133">Klienci</span><span class="sxs-lookup"><span data-stu-id="b3f01-133">Clients</span></span>](../../../wcf/feature-details/clients.md)
