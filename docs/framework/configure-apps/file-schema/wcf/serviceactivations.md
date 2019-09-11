---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855133"
---
# <a name="serviceactivations"></a><span data-ttu-id="6fbaa-101">\<> ServiceActivations</span><span class="sxs-lookup"><span data-stu-id="6fbaa-101">\<serviceActivations></span></span>

<span data-ttu-id="6fbaa-102">Element konfiguracji, który pozwala dodać ustawienia, które definiują ustawienia aktywacji usług wirtualnych, które są mapowane na typy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6fbaa-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="6fbaa-103">Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="6fbaa-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6fbaa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6fbaa-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6fbaa-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6fbaa-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="6fbaa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="6fbaa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> ServiceActivations**</span><span class="sxs-lookup"><span data-stu-id="6fbaa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6fbaa-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fbaa-108">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6fbaa-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6fbaa-109">Attributes and Elements</span></span>

<span data-ttu-id="6fbaa-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6fbaa-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6fbaa-111">Attributes</span></span>

<span data-ttu-id="6fbaa-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6fbaa-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6fbaa-113">Child Elements</span></span>

|<span data-ttu-id="6fbaa-114">Element</span><span class="sxs-lookup"><span data-stu-id="6fbaa-114">Element</span></span>|<span data-ttu-id="6fbaa-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6fbaa-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6fbaa-116">\<add></span><span class="sxs-lookup"><span data-stu-id="6fbaa-116">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="6fbaa-117">Dodaje element konfiguracji, który określa aktywację aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-117">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6fbaa-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6fbaa-118">Parent Elements</span></span>

|<span data-ttu-id="6fbaa-119">Element</span><span class="sxs-lookup"><span data-stu-id="6fbaa-119">Element</span></span>|<span data-ttu-id="6fbaa-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6fbaa-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6fbaa-121">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="6fbaa-121">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="6fbaa-122">Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6fbaa-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fbaa-123">Remarks</span></span>

<span data-ttu-id="6fbaa-124">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-124">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="6fbaa-125">Korzystając z tej konfiguracji, można aktywować GreetingService bez użycia pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="6fbaa-126">Należy pamiętać `<serviceHostingEnvironment>` , że jest to konfiguracja poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="6fbaa-127">Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="6fbaa-128">Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-128">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="6fbaa-129">Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="6fbaa-130">Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="6fbaa-131">Wymaga rozszerzeń w relativeAddress (SVC, xoml lub. xamlx).</span><span class="sxs-lookup"><span data-stu-id="6fbaa-131">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="6fbaa-132">Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="6fbaa-133">W `<serviceActivations>` przypadku konfliktu sekcja zastępuje rejestracje SVC.</span><span class="sxs-lookup"><span data-stu-id="6fbaa-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fbaa-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fbaa-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
