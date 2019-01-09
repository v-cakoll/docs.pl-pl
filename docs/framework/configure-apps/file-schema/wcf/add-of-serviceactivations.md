---
title: '&lt;add&gt; w &lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: b40127d531926f103f3e367c8721e8f5ff8e1a99
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151543"
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="73fb2-102">&lt;add&gt; w &lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="73fb2-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="73fb2-103">Element konfiguracji, który pozwala zdefiniować ustawienia Aktywacja usług wirtualnych mapowane odpowiadają typom usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="73fb2-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="73fb2-104">Dzięki temu można aktywować usługi hostowane w WAS / IIS bez pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="73fb2-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="73fb2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="73fb2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="73fb2-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="73fb2-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fb2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="73fb2-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73fb2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="73fb2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="73fb2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="73fb2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73fb2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="73fb2-110">Attributes</span></span>  
  
|<span data-ttu-id="73fb2-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="73fb2-111">Attribute</span></span>|<span data-ttu-id="73fb2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="73fb2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73fb2-113">Fabryka</span><span class="sxs-lookup"><span data-stu-id="73fb2-113">factory</span></span>|<span data-ttu-id="73fb2-114">Ciąg, który określa nazwę typu CLR fabryki, która generuje element aktywacji usługi.</span><span class="sxs-lookup"><span data-stu-id="73fb2-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="73fb2-115">usługa</span><span class="sxs-lookup"><span data-stu-id="73fb2-115">service</span></span>|<span data-ttu-id="73fb2-116">Typ ServiceType, który implementuje usługę (pełna kwalifikowana nazwa typu lub krótki Typename (jeśli znajduje się w folderze App_Code).</span><span class="sxs-lookup"><span data-stu-id="73fb2-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="73fb2-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="73fb2-117">relativeAddress</span></span>|<span data-ttu-id="73fb2-118">Adres względny w bieżącej aplikacji usług IIS — na przykład "Service.svc".</span><span class="sxs-lookup"><span data-stu-id="73fb2-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="73fb2-119">W wersji 4.0 WCF tego adresu względnego musi zawierać rozszerzenia znanych plików (.svc .xamlx...). Nie pliku fizycznego musi istnieć dla relativeUrl</span><span class="sxs-lookup"><span data-stu-id="73fb2-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73fb2-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="73fb2-120">Child Elements</span></span>  
 <span data-ttu-id="73fb2-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="73fb2-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73fb2-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="73fb2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73fb2-123">Element</span><span class="sxs-lookup"><span data-stu-id="73fb2-123">Element</span></span>|<span data-ttu-id="73fb2-124">Opis</span><span class="sxs-lookup"><span data-stu-id="73fb2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73fb2-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="73fb2-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="73fb2-126">Sekcja konfiguracji, który opisuje ustawienia aktywacji.</span><span class="sxs-lookup"><span data-stu-id="73fb2-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73fb2-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73fb2-127">Remarks</span></span>  
 <span data-ttu-id="73fb2-128">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="73fb2-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="73fb2-129">Za pomocą tej konfiguracji, możesz aktywować GreetingService bez użycia pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="73fb2-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="73fb2-130">Należy pamiętać, że `<serviceHostingEnvironment>` jest konfiguracji na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="73fb2-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="73fb2-131">Musisz umieszczać `web.config` zawierający konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="73fb2-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="73fb2-132">Ponadto `serviceHostingEnvironment` to sekcja dziedziczne machinetoApplication.</span><span class="sxs-lookup"><span data-stu-id="73fb2-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="73fb2-133">Jeśli zarejestrujesz jednej usługi w katalogu głównym maszyny do każdej usługi w aplikacji będą dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="73fb2-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="73fb2-134">Aktywacja oparta na konfiguracji obsługuje aktywacji za pośrednictwem protokołu http i innych niż http.</span><span class="sxs-lookup"><span data-stu-id="73fb2-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="73fb2-135">Wymaga rozszerzenia w relatativeAddress, czyli .svc xoml oraz .xamlx.</span><span class="sxs-lookup"><span data-stu-id="73fb2-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="73fb2-136">Własne rozszerzenia można zamapować na buildProviders wie, który następnie umożliwi Aktywuj usługę za pośrednictwem dowolnego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="73fb2-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="73fb2-137">Po konfliktu `<serviceActivations>` sekcji zastępuje .svc rejestracji.</span><span class="sxs-lookup"><span data-stu-id="73fb2-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fb2-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73fb2-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
