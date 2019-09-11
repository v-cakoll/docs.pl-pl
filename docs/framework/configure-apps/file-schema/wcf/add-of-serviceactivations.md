---
title: <add> dla <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850330"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="8f749-102">\<Dodaj >ę \<ServiceActivations ></span><span class="sxs-lookup"><span data-stu-id="8f749-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="8f749-103">Element konfiguracji, który pozwala zdefiniować ustawienia aktywacji usługi wirtualnej, które są mapowane na typy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8f749-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="8f749-104">Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="8f749-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="8f749-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8f749-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8f749-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8f749-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8f749-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="8f749-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="8f749-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceActivations**](serviceactivations.md)</span><span class="sxs-lookup"><span data-stu-id="8f749-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)</span></span>\
<span data-ttu-id="8f749-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="8f749-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="8f749-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f749-110">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f749-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8f749-111">Attributes and Elements</span></span>

<span data-ttu-id="8f749-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8f749-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f749-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8f749-113">Attributes</span></span>

|<span data-ttu-id="8f749-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8f749-114">Attribute</span></span>|<span data-ttu-id="8f749-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8f749-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="8f749-116">indywidual</span><span class="sxs-lookup"><span data-stu-id="8f749-116">factory</span></span>|<span data-ttu-id="8f749-117">Ciąg określający nazwę typu CLR fabryki, która generuje element aktywacji usługi.</span><span class="sxs-lookup"><span data-stu-id="8f749-117">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="8f749-118">usługa</span><span class="sxs-lookup"><span data-stu-id="8f749-118">service</span></span>|<span data-ttu-id="8f749-119">Typ, który implementuje usługę (pełna kwalifikowana nazwa typu lub krótki typ TypeName (gdy jest umieszczony w folderze App_Code).</span><span class="sxs-lookup"><span data-stu-id="8f749-119">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="8f749-120">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="8f749-120">relativeAddress</span></span>|<span data-ttu-id="8f749-121">Adres względny w bieżącej aplikacji usług IIS — na przykład "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="8f749-121">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="8f749-122">W programie WCF 4,0 ten adres względny musi zawierać jedno z znanych rozszerzeń plików (. svc,. xamlx,...). Brak pliku fizycznego dla relativeUrl</span><span class="sxs-lookup"><span data-stu-id="8f749-122">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8f749-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8f749-123">Child Elements</span></span>

<span data-ttu-id="8f749-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="8f749-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f749-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8f749-125">Parent Elements</span></span>

|<span data-ttu-id="8f749-126">Element</span><span class="sxs-lookup"><span data-stu-id="8f749-126">Element</span></span>|<span data-ttu-id="8f749-127">Opis</span><span class="sxs-lookup"><span data-stu-id="8f749-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f749-128">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="8f749-128">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="8f749-129">Sekcja konfiguracji opisująca ustawienia aktywacji.</span><span class="sxs-lookup"><span data-stu-id="8f749-129">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f749-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f749-130">Remarks</span></span>

<span data-ttu-id="8f749-131">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="8f749-131">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="8f749-132">Korzystając z tej konfiguracji, można aktywować GreetingService bez użycia pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="8f749-132">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="8f749-133">Należy pamiętać `<serviceHostingEnvironment>` , że jest to konfiguracja poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8f749-133">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="8f749-134">Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="8f749-134">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="8f749-135">Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="8f749-135">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="8f749-136">Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8f749-136">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="8f749-137">Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http.</span><span class="sxs-lookup"><span data-stu-id="8f749-137">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="8f749-138">Wymaga rozszerzeń w relativeAddress, tzn. svc, xoml lub. xamlx.</span><span class="sxs-lookup"><span data-stu-id="8f749-138">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="8f749-139">Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu.</span><span class="sxs-lookup"><span data-stu-id="8f749-139">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="8f749-140">W `<serviceActivations>` przypadku konfliktu sekcja zastępuje rejestracje SVC.</span><span class="sxs-lookup"><span data-stu-id="8f749-140">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f749-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f749-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
