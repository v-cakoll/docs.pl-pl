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
ms.openlocfilehash: 021f2b7a720c2190d56bdb2b35214c581a7b5f56
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456938"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="38e8a-102">CorBindToCurrentRuntime — Funkcja</span><span class="sxs-lookup"><span data-stu-id="38e8a-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="38e8a-103">Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu za pomocą informacji o wersji przechowywanych w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="38e8a-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="38e8a-104">Format pliku XML jest modelowane pliku konfiguracji standardowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38e8a-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="38e8a-105">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [schemat pliku konfiguracji](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="38e8a-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="38e8a-106">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38e8a-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="38e8a-107">Zobacz [ładowanie środowiska uruchomieniowego języka wspólnego w procesie](https://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span><span class="sxs-lookup"><span data-stu-id="38e8a-107">See [Loading the Common Language Runtime into a Process](https://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e8a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="38e8a-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38e8a-109">Parametry</span><span class="sxs-lookup"><span data-stu-id="38e8a-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="38e8a-110">[in] Nazwa pliku konfiguracji aplikacji, który określa wersja środowiska CLR do załadowania.</span><span class="sxs-lookup"><span data-stu-id="38e8a-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="38e8a-111">Jeśli nazwa pliku nie jest w pełni kwalifikowana, zakłada się, w tym samym katalogu co plik wykonywalny wywołania.</span><span class="sxs-lookup"><span data-stu-id="38e8a-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="38e8a-112">Wersja środowiska uruchomieniowego do załadowania jest opisana przez atrybut version w [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="38e8a-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="38e8a-113">Jeśli wersja nie jest określona lub `<requiredRuntime>` nie można odnaleźć elementu, najnowszą wersję środowiska CLR, który jest zainstalowany na maszynie jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="38e8a-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="38e8a-114">[in] `CLSID` z koklas, która implementuje [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="38e8a-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="38e8a-115">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="38e8a-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="38e8a-116">[in] `IID` Dla żądanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="38e8a-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="38e8a-117">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="38e8a-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="38e8a-118">[out] Wskaźnik interfejsu zwrócone.</span><span class="sxs-lookup"><span data-stu-id="38e8a-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e8a-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38e8a-119">Requirements</span></span>  
 <span data-ttu-id="38e8a-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38e8a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e8a-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38e8a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38e8a-122">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38e8a-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38e8a-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38e8a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e8a-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38e8a-124">See Also</span></span>  
 [<span data-ttu-id="38e8a-125">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="38e8a-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="38e8a-126">CorBindToRuntimeByCfg, funkcja</span><span class="sxs-lookup"><span data-stu-id="38e8a-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="38e8a-127">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="38e8a-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="38e8a-128">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="38e8a-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="38e8a-129">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="38e8a-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="38e8a-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="38e8a-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
