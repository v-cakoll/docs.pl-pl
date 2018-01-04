---
title: "METAHOST_POLICY_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_POLICY_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_POLICY_FLAGS
helpviewer_keywords: METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80abed08cc7659d4218dce445be81481bb5a665b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="ecda1-102">METAHOST_POLICY_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ecda1-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="ecda1-103">Udostępnia zasady powiązania, które są wspólne dla większości hosty w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ecda1-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="ecda1-104">To wyliczenie jest używany przez [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ecda1-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecda1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecda1-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ecda1-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ecda1-106">Members</span></span>  
  
|<span data-ttu-id="ecda1-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ecda1-107">Member</span></span>|<span data-ttu-id="ecda1-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ecda1-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="ecda1-109">Definiuje zasady zgodności wysokiej, który nie należy wziąć pod uwagę wszystkie środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany do bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="ecda1-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="ecda1-110">Zamiast tego traktuje tylko zainstalowany CLRs i preferencji składnika, ponieważ sam plik zestawu, zadeklarowane skompilowany przed wersji lub plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecda1-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="ecda1-111">Dotyczy zasad uaktualniania wersji wynik wiązania nie znaleziono dokładnego dopasowania, na podstawie zawartości HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="ecda1-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="ecda1-112">Jest to ten sam efekt co [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ecda1-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="ecda1-113">Powiązania są zwracane tak, jakby uruchomiono obrazu dostarczonego do wywołania w nowego procesu.</span><span class="sxs-lookup"><span data-stu-id="ecda1-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="ecda1-114">Obecnie `GetRequestedRuntime` ignoruje zbiór obciążana środowisk uruchomieniowych i wiąże z zestawu zainstalowanych środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="ecda1-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="ecda1-115">Ta flaga umożliwia hosta określić, które środowiska uruchomieniowego EXE zostanie z nim powiązane po jej uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="ecda1-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="ecda1-116">Okno dialogowe błędu jest wyświetlana, jeśli `GetRequestedRuntime` nie może znaleźć środowiska uruchomieniowego, która jest zgodna z parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="ecda1-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="ecda1-117">Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], to okno dialogowe błędu może mieć postać z pytaniem, czy użytkownik chce włączyć funkcję odpowiednie okno dialogowe funkcji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ecda1-117">Beginning with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="ecda1-118">`GetRequestedRuntime`używa obraz procesu (i wszelkie w odpowiednim pliku konfiguracyjnym) jako dodatkowe dane wejściowe proces wiązania.</span><span class="sxs-lookup"><span data-stu-id="ecda1-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="ecda1-119">Domyślnie `GetRequestedRuntime` nie wracały do ścieżka obrazu procesu (zazwyczaj EXE, który został użyty do uruchamiania procesu) podczas określania czasu wykonywania, aby powiązać.</span><span class="sxs-lookup"><span data-stu-id="ecda1-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="ecda1-120">`GetRequestedRuntime`musi sprawdzić, czy odpowiednie jednostki SKU jest zainstalowany, gdy informacje są niedostępne w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecda1-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="ecda1-121">Dzięki temu aplikacje, które nie mają plików konfiguracyjnych niepowodzenie bezpiecznie na mniejsze jednostki SKU niż domyślna instalacja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecda1-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="ecda1-122">Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednie jednostki SKU jest zainstalowany, chyba że jednostka SKU nie jest określony w pliku konfiguracyjnym `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="ecda1-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="ecda1-123">`GetRequestedRuntime`musi sprawdzić, czy odpowiednie jednostki SKU jest zainstalowany, gdy informacje są niedostępne w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecda1-123">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="ecda1-124">Dzięki temu aplikacje, które nie mają plików konfiguracyjnych niepowodzenie bezpiecznie na mniejsze jednostki SKU niż domyślna instalacja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecda1-124">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="ecda1-125">Domyślnie `GetRequestedRuntime` nie sprawdza, czy odpowiednie jednostki SKU jest zainstalowany, chyba że jednostka SKU nie jest określony w pliku konfiguracyjnym `<supportedRuntime />` elementu.</span><span class="sxs-lookup"><span data-stu-id="ecda1-125">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="ecda1-126">`GetRequestedRuntime`Parametr SEM_FAILCRITICALERRORS ignorować (który jest ustawiony przez wywołanie [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) funkcji) i wyświetlenie okna dialogowego błędu.</span><span class="sxs-lookup"><span data-stu-id="ecda1-126">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="ecda1-127">Domyślnie parametr SEM_FAILCRITICALERRORS powoduje pominięcie okna dialogowego błędu.</span><span class="sxs-lookup"><span data-stu-id="ecda1-127">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="ecda1-128">Zostało odziedziczone od innego procesu, a dyskretnej błędu może być niepożądane w danym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="ecda1-128">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecda1-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecda1-129">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecda1-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecda1-130">Requirements</span></span>  
 <span data-ttu-id="ecda1-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecda1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecda1-132">**Nagłówek:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="ecda1-132">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="ecda1-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecda1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecda1-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecda1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecda1-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecda1-135">See Also</span></span>  
 [<span data-ttu-id="ecda1-136">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ecda1-136">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="ecda1-137">GetRequestedRuntime, metoda</span><span class="sxs-lookup"><span data-stu-id="ecda1-137">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
