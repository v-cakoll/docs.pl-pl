---
title: Aktywacja oparta na konfiguracji w usługach IIS i WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 6515d6621798a9dab67aa7b73a39b9481c1779fc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963481"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="ecea4-102">Aktywacja oparta na konfiguracji w usługach IIS i WAS</span><span class="sxs-lookup"><span data-stu-id="ecea4-102">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="ecea4-103">Zwykle podczas hostowania usługi Windows Communication Foundation (WCF) w ramach Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS) należy podać plik SVC.</span><span class="sxs-lookup"><span data-stu-id="ecea4-103">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="ecea4-104">Plik SVC zawiera nazwę usługi i opcjonalną fabrykę hosta usługi niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="ecea4-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="ecea4-105">Ten dodatkowy plik dodaje obciążenie związane z zarządzaniem.</span><span class="sxs-lookup"><span data-stu-id="ecea4-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="ecea4-106">Funkcja aktywacji opartej na konfiguracji eliminuje konieczność posiadania pliku svc i dlatego skojarzone obciążenie.</span><span class="sxs-lookup"><span data-stu-id="ecea4-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="ecea4-107">Aktywacja oparta na konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ecea4-107">Configuration-Based Activation</span></span>

<span data-ttu-id="ecea4-108">Aktywacja oparta na konfiguracji pobiera metadane, które były używane do umieszczania w pliku svc i umieszcza je w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="ecea4-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="ecea4-109">W <`serviceHostingEnvironment`> element <`serviceActivations`>.</span><span class="sxs-lookup"><span data-stu-id="ecea4-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="ecea4-110">W <`serviceActivations`> element to co najmniej jeden <`add`> elementów, po jednym dla każdej usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="ecea4-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="ecea4-111">Element <`add`> zawiera atrybuty pozwalające ustawić adres względny dla usługi i typu usługi lub fabryki hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="ecea4-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="ecea4-112">Poniższy przykładowy kod konfiguracji pokazuje, w jaki sposób ta sekcja jest używana.</span><span class="sxs-lookup"><span data-stu-id="ecea4-112">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
> <span data-ttu-id="ecea4-113">Każdy <`add`> element musi określać usługę lub atrybut fabryki.</span><span class="sxs-lookup"><span data-stu-id="ecea4-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="ecea4-114">Określanie atrybutów Service i Factory jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="ecea4-114">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="ecea4-115">Za pomocą tego elementu w pliku Web. config można umieścić kod źródłowy usługi w katalogu App_Code aplikacji lub zgodnego zestawu w katalogu bin aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecea4-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="ecea4-116">W przypadku korzystania z aktywacji opartej na konfiguracji, kod wbudowany w plikach. svc nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="ecea4-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="ecea4-117">Atrybut `relativeAddress` musi być ustawiony na adres względny, taki jak "\<subdirectory >/Service.svc" lub "~/\<sub-Directory/Service. svc".</span><span class="sxs-lookup"><span data-stu-id="ecea4-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="ecea4-118">Wyjątek konfiguracji jest zgłaszany w przypadku zarejestrowania adresu względnego, który nie ma znanego rozszerzenia skojarzonego z WCF.</span><span class="sxs-lookup"><span data-stu-id="ecea4-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="ecea4-119">Określony adres względny jest względny w stosunku do elementu głównego aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="ecea4-119">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="ecea4-120">Ze względu na hierarchiczny model konfiguracji, zarejestrowane adresy względne na poziomie komputera i lokacji są dziedziczone przez aplikacje wirtualne.</span><span class="sxs-lookup"><span data-stu-id="ecea4-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="ecea4-121">Rejestracje w pliku konfiguracji mają pierwszeństwo przed ustawieniami w pliku SVC, xamlx, xoml lub innym.</span><span class="sxs-lookup"><span data-stu-id="ecea4-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="ecea4-122">Wszystkie znaki "\" (ukośniki odwrotne) w identyfikatorze URI wysłanym do usług IIS/były automatycznie konwertowane na znak "/" (ukośnik).</span><span class="sxs-lookup"><span data-stu-id="ecea4-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="ecea4-123">Jeśli zostanie dodany adres względny, który zawiera znak "\", a w usługach IIS zostanie wysłany identyfikator URI, który używa adresu względnego, ukośnik odwrotny jest konwertowany na ukośnik, a usługi IIS nie będą zgodne z adresem względnym.</span><span class="sxs-lookup"><span data-stu-id="ecea4-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="ecea4-124">Program IIS wysyła informacje śledzenia, które wskazują, że nie znaleziono dopasowań.</span><span class="sxs-lookup"><span data-stu-id="ecea4-124">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecea4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecea4-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="ecea4-126">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="ecea4-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="ecea4-127">Przegląd hostowania usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ecea4-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [<span data-ttu-id="ecea4-128">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="ecea4-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- <span data-ttu-id="ecea4-129">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ecea4-129">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
