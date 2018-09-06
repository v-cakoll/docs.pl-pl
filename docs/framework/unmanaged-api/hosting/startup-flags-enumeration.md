---
title: STARTUP_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4680187de7318a6438bf6a5e6bd7c5f3acd05c2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43797849"
---
# <a name="startupflags-enumeration"></a><span data-ttu-id="1ef02-102">STARTUP_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1ef02-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="1ef02-103">Zawiera wartości, które wskazują zachowanie uruchamiania środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1ef02-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="1ef02-104">Domyślnie, wyrzucanie elementów bezużytecznych jest niewspółbieżne i tylko Biblioteka klasy podstawowej jest załadowana do obszaru neutralnej domeny.</span><span class="sxs-lookup"><span data-stu-id="1ef02-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef02-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ef02-105">Syntax</span></span>  
  
```  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="1ef02-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1ef02-106">Members</span></span>  
  
|<span data-ttu-id="1ef02-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1ef02-107">Member</span></span>|<span data-ttu-id="1ef02-108">Opis</span><span class="sxs-lookup"><span data-stu-id="1ef02-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="1ef02-109">Określa, że powinny być używane współbieżne wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1ef02-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="1ef02-110">Jeśli obiekt wywołujący prosi o kompilację serwera i równoczesne wyrzucania elementów bezużytecznych na komputerze jednoprocesorowym, stacja robocza kompilacji i niewspółbieżnym wyrzucaniem elementów bezużytecznych zostaną uruchomione w zamian.</span><span class="sxs-lookup"><span data-stu-id="1ef02-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="1ef02-111">**Uwaga:** współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacji, które są uruchomione przez środowisko WOW64 x86 emulatora w systemach 64-bitowych, które implementują architekturę Intel Itanium (wcześniej noszącą nazwę IA-64).</span><span class="sxs-lookup"><span data-stu-id="1ef02-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="1ef02-112">Aby uzyskać więcej informacji o używaniu WOW64 w 64-bitowych systemach Windows, zobacz [uruchomiona 32-bitowych aplikacji](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="1ef02-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="1ef02-113">Określa, że Optymalizacja programu ładującego powinna występować.</span><span class="sxs-lookup"><span data-stu-id="1ef02-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="1ef02-114">Określa, że żadne zespoły nie są ładowane jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="1ef02-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="1ef02-115">Określa, że wszystkie zespoły są ładowane jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="1ef02-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="1ef02-116">Określa, że wszystkie zestawy o silnej nazwie są ładowane jako niezależne od domeny.</span><span class="sxs-lookup"><span data-stu-id="1ef02-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="1ef02-117">Określa, że zasady wersji środowiska CLR nie zostaną zastosowane do wersji przekazania.</span><span class="sxs-lookup"><span data-stu-id="1ef02-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="1ef02-118">Dokładna wersja określona w CLR zostanie załadowana.</span><span class="sxs-lookup"><span data-stu-id="1ef02-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="1ef02-119">Podkładka nie ocenia uprawnień do ustalenia najnowszej zgodnej wersji.</span><span class="sxs-lookup"><span data-stu-id="1ef02-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="1ef02-120">Określa, że preferowanego czasu wykonywania zostanie ustawiona, ale faktycznie nie jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="1ef02-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="1ef02-121">Określa, że serwer wyrzucania elementów bezużytecznych zostanie użyty.</span><span class="sxs-lookup"><span data-stu-id="1ef02-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="1ef02-122">Określa, że wyrzucanie elementów bezużytecznych zostanie zachowana, aby adres wirtualny używany.</span><span class="sxs-lookup"><span data-stu-id="1ef02-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="1ef02-123">Określa, że mieszanie hostingu interfejsu będzie niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="1ef02-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="1ef02-124">Określa, że personifikacja nie powinna przepływać przez punkty asynchroniczne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="1ef02-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="1ef02-125">Określa, że stos pełnego wątku nie powinien być ustalony podczas uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="1ef02-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="1ef02-126">Określa, że zarządzane personifikacje i personifikacje osiągnięte przez platformę wywołania będą przepływać przez punkty asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="1ef02-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="1ef02-127">Domyślnie tylko zarządzane impersonacje będą przepływać przez punkty asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="1ef02-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="1ef02-128">Określa, że wyrzucanie elementów bezużytecznych będzie używać mniej przydzielonych miejsc, gdy brakuje pamięci systemowej.</span><span class="sxs-lookup"><span data-stu-id="1ef02-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="1ef02-129">Zobacz `gcTrimCommitOnLowMemory` w [Optymalizacja udostępnionej usługi hostingu internetowego](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="1ef02-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="1ef02-130">Określa, że śledzenie zdarzeń dla Windows (ETW) jest włączone dla typowych zdarzeń środowiska wykonawczego języka.</span><span class="sxs-lookup"><span data-stu-id="1ef02-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="1ef02-131">Począwszy od systemów Windows Vista, śledzenie zdarzeń jest zawsze włączone, więc ta flaga nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="1ef02-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="1ef02-132">Zobacz [Kontrolowanie logowania w programie .NET Framework](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="1ef02-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="1ef02-133">Określa, czy jest włączone monitorowanie zasobów domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1ef02-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="1ef02-134">Zobacz <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> właściwości i [ \<appdomainresourcemonitoring — > Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="1ef02-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ef02-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ef02-135">Requirements</span></span>  
 <span data-ttu-id="1ef02-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ef02-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef02-137">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ef02-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ef02-138">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ef02-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ef02-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef02-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef02-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ef02-140">See Also</span></span>  
 [<span data-ttu-id="1ef02-141">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1ef02-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
