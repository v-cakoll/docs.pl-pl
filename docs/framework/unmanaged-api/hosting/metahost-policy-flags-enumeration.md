---
title: METAHOST_POLICY_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a2ce58576ebf03d756c4e8157ab65d57cd7683b
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380254"
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="91a9e-102">METAHOST_POLICY_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="91a9e-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="91a9e-103">Udostępnia zasady powiązania, które są wspólne dla większości hosty środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="91a9e-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="91a9e-104">To wyliczenie jest używane przez [iclrmetahostpolicy::getrequestedruntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="91a9e-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a9e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="91a9e-105">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="91a9e-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="91a9e-106">Members</span></span>  
  
|<span data-ttu-id="91a9e-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="91a9e-107">Member</span></span>|<span data-ttu-id="91a9e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="91a9e-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="91a9e-109">Definiuje zasady wysokiej zgodności z poprzednią wersją, który nie należy wziąć pod uwagę wszystkie środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany do bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="91a9e-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="91a9e-110">Zamiast tego traktuje tylko zainstalowane CLRs i preferencje dotyczące składnika, ponieważ sam plik zestawu, zadeklarowany oparta na wersji lub plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="91a9e-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="91a9e-111">Dotyczy zasad uaktualniania wersji wynik powiązania dokładne dopasowanie nie zostanie znaleziony, na podstawie zawartości HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="91a9e-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="91a9e-112">Ma to taki sam skutek jak [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="91a9e-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="91a9e-113">Powiązanie wyniki są zwracane, tak, jakby obrazu dostarczonego wywołania zostały uruchomione w ramach nowego procesu.</span><span class="sxs-lookup"><span data-stu-id="91a9e-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="91a9e-114">Obecnie `GetRequestedRuntime` ignoruje zbiór obciążana środowisk uruchomieniowych i wiąże względem zestawu zainstalowanych modułów wykonawczych.</span><span class="sxs-lookup"><span data-stu-id="91a9e-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="91a9e-115">Ta flaga umożliwia hostowi na określenie środowiska uruchomieniowego, który powiąże EXE po jej uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="91a9e-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="91a9e-116">Wyświetlane jest okno dialogowe błędu, jeśli `GetRequestedRuntime` nie może odnaleźć środowiska uruchomieniowego, który jest zgodny z parametrami wejściowymi.</span><span class="sxs-lookup"><span data-stu-id="91a9e-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="91a9e-117">Począwszy od programu .NET Framework 4.5, to okno dialogowe błędu może mieć postać Windows funkcji okno dialogowe z pytaniem, czy użytkownik chce włączyć funkcję odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="91a9e-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="91a9e-118">`GetRequestedRuntime` używa obrazu procesu (i wszelkie odpowiedni plik konfiguracji) jako dodatkowe dane wejściowe do przetworzenia powiązania.</span><span class="sxs-lookup"><span data-stu-id="91a9e-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="91a9e-119">Domyślnie `GetRequestedRuntime` nie wrócił do ścieżki obrazu procesu (zwykle EXE, który został użyty do uruchamiania procesu) podczas określania środowiska uruchomieniowego, można powiązać.</span><span class="sxs-lookup"><span data-stu-id="91a9e-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="91a9e-120">`GetRequestedRuntime` należy sprawdzić, czy odpowiednią jednostkę SKU jest zainstalowany, gdy żadne informacje nie będzie dostępna w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="91a9e-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="91a9e-121">Dzięki temu aplikacje, które nie mają plików konfiguracyjnych do elegancko nie powieść się na mniejsze jednostki SKU niż domyślnej instalacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91a9e-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="91a9e-122">Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednią jednostkę SKU jest zainstalowany, chyba że jednostka SKU nie jest określony w pliku konfiguracyjnym `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="91a9e-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="91a9e-123">`GetRequestedRuntime` powinien ignorować SEM_FAILCRITICALERRORS (który jest ustawiony przez wywołanie metody [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) funkcji) i wyświetlenie okna dialogowego błędu.</span><span class="sxs-lookup"><span data-stu-id="91a9e-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="91a9e-124">Domyślnie SEM_FAILCRITICALERRORS powoduje pominięcie okna dialogowego błędu.</span><span class="sxs-lookup"><span data-stu-id="91a9e-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="91a9e-125">Zostało odziedziczone z innego procesu, a dyskretnej błędu może być niepożądane w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="91a9e-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91a9e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91a9e-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a9e-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91a9e-127">Requirements</span></span>  
 <span data-ttu-id="91a9e-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91a9e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91a9e-129">**Nagłówek:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="91a9e-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="91a9e-130">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91a9e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91a9e-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91a9e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a9e-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91a9e-132">See also</span></span>

- [<span data-ttu-id="91a9e-133">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="91a9e-133">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="91a9e-134">GetRequestedRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="91a9e-134">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
