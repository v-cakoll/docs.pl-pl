---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "72773944"
---
# \<client>
<span data-ttu-id="c5190-101">`client`Element definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="c5190-101">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="c5190-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5190-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c5190-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c5190-103">Attributes and Elements</span></span>
 <span data-ttu-id="c5190-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5190-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5190-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c5190-105">Attributes</span></span>
 <span data-ttu-id="c5190-106">Brak</span><span class="sxs-lookup"><span data-stu-id="c5190-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5190-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c5190-107">Child Elements</span></span>

|<span data-ttu-id="c5190-108">Element</span><span class="sxs-lookup"><span data-stu-id="c5190-108">Element</span></span>|<span data-ttu-id="c5190-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c5190-109">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="c5190-110">Zawiera kolekcję elementów punktu końcowego, które określają punkty końcowe, z którymi ten klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="c5190-110">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="c5190-111">Zawiera ustawienia dotyczące przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="c5190-111">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c5190-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c5190-112">Parent Elements</span></span>

|<span data-ttu-id="c5190-113">Element</span><span class="sxs-lookup"><span data-stu-id="c5190-113">Element</span></span>|<span data-ttu-id="c5190-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c5190-114">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="c5190-115">Element główny wszystkich elementów konfiguracji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c5190-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c5190-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5190-116">Remarks</span></span>
 <span data-ttu-id="c5190-117">`client`Sekcja definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="c5190-117">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="c5190-118">Każdy punkt końcowy wymieniony w sekcji Client definiuje własne powiązanie, zachowanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="c5190-118">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="c5190-119">Jest unikatowo identyfikowana przez kombinację `name` atrybutów i `contract` .</span><span class="sxs-lookup"><span data-stu-id="c5190-119">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="c5190-120">Kod klienta określa, `name` Aby połączyć się z punktem końcowym usługi, którą implementuje klient.</span><span class="sxs-lookup"><span data-stu-id="c5190-120">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="c5190-121">Jeśli `name` atrybut zostanie pominięty, punkt końcowy działa jako domyślny punkt końcowy dla wdrażanego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c5190-121">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="c5190-122">Ponadto ta sekcja określa również ustawienia przetwarzania metadanych.</span><span class="sxs-lookup"><span data-stu-id="c5190-122">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="c5190-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5190-123">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c5190-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5190-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="c5190-125">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="c5190-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c5190-126">Klienci</span><span class="sxs-lookup"><span data-stu-id="c5190-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
