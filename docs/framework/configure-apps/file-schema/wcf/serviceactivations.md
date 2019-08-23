---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936446"
---
# <a name="serviceactivations"></a><span data-ttu-id="ae988-101">\<> ServiceActivations</span><span class="sxs-lookup"><span data-stu-id="ae988-101">\<serviceActivations></span></span>

<span data-ttu-id="ae988-102">Element konfiguracji, który pozwala dodać ustawienia, które definiują ustawienia aktywacji usług wirtualnych, które są mapowane na typy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ae988-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="ae988-103">Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="ae988-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="ae988-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ae988-104">\<system.ServiceModel></span></span>\
<span data-ttu-id="ae988-105">\<serviceHostingEnvironment > </span><span class="sxs-lookup"><span data-stu-id="ae988-105">\<serviceHostingEnvironment></span></span>\
<span data-ttu-id="ae988-106">\<> ServiceActivations</span><span class="sxs-lookup"><span data-stu-id="ae988-106">\<serviceActivations></span></span>

## <a name="syntax"></a><span data-ttu-id="ae988-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae988-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae988-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ae988-108">Attributes and Elements</span></span>

<span data-ttu-id="ae988-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ae988-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae988-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ae988-110">Attributes</span></span>

<span data-ttu-id="ae988-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="ae988-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae988-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ae988-112">Child Elements</span></span>

|<span data-ttu-id="ae988-113">Element</span><span class="sxs-lookup"><span data-stu-id="ae988-113">Element</span></span>|<span data-ttu-id="ae988-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ae988-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae988-115">\<add></span><span class="sxs-lookup"><span data-stu-id="ae988-115">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="ae988-116">Dodaje element konfiguracji, który określa aktywację aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="ae988-116">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ae988-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ae988-117">Parent Elements</span></span>

|<span data-ttu-id="ae988-118">Element</span><span class="sxs-lookup"><span data-stu-id="ae988-118">Element</span></span>|<span data-ttu-id="ae988-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ae988-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae988-120">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="ae988-120">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="ae988-121">Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="ae988-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ae988-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae988-122">Remarks</span></span>

<span data-ttu-id="ae988-123">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="ae988-123">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="ae988-124">Korzystając z tej konfiguracji, można aktywować GreetingService bez użycia pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="ae988-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="ae988-125">Należy pamiętać `<serviceHostingEnvironment>` , że jest to konfiguracja poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae988-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="ae988-126">Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="ae988-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="ae988-127">Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="ae988-127">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="ae988-128">Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="ae988-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="ae988-129">Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http.</span><span class="sxs-lookup"><span data-stu-id="ae988-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="ae988-130">Wymaga rozszerzeń w relativeAddress (SVC, xoml lub. xamlx).</span><span class="sxs-lookup"><span data-stu-id="ae988-130">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="ae988-131">Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu.</span><span class="sxs-lookup"><span data-stu-id="ae988-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="ae988-132">W `<serviceActivations>` przypadku konfliktu sekcja zastępuje rejestracje SVC.</span><span class="sxs-lookup"><span data-stu-id="ae988-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae988-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae988-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
