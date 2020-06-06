---
title: <add> dla <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850330"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="8aa07-102">\<add> dla \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="8aa07-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="8aa07-103">Element konfiguracji, który pozwala zdefiniować ustawienia aktywacji usługi wirtualnej, które są mapowane na typy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8aa07-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="8aa07-104">Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="8aa07-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="8aa07-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8aa07-105">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8aa07-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8aa07-106">Attributes and Elements</span></span>

<span data-ttu-id="8aa07-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8aa07-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8aa07-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8aa07-108">Attributes</span></span>

|<span data-ttu-id="8aa07-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8aa07-109">Attribute</span></span>|<span data-ttu-id="8aa07-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8aa07-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="8aa07-111">indywidual</span><span class="sxs-lookup"><span data-stu-id="8aa07-111">factory</span></span>|<span data-ttu-id="8aa07-112">Ciąg określający nazwę typu CLR fabryki, która generuje element aktywacji usługi.</span><span class="sxs-lookup"><span data-stu-id="8aa07-112">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="8aa07-113">usługa</span><span class="sxs-lookup"><span data-stu-id="8aa07-113">service</span></span>|<span data-ttu-id="8aa07-114">Typ ServiceType implementujący usługę (pełna kwalifikowana nazwa typu lub krótki typ TypeName (gdy jest umieszczony w folderze App_Code).</span><span class="sxs-lookup"><span data-stu-id="8aa07-114">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="8aa07-115">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="8aa07-115">relativeAddress</span></span>|<span data-ttu-id="8aa07-116">Adres względny w bieżącej aplikacji usług IIS — na przykład "Service. svc".</span><span class="sxs-lookup"><span data-stu-id="8aa07-116">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="8aa07-117">W programie WCF 4,0 ten adres względny musi zawierać jedno z znanych rozszerzeń plików (. svc,. xamlx,...). Brak pliku fizycznego dla relativeUrl</span><span class="sxs-lookup"><span data-stu-id="8aa07-117">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8aa07-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8aa07-118">Child Elements</span></span>

<span data-ttu-id="8aa07-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="8aa07-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8aa07-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8aa07-120">Parent Elements</span></span>

|<span data-ttu-id="8aa07-121">Element</span><span class="sxs-lookup"><span data-stu-id="8aa07-121">Element</span></span>|<span data-ttu-id="8aa07-122">Opis</span><span class="sxs-lookup"><span data-stu-id="8aa07-122">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="8aa07-123">Sekcja konfiguracji opisująca ustawienia aktywacji.</span><span class="sxs-lookup"><span data-stu-id="8aa07-123">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8aa07-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8aa07-124">Remarks</span></span>

<span data-ttu-id="8aa07-125">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="8aa07-125">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="8aa07-126">Korzystając z tej konfiguracji, można aktywować GreetingService bez użycia pliku SVC.</span><span class="sxs-lookup"><span data-stu-id="8aa07-126">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="8aa07-127">Należy pamiętać, że `<serviceHostingEnvironment>` jest to konfiguracja poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8aa07-127">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="8aa07-128">Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="8aa07-128">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="8aa07-129">Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication.</span><span class="sxs-lookup"><span data-stu-id="8aa07-129">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="8aa07-130">Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8aa07-130">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="8aa07-131">Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http.</span><span class="sxs-lookup"><span data-stu-id="8aa07-131">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="8aa07-132">Wymaga rozszerzeń w relativeAddress, tzn. svc, xoml lub. xamlx.</span><span class="sxs-lookup"><span data-stu-id="8aa07-132">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="8aa07-133">Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu.</span><span class="sxs-lookup"><span data-stu-id="8aa07-133">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="8aa07-134">W przypadku konfliktu `<serviceActivations>` sekcja zastępuje rejestracje SVC.</span><span class="sxs-lookup"><span data-stu-id="8aa07-134">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="8aa07-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8aa07-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
