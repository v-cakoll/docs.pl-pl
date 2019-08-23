---
title: <add> dla <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920030"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="6a17a-102">\<Dodaj >ę \<ServiceActivations ></span><span class="sxs-lookup"><span data-stu-id="6a17a-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="6a17a-103">Element konfiguracji, który pozwala zdefiniować ustawienia aktywacji usługi wirtualnej, które są mapowane na typy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6a17a-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="6a17a-104">Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="6a17a-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="6a17a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6a17a-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="6a17a-106">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="6a17a-106">\<serviceHostingEnvironment></span></span>

## <a name="syntax"></a><span data-ttu-id="6a17a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a17a-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a17a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a17a-108">Attributes and Elements</span></span>

<span data-ttu-id="6a17a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a17a-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a17a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a17a-110">Attributes</span></span>

|<span data-ttu-id="6a17a-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6a17a-111">Attribute</span></span>|<span data-ttu-id="6a17a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6a17a-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6a17a-113">indywidual</span><span class="sxs-lookup"><span data-stu-id="6a17a-113">factory</span></span>|<span data-ttu-id="6a17a-114">Ciąg określający nazwę typu CLR fabryki, która generuje element aktywacji usługi.</span><span class="sxs-lookup"><span data-stu-id="6a17a-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="6a17a-115">usługa</span><span class="sxs-lookup"><span data-stu-id="6a17a-115">service</span></span>|<span data-ttu-id="6a17a-116">Typ, który implementuje usługę (pełna kwalifikowana nazwa typu lub krótki typ TypeName (gdy jest umieszczony w folderze App_Code).</span><span class="sxs-lookup"><span data-stu-id="6a17a-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="6a17a-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="6a17a-117">relativeAddress</span></span>|<span data-ttu-id="6a17a-118">Adres względny w bieżącej aplikacji usług IIS — na przykład "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="6a17a-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="6a17a-119">W programie WCF 4,0 ten adres względny musi zawierać jedno z znanych rozszerzeń plików (. svc,. xamlx,...). Brak pliku fizycznego dla relativeUrl</span><span class="sxs-lookup"><span data-stu-id="6a17a-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6a17a-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a17a-120">Child Elements</span></span>

<span data-ttu-id="6a17a-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="6a17a-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a17a-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a17a-122">Parent Elements</span></span>

|<span data-ttu-id="6a17a-123">Element</span><span class="sxs-lookup"><span data-stu-id="6a17a-123">Element</span></span>|<span data-ttu-id="6a17a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="6a17a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a17a-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="6a17a-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="6a17a-126">Sekcja konfiguracji opisująca ustawienia aktywacji.</span><span class="sxs-lookup"><span data-stu-id="6a17a-126">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a17a-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a17a-127">Remarks</span></span>

<span data-ttu-id="6a17a-128">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="6a17a-128">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="6a17a-129">Korzystając z tej konfiguracji, można aktywować GreetingService bez użycia pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="6a17a-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="6a17a-130">Należy pamiętać `<serviceHostingEnvironment>` , że jest to konfiguracja poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6a17a-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="6a17a-131">Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="6a17a-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="6a17a-132">Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="6a17a-132">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="6a17a-133">Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="6a17a-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="6a17a-134">Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http.</span><span class="sxs-lookup"><span data-stu-id="6a17a-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="6a17a-135">Wymaga rozszerzeń w relativeAddress, tzn. svc, xoml lub. xamlx.</span><span class="sxs-lookup"><span data-stu-id="6a17a-135">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="6a17a-136">Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu.</span><span class="sxs-lookup"><span data-stu-id="6a17a-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="6a17a-137">W `<serviceActivations>` przypadku konfliktu sekcja zastępuje rejestracje SVC.</span><span class="sxs-lookup"><span data-stu-id="6a17a-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a17a-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a17a-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
