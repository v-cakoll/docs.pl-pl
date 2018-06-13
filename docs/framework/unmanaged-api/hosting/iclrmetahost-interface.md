---
title: ICLRMetaHost — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e4db5f3c7deb300a9666182cb6b712eacf42cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436231"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="0152d-102">ICLRMetaHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0152d-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="0152d-103">Udostępnia metody, które zwraca określoną wersję środowisko uruchomieniowe języka wspólnego (CLR) na podstawie jego numeru wersji, wyświetlić listę wszystkich zainstalowanych CLRs, listy wszystkich środowisk uruchomieniowych, które są ładowane w określonym procesie, wersji środowiska CLR, używanej do kompilacji zestawu, Zakończ proces odnajdywania Zamknięcie czyste środowiska uruchomieniowego i powiązań dla zapytań starszej wersji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="0152d-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0152d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0152d-104">Methods</span></span>  
  
|<span data-ttu-id="0152d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0152d-105">Method</span></span>|<span data-ttu-id="0152d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0152d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0152d-107">EnumerateInstalledRuntimes, metoda</span><span class="sxs-lookup"><span data-stu-id="0152d-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="0152d-108">Zwraca wyliczenie, który zawiera prawidłowy [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdej wersji środowiska CLR, który jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0152d-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="0152d-109">EnumerateLoadedRuntimes, metoda</span><span class="sxs-lookup"><span data-stu-id="0152d-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="0152d-110">Zwraca wyliczenie, który zawiera prawidłowy [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdego środowiska CLR, który jest ładowany w danym procesie.</span><span class="sxs-lookup"><span data-stu-id="0152d-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="0152d-111">Ta metoda zastępuje [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="0152d-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="0152d-112">ExitProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="0152d-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="0152d-113">Podejmuje próbę prawidłowe zamknięcie wszystkich załadowanych środowisk uruchomieniowych, a następnie kończy proces.</span><span class="sxs-lookup"><span data-stu-id="0152d-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="0152d-114">Zastępuje [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="0152d-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="0152d-115">GetRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="0152d-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="0152d-116">Pobiera [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu, który odpowiada określonej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0152d-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="0152d-117">Ta metoda zastępuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcja używana z [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flagi.</span><span class="sxs-lookup"><span data-stu-id="0152d-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="0152d-118">GetVersionFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="0152d-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="0152d-119">Pobiera zestawu oryginalna wersja programu .NET Framework kompilacji (przechowywane w metadanych) podanej ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="0152d-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="0152d-120">Ta metoda zastępuje [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="0152d-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="0152d-121">QueryLegacyV2RuntimeBinding, metoda</span><span class="sxs-lookup"><span data-stu-id="0152d-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="0152d-122">Zwraca interfejs, który reprezentuje runtime, do którego zasad aktywacji starszych wersji został powiązany, na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu [ \<uruchamiania > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) wpis pliku konfiguracji, używając bezpośredniego aktywacji starszych interfejsów API, przez wywołanie [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0152d-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="0152d-123">RequestRuntimeLoadedNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="0152d-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="0152d-124">Gwarantuje wywołania zwrotnego do wskaźnika funkcji określonej wersji środowiska CLR jest ładowana jako pierwsza, ale jeszcze nie uruchomiono.</span><span class="sxs-lookup"><span data-stu-id="0152d-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="0152d-125">Ta metoda zastępuje [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="0152d-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0152d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0152d-126">Remarks</span></span>  
 <span data-ttu-id="0152d-127">Jedynym sposobem na pobranie wystąpienia tego interfejsu jest wywołując [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) działają w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0152d-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0152d-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0152d-128">Requirements</span></span>  
 <span data-ttu-id="0152d-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0152d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0152d-130">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0152d-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0152d-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0152d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0152d-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0152d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0152d-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0152d-133">See Also</span></span>  
 [<span data-ttu-id="0152d-134">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0152d-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="0152d-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="0152d-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
