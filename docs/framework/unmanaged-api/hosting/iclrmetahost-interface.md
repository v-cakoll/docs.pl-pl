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
ms.openlocfilehash: bb7c3659930f308328cba121c06a88cb6a95eb26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504163"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="0953f-102">ICLRMetaHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0953f-102">ICLRMetaHost Interface</span></span>
<span data-ttu-id="0953f-103">Dostarcza metody, które zwracają określoną wersję środowiska uruchomieniowego języka wspólnego (CLR) na podstawie jego numeru wersji, wyświetla listę wszystkich zainstalowanych CLRs, wyświetla wszystkie środowiska uruchomieniowe, które są ładowane w określonym procesie, wykrywają wersję środowiska CLR używaną do kompilowania zestawu, opuszczają proces z zamknięciem czystego środowiska uruchomieniowego i powiążą się z kwerendą ze starszej wersji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="0953f-103">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0953f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0953f-104">Methods</span></span>  
  
|<span data-ttu-id="0953f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0953f-105">Method</span></span>|<span data-ttu-id="0953f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0953f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0953f-107">EnumerateInstalledRuntimes, metoda</span><span class="sxs-lookup"><span data-stu-id="0953f-107">EnumerateInstalledRuntimes Method</span></span>](iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="0953f-108">Zwraca Wyliczenie, które zawiera prawidłowy wskaźnik interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) dla każdej wersji środowiska CLR zainstalowanej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0953f-108">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="0953f-109">EnumerateLoadedRuntimes, metoda</span><span class="sxs-lookup"><span data-stu-id="0953f-109">EnumerateLoadedRuntimes Method</span></span>](iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="0953f-110">Zwraca Wyliczenie, które zawiera prawidłowy wskaźnik interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) dla każdego środowiska CLR, które jest załadowane w danym procesie.</span><span class="sxs-lookup"><span data-stu-id="0953f-110">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="0953f-111">Ta metoda zastępuje [GetVersionFromProcess —](getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="0953f-111">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="0953f-112">ExitProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="0953f-112">ExitProcess Method</span></span>](iclrmetahost-exitprocess-method.md)|<span data-ttu-id="0953f-113">Próbuje bezpiecznie zamknąć wszystkie ładowane środowiska uruchomieniowe, a następnie kończy proces.</span><span class="sxs-lookup"><span data-stu-id="0953f-113">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="0953f-114">Zastępuje funkcję [CorExitProcess —](corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="0953f-114">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="0953f-115">GetRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="0953f-115">GetRuntime Method</span></span>](iclrmetahost-getruntime-method.md)|<span data-ttu-id="0953f-116">Pobiera Interfejs [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , który odpowiada określonej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0953f-116">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="0953f-117">Ta metoda zastępuje funkcję [CorBindToRuntimeEx](corbindtoruntimeex-function.md) używaną z flagą [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="0953f-117">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="0953f-118">GetVersionFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="0953f-118">GetVersionFromFile Method</span></span>](iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="0953f-119">Pobiera oryginalną wersję kompilacji .NET Framework zestawu (przechowywaną w metadanych), uwzględniając ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="0953f-119">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="0953f-120">Ta metoda zastępuje [GetFileVersion —](getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="0953f-120">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="0953f-121">QueryLegacyV2RuntimeBinding, metoda</span><span class="sxs-lookup"><span data-stu-id="0953f-121">QueryLegacyV2RuntimeBinding Method</span></span>](iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="0953f-122">Zwraca interfejs reprezentujący środowisko uruchomieniowe, do którego powiązano starsze zasady aktywacji, na przykład przy użyciu `useLegacyV2RuntimeActivationPolicy` atrybutu w wpisie pliku konfiguracji [ \<startup> elementu](../../configure-apps/file-schema/startup/startup-element.md) , bezpośrednio wykorzystując starsze interfejsy API aktywacji lub wywołując metodę [ICLRRuntimeInfo:: BindAsLegacyV2Runtime —](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0953f-122">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="0953f-123">RequestRuntimeLoadedNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="0953f-123">RequestRuntimeLoadedNotification Method</span></span>](iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="0953f-124">Gwarantuje wywołanie zwrotne do określonego wskaźnika funkcji podczas pierwszego ładowania wersji środowiska CLR, ale nie zostało jeszcze uruchomione.</span><span class="sxs-lookup"><span data-stu-id="0953f-124">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="0953f-125">Ta metoda zastępuje [LockClrVersion —](lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="0953f-125">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0953f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0953f-126">Remarks</span></span>  
 <span data-ttu-id="0953f-127">Jedynym sposobem, aby uzyskać wystąpienie tego interfejsu, jest wywołanie funkcji [CLRCreateInstance](clrcreateinstance-function.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0953f-127">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0953f-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0953f-128">Requirements</span></span>  
 <span data-ttu-id="0953f-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0953f-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0953f-130">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="0953f-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0953f-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0953f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0953f-132">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0953f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0953f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0953f-133">See also</span></span>

- [<span data-ttu-id="0953f-134">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0953f-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0953f-135">Hosting</span><span class="sxs-lookup"><span data-stu-id="0953f-135">Hosting</span></span>](index.md)
