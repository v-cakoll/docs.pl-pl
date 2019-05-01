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
ms.openlocfilehash: a1b189b79a02f04b7f795ff2524441f12b053cec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984636"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="6dcd2-102">ICLRMetaHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6dcd2-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="6dcd2-103">Udostępnia metody, które zwracają określonej wersji środowiska uruchomieniowego języka wspólnego (CLR) na podstawie jego numeru wersji, listę wszystkich zainstalowanych CLRs, listy wszystkie środowiska uruchomieniowe, które są ładowane w określonym procesie, odnajdź wersję środowiska CLR używane do kompilowania zestawu, Zakończ proces Zamknięcie czyste środowisko uruchomieniowe i powiązań dla zapytań dotyczących starszej wersji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6dcd2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6dcd2-104">Methods</span></span>  
  
|<span data-ttu-id="6dcd2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6dcd2-105">Method</span></span>|<span data-ttu-id="6dcd2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6dcd2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6dcd2-107">EnumerateInstalledRuntimes, metoda</span><span class="sxs-lookup"><span data-stu-id="6dcd2-107">EnumerateInstalledRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="6dcd2-108">Zwraca wyliczenie, które zawiera prawidłową [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdej wersji środowiska CLR, który jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="6dcd2-109">EnumerateLoadedRuntimes, metoda</span><span class="sxs-lookup"><span data-stu-id="6dcd2-109">EnumerateLoadedRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="6dcd2-110">Zwraca wyliczenie, które zawiera prawidłową [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdego środowiska CLR, który jest ładowany w danym procesie.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="6dcd2-111">Ta metoda zastępuje [getversionfromprocess —](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="6dcd2-111">This method supersedes [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="6dcd2-112">ExitProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="6dcd2-112">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|<span data-ttu-id="6dcd2-113">Próbuje zamknięcie wszystkie załadowane środowisk wykonawczych, a następnie kończy proces.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="6dcd2-114">Zastępuje [corexitprocess —](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-114">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="6dcd2-115">GetRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="6dcd2-115">GetRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|<span data-ttu-id="6dcd2-116">Pobiera [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który odnosi się do określonej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-116">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="6dcd2-117">Ta metoda zastępuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcja używana z [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flagi.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-117">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="6dcd2-118">GetVersionFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="6dcd2-118">GetVersionFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="6dcd2-119">Pobiera zestaw oryginalna wersja programu .NET Framework kompilacji (przechowywany w metadanych) podanej ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="6dcd2-120">Ta metoda zastępuje [getfileversion —](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="6dcd2-120">This method supersedes [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="6dcd2-121">QueryLegacyV2RuntimeBinding, metoda</span><span class="sxs-lookup"><span data-stu-id="6dcd2-121">QueryLegacyV2RuntimeBinding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="6dcd2-122">Zwraca interfejs, który reprezentuje środowiska uruchomieniowego, do którego zasady starszych aktywacji została powiązana, na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu na [ \<uruchamiania > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) wpis w pliku konfiguracji, przy użyciu bezpośredniego Aktywacja starszych interfejsów API lub przez wywołanie metody [iclrruntimeinfo::bindaslegacyv2runtime —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="6dcd2-123">RequestRuntimeLoadedNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="6dcd2-123">RequestRuntimeLoadedNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="6dcd2-124">Gwarantuje wywołanie zwrotne do wskaźnika określonej funkcji, gdy jest ładowana jako pierwsza wersja środowiska CLR, ale jeszcze nie rozpoczęty.</span><span class="sxs-lookup"><span data-stu-id="6dcd2-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="6dcd2-125">Ta metoda zastępuje [lockclrversion —](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="6dcd2-125">This method supersedes [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dcd2-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6dcd2-126">Remarks</span></span>  
 <span data-ttu-id="6dcd2-127">Jedynym sposobem, aby pobrać wystąpienie ten interfejs jest wywołanie [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6dcd2-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as follows:</span></span>  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6dcd2-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6dcd2-128">Requirements</span></span>  
 <span data-ttu-id="6dcd2-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dcd2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dcd2-130">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6dcd2-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6dcd2-131">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6dcd2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6dcd2-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dcd2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dcd2-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6dcd2-133">See also</span></span>

- [<span data-ttu-id="6dcd2-134">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6dcd2-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="6dcd2-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="6dcd2-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
