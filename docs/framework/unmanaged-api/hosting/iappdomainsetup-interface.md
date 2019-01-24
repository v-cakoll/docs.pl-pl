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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef967039450c77b5927d501de63d53a245c90be0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509834"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="762d3-102">IAppDomainSetup — Interfejs</span><span class="sxs-lookup"><span data-stu-id="762d3-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="762d3-103">Udostępnia właściwości umożliwiające hosta skonfigurować <xref:System.AppDomain?displayProperty=nameWithType> typ przed wywołaniem [icorruntimehost::createdomainex —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metodę, aby go utworzyć.</span><span class="sxs-lookup"><span data-stu-id="762d3-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="762d3-104">Właściwości</span><span class="sxs-lookup"><span data-stu-id="762d3-104">Properties</span></span>  
  
|<span data-ttu-id="762d3-105">Właściwość</span><span class="sxs-lookup"><span data-stu-id="762d3-105">Property</span></span>|<span data-ttu-id="762d3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="762d3-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="762d3-107">Pobiera lub ustawia nazwę katalogu, który zawiera aplikację.</span><span class="sxs-lookup"><span data-stu-id="762d3-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="762d3-108">Pobiera lub ustawia nazwę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="762d3-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="762d3-109">Pobiera lub ustawia nazwę obszaru określonych aplikacji której pliki są kopiowane w tle.</span><span class="sxs-lookup"><span data-stu-id="762d3-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="762d3-110">Pobiera lub ustawia nazwę pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="762d3-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="762d3-111">Pobiera lub ustawia nazwę katalogu, gdzie przechowywane dynamicznie generowanych plików i dostępne.</span><span class="sxs-lookup"><span data-stu-id="762d3-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="762d3-112">Pobiera lub ustawia ścieżkę do pliku licencji, który jest skojarzony z tą domeną.</span><span class="sxs-lookup"><span data-stu-id="762d3-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="762d3-113">Pobiera lub ustawia listę katalogów w połączeniu z <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu, aby sondować zestawy prywatne.</span><span class="sxs-lookup"><span data-stu-id="762d3-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="762d3-114">Pobiera lub ustawia wartość ciągu, która obejmuje lub wyklucza <xref:System.AppDomainSetup.ApplicationBase%2A> ze ścieżki wyszukiwania dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="762d3-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="762d3-115">Pobiera lub ustawia nazwy katalogów, które zawierają zestawy być kopiowane w tle.</span><span class="sxs-lookup"><span data-stu-id="762d3-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="762d3-116">Pobiera lub ustawia ciąg, który wskazuje, czy kopiowanie w tle jest włączony lub wyłączony.</span><span class="sxs-lookup"><span data-stu-id="762d3-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="762d3-117">Prawidłowe wartości to "true" lub "false".</span><span class="sxs-lookup"><span data-stu-id="762d3-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="762d3-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="762d3-118">Remarks</span></span>  
 <span data-ttu-id="762d3-119">`IAppDomainSetup` Interfejsu odnosi się do zarządzanej <xref:System.IAppDomainSetup> interfejsu, który <xref:System.AppDomainSetup> typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="762d3-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="762d3-120">Zobacz <xref:System.IAppDomainSetup?displayProperty=nameWithType> szczegółowe opisy jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="762d3-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="762d3-121">`IAppDomainSetup` przedstawia informacje o powiązań zestawów, które mogą być dodawane do <xref:System.AppDomain> wystąpienia przed jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="762d3-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="762d3-122">Na przykład można ustawić hosta <xref:System.AppDomainSetup.ApplicationBase%2A> zarządzane zestawy, właściwość, aby ustanowić katalogu głównego sondy środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="762d3-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="762d3-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="762d3-123">Requirements</span></span>  
 <span data-ttu-id="762d3-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="762d3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="762d3-125">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="762d3-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="762d3-126">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="762d3-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="762d3-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="762d3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762d3-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="762d3-128">See also</span></span>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="762d3-129">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="762d3-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
