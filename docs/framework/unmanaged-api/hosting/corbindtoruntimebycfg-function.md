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
ms.openlocfilehash: 3802354bf52cd2aab2a4149d565993b9965e8312
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138297"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="1bdae-102">CorBindToRuntimeByCfg — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1bdae-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="1bdae-103">Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu przy użyciu informacji o wersji, które są odczytywane z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="1bdae-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="1bdae-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1bdae-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdae-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1bdae-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1bdae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bdae-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="1bdae-107">podczas Wskaźnik do obiektu `IStream`, który odczytuje plik XML.</span><span class="sxs-lookup"><span data-stu-id="1bdae-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="1bdae-108">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="1bdae-108">[in] Reserved for future use.</span></span> <span data-ttu-id="1bdae-109">Użyj 0 (zero) jako wartości.</span><span class="sxs-lookup"><span data-stu-id="1bdae-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="1bdae-110">podczas Wartość wyliczenia [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) , która określa zachowanie uruchamiania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="1bdae-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="1bdae-111">podczas `CLSID` klasy coclass implementującej interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1bdae-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="1bdae-112">Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1bdae-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="1bdae-113">podczas `IID` `ICorRuntimeHost` lub interfejsu `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="1bdae-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="1bdae-114">Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1bdae-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="1bdae-115">określoną Wskaźnik do adresu zwracanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1bdae-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bdae-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1bdae-116">Remarks</span></span>  
 <span data-ttu-id="1bdae-117">Format pliku XML jest modelowany po standardowym pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bdae-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="1bdae-118">Aby uzyskać więcej informacji na temat plików XML, zobacz [Schemat pliku konfiguracji](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="1bdae-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bdae-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1bdae-119">Requirements</span></span>  
 <span data-ttu-id="1bdae-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bdae-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bdae-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1bdae-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bdae-122">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1bdae-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bdae-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bdae-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdae-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bdae-124">See also</span></span>

- [<span data-ttu-id="1bdae-125">CorBindToCurrentRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="1bdae-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="1bdae-126">CorBindToRuntime, funkcja</span><span class="sxs-lookup"><span data-stu-id="1bdae-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="1bdae-127">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="1bdae-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="1bdae-128">CorBindToRuntimeHost, funkcja</span><span class="sxs-lookup"><span data-stu-id="1bdae-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="1bdae-129">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1bdae-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="1bdae-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="1bdae-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
