---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855133"
---
# \<serviceActivations>

<span data-ttu-id="f186d-101">Element konfiguracji, który pozwala dodać ustawienia, które definiują ustawienia aktywacji usług wirtualnych, które są mapowane na typy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f186d-101">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="f186d-102">Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="f186d-102">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="f186d-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="f186d-103">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f186d-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f186d-104">Attributes and Elements</span></span>

<span data-ttu-id="f186d-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f186d-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f186d-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f186d-106">Attributes</span></span>

<span data-ttu-id="f186d-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="f186d-107">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f186d-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f186d-108">Child Elements</span></span>

|<span data-ttu-id="f186d-109">Element</span><span class="sxs-lookup"><span data-stu-id="f186d-109">Element</span></span>|<span data-ttu-id="f186d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f186d-110">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="f186d-111">Dodaje element konfiguracji, który określa aktywację aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f186d-111">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f186d-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f186d-112">Parent Elements</span></span>

|<span data-ttu-id="f186d-113">Element</span><span class="sxs-lookup"><span data-stu-id="f186d-113">Element</span></span>|<span data-ttu-id="f186d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f186d-114">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="f186d-115">Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.</span><span class="sxs-lookup"><span data-stu-id="f186d-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f186d-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f186d-116">Remarks</span></span>

<span data-ttu-id="f186d-117">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="f186d-117">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="f186d-118">Korzystając z tej konfiguracji, można aktywować GreetingService bez użycia pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="f186d-118">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="f186d-119">Należy pamiętać, że `<serviceHostingEnvironment>` jest to konfiguracja poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f186d-119">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="f186d-120">Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="f186d-120">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="f186d-121">Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="f186d-121">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="f186d-122">Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="f186d-122">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="f186d-123">Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http.</span><span class="sxs-lookup"><span data-stu-id="f186d-123">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="f186d-124">Wymaga rozszerzeń w relativeAddress (SVC, xoml lub. xamlx).</span><span class="sxs-lookup"><span data-stu-id="f186d-124">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="f186d-125">Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu.</span><span class="sxs-lookup"><span data-stu-id="f186d-125">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="f186d-126">W przypadku konfliktu `<serviceActivations>` sekcja zastępuje rejestracje SVC.</span><span class="sxs-lookup"><span data-stu-id="f186d-126">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="f186d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f186d-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
