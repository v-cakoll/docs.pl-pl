---
title: CorBindToCurrentRuntime — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3667ac5a19664507b767ee6c5421a5e93f6cdfe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="05dfe-102">CorBindToCurrentRuntime — Funkcja</span><span class="sxs-lookup"><span data-stu-id="05dfe-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="05dfe-103">Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu za pomocą wersji informacje przechowywane w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="05dfe-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="05dfe-104">Format pliku XML jest modelowane pliku konfiguracji standardowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05dfe-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="05dfe-105">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="05dfe-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="05dfe-106">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05dfe-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="05dfe-107">Zobacz [ładowania środowiska CLR do procesu](http://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span><span class="sxs-lookup"><span data-stu-id="05dfe-107">See [Loading the Common Language Runtime into a Process](http://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05dfe-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="05dfe-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05dfe-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="05dfe-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="05dfe-110">[in] Nazwa określająca wersję środowiska CLR, aby załadować plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05dfe-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="05dfe-111">Jeśli nazwa pliku nie jest w pełni kwalifikowana, zakłada się w tym samym katalogu co plik wykonywalny wywołania.</span><span class="sxs-lookup"><span data-stu-id="05dfe-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="05dfe-112">Wersja środowiska uruchomieniowego do załadowania jest opisane przez atrybut version w [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="05dfe-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="05dfe-113">Jeśli wersja nie jest określona lub `<requiredRuntime>` nie można znaleźć elementu, jest ładowany najnowszą wersję środowiska CLR, która jest zainstalowana na komputerze.</span><span class="sxs-lookup"><span data-stu-id="05dfe-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="05dfe-114">[in] `CLSID` Klasy coclass, który implementuje albo [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="05dfe-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="05dfe-115">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="05dfe-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="05dfe-116">[in] `IID` Interfejsu żądania dostępu.</span><span class="sxs-lookup"><span data-stu-id="05dfe-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="05dfe-117">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="05dfe-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="05dfe-118">[out] Wskaźnik interfejsu zwrócony.</span><span class="sxs-lookup"><span data-stu-id="05dfe-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05dfe-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05dfe-119">Requirements</span></span>  
 <span data-ttu-id="05dfe-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05dfe-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05dfe-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05dfe-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05dfe-122">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05dfe-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05dfe-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05dfe-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05dfe-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05dfe-124">See Also</span></span>  
 [<span data-ttu-id="05dfe-125">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="05dfe-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="05dfe-126">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="05dfe-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="05dfe-127">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="05dfe-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="05dfe-128">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="05dfe-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="05dfe-129">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="05dfe-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="05dfe-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="05dfe-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
