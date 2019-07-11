---
title: CorBindToRuntimeByCfg — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8f5e9a909a752dd8dc70bfc1c683b4611715f31
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767962"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="4340f-102">CorBindToRuntimeByCfg — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4340f-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="4340f-103">Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu za pomocą informacji o wersji, które są odczytywane z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="4340f-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="4340f-104">Ta funkcja jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4340f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4340f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4340f-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4340f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4340f-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="4340f-107">[in] Wskaźnik do `IStream` obiekt, który odczytuje plik XML.</span><span class="sxs-lookup"><span data-stu-id="4340f-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="4340f-108">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="4340f-108">[in] Reserved for future use.</span></span> <span data-ttu-id="4340f-109">Użyj wartości 0 (zero) jako wartość.</span><span class="sxs-lookup"><span data-stu-id="4340f-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="4340f-110">[in] Wartość [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia, która określa zachowanie uruchamiania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="4340f-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="4340f-111">[in] `CLSID` z koklas, która implementuje [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4340f-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="4340f-112">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="4340f-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="4340f-113">[in] `IID` Albo `ICorRuntimeHost` lub `ICLRRuntimeHost` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4340f-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="4340f-114">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="4340f-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="4340f-115">[out] Wskaźnik na adres zwrócony interfejs.</span><span class="sxs-lookup"><span data-stu-id="4340f-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4340f-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4340f-116">Remarks</span></span>  
 <span data-ttu-id="4340f-117">Format pliku XML jest modelowane pliku konfiguracji standardowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4340f-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="4340f-118">Aby uzyskać więcej informacji na temat plików XML, zobacz [schemat pliku konfiguracji](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="4340f-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4340f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4340f-119">Requirements</span></span>  
 <span data-ttu-id="4340f-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4340f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4340f-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4340f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4340f-122">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4340f-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4340f-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4340f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4340f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4340f-124">See also</span></span>

- [<span data-ttu-id="4340f-125">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="4340f-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="4340f-126">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="4340f-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="4340f-127">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="4340f-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="4340f-128">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="4340f-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="4340f-129">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="4340f-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="4340f-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="4340f-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
