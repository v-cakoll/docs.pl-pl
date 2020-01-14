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
ms.openlocfilehash: 048286fb9e1af34cd964fb5b21892778f9575d2c
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938203"
---
# <a name="metahost_policy_flags-enumeration"></a><span data-ttu-id="54a5d-102">METAHOST_POLICY_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="54a5d-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="54a5d-103">Program udostępnia zasady powiązań, które są wspólne dla większości hostów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="54a5d-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="54a5d-104">To wyliczenie jest używane przez metodę [ICLRMetaHostPolicy:: GetRequestedRuntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="54a5d-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54a5d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="54a5d-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="54a5d-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="54a5d-106">Members</span></span>  
  
|<span data-ttu-id="54a5d-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="54a5d-107">Member</span></span>|<span data-ttu-id="54a5d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="54a5d-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="54a5d-109">Definiuje zasady wysokiej zgodności, które nie uwzględnia żadnego środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany do bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="54a5d-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="54a5d-110">Zamiast tego uwzględnia tylko zainstalowaną CLRs i preferencje składnika, jak wynika z samego pliku zestawu, zadeklarowanej wbudowanej wersji lub pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="54a5d-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="54a5d-111">Stosuje zasady uaktualniania do wyniku powiązania wersji, gdy nie znaleziono dokładnego dopasowania, na podstawie zawartości HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="54a5d-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="54a5d-112">Ma to taki sam efekt jak [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="54a5d-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="54a5d-113">Wyniki powiązań są zwracane, jeśli obraz dostarczony do wywołania został uruchomiony w nowym procesie.</span><span class="sxs-lookup"><span data-stu-id="54a5d-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="54a5d-114">Obecnie `GetRequestedRuntime` ignoruje zestaw plików wykonywalnych do załadowania i tworzy powiązania z zestawem zainstalowanych środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="54a5d-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="54a5d-115">Ta flaga umożliwia hostowi określenie, które środowisko uruchomieniowe zostanie powiązane z tym, gdy zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="54a5d-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="54a5d-116">Gdy `GetRequestedRuntime` nie może znaleźć środowiska uruchomieniowego zgodnego z parametrami wejściowymi, zostanie wyświetlone okno dialogowe błędu.</span><span class="sxs-lookup"><span data-stu-id="54a5d-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="54a5d-117">Począwszy od .NET Framework 4,5, to okno dialogowe błędu może przyjmować formę okna dialogowego funkcji systemu Windows z pytaniem, czy użytkownik chce włączyć odpowiednią funkcję.</span><span class="sxs-lookup"><span data-stu-id="54a5d-117">Beginning with the .NET Framework 4.5, this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="54a5d-118">`GetRequestedRuntime` używa obrazu procesu (i dowolnego odpowiedniego pliku konfiguracji) jako dodatkowego wejścia do procesu powiązania.</span><span class="sxs-lookup"><span data-stu-id="54a5d-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="54a5d-119">Domyślnie `GetRequestedRuntime` nie wraca do ścieżki obrazu procesu (zazwyczaj jest to plik EXE używany do uruchomienia procesu) podczas określania środowiska uruchomieniowego, z którym ma zostać utworzone powiązanie.</span><span class="sxs-lookup"><span data-stu-id="54a5d-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="54a5d-120">`GetRequestedRuntime` musi sprawdzić, czy odpowiednia jednostka SKU jest zainstalowana, gdy w pliku konfiguracji nie ma dostępnych informacji.</span><span class="sxs-lookup"><span data-stu-id="54a5d-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="54a5d-121">Dzięki temu aplikacje, które nie mają plików konfiguracyjnych, mogą bezpiecznie kończyć się niepowodzeniem w mniejszych jednostkach SKU niż domyślna instalacja .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54a5d-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="54a5d-122">Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednia jednostka SKU jest zainstalowana, chyba że atrybut SKU jest określony w pliku konfiguracji `<supportedRuntime />` elemencie.</span><span class="sxs-lookup"><span data-stu-id="54a5d-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="54a5d-123">`GetRequestedRuntime` powinien ignorować SEM_FAILCRITICALERRORS (ustawiane przez wywołanie funkcji [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) ) i wyświetlać okno dialogowe błędu.</span><span class="sxs-lookup"><span data-stu-id="54a5d-123">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function), and show the error dialog box.</span></span> <span data-ttu-id="54a5d-124">Domyślnie SEM_FAILCRITICALERRORS pomija okno dialogowe błędu.</span><span class="sxs-lookup"><span data-stu-id="54a5d-124">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="54a5d-125">Być może został on odziedziczony z innego procesu, a błąd dyskretny może być niepożądany w Twoim scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="54a5d-125">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54a5d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54a5d-126">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54a5d-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54a5d-127">Requirements</span></span>  
 <span data-ttu-id="54a5d-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54a5d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54a5d-129">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="54a5d-129">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="54a5d-130">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54a5d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54a5d-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54a5d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a5d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54a5d-132">See also</span></span>

- [<span data-ttu-id="54a5d-133">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="54a5d-133">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="54a5d-134">GetRequestedRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="54a5d-134">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
