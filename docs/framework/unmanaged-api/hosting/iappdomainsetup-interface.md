---
title: IAppDomainSetup — Interfejs
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126871"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="e4ea1-102">IAppDomainSetup — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e4ea1-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="e4ea1-103">Udostępnia właściwości, które umożliwiają hostowi skonfigurowanie typu <xref:System.AppDomain?displayProperty=nameWithType> przed wywołaniem metody [ICorRuntimeHost:: CreateDomainEx —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) , aby ją utworzyć.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e4ea1-104">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e4ea1-104">Properties</span></span>  
  
|<span data-ttu-id="e4ea1-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="e4ea1-105">Property</span></span>|<span data-ttu-id="e4ea1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e4ea1-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="e4ea1-107">Pobiera lub ustawia nazwę katalogu, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="e4ea1-108">Pobiera lub ustawia nazwę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="e4ea1-109">Pobiera lub ustawia nazwę obszaru określonego dla aplikacji, w której pliki są kopiowane w tle.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="e4ea1-110">Pobiera lub ustawia nazwę pliku konfiguracji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="e4ea1-111">Pobiera lub ustawia nazwę katalogu, w którym są przechowywane i dostępne dynamicznie generowane pliki.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="e4ea1-112">Pobiera lub ustawia ścieżkę do pliku licencji skojarzonego z tą domeną.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="e4ea1-113">Pobiera lub ustawia listę katalogów połączonych z katalogiem <xref:System.AppDomainSetup.ApplicationBase%2A> w celu sondowania zestawów prywatnych.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="e4ea1-114">Pobiera lub ustawia wartość ciągu, która zawiera lub wyklucza <xref:System.AppDomainSetup.ApplicationBase%2A> ze ścieżki wyszukiwania dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="e4ea1-115">Pobiera lub ustawia nazwy katalogów, które zawierają zestawy przeznaczone do kopiowania w tle.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="e4ea1-116">Pobiera lub ustawia ciąg, który wskazuje, czy kopiowanie w tle jest włączone czy wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="e4ea1-117">Prawidłowe wartości to "true" lub "false".</span><span class="sxs-lookup"><span data-stu-id="e4ea1-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4ea1-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4ea1-118">Remarks</span></span>  
 <span data-ttu-id="e4ea1-119">Interfejs `IAppDomainSetup` odpowiada interfejsowi zarządzanemu <xref:System.IAppDomainSetup>, który implementuje typ <xref:System.AppDomainSetup>.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="e4ea1-120">Zobacz <xref:System.IAppDomainSetup?displayProperty=nameWithType>, aby uzyskać szczegółowe opisy jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="e4ea1-121">`IAppDomainSetup` reprezentuje informacje o powiązaniu zestawu, które można dodać do wystąpienia <xref:System.AppDomain> przed jego utworzeniem.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="e4ea1-122">Na przykład host może ustawić właściwość <xref:System.AppDomainSetup.ApplicationBase%2A>, aby ustanowić katalog główny, który sond środowiska uruchomieniowego języka wspólnego (CLR) dla zestawów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="e4ea1-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4ea1-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4ea1-123">Requirements</span></span>  
 <span data-ttu-id="e4ea1-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4ea1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4ea1-125">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4ea1-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4ea1-126">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4ea1-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4ea1-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4ea1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ea1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4ea1-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="e4ea1-129">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e4ea1-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
