---
title: CreateDebuggingInterfaceFromVersion — Funkcja
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d1c49e8762d00e3e154c598c2542c4a76b9b28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107500"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="203d2-102">CreateDebuggingInterfaceFromVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="203d2-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="203d2-103">Tworzy [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiektu na podstawie określonej wersji informacji.</span><span class="sxs-lookup"><span data-stu-id="203d2-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="203d2-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="203d2-104">This function is obsolete in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="203d2-105">Aby uzyskać interfejs na środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0, użyj [iclrruntimeinfo::getinterface —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metody i określ identyfikator klasy CLSID_CLRDebuggingLegacy oraz identyfikator interfejsu IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="203d2-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="203d2-106">Aby uzyskać interfejs dla środowiska CLR 4 lub nowszy, wywołaj [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji, a następnie określ identyfikator klasy CLSID_CLRDebugging i identyfikator interfejsu IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="203d2-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203d2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="203d2-107">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="203d2-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="203d2-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="203d2-109">[in] Wersja `ICorDebug` jest to oczekiwane przez debuger.</span><span class="sxs-lookup"><span data-stu-id="203d2-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="203d2-110">Zobacz [cordebuginterfaceversion —](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) wyliczenie prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="203d2-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="203d2-111">[in] Typowe wersja środowiska uruchomieniowego języka skojarzone z aplikacją lub procesu do debugowania.</span><span class="sxs-lookup"><span data-stu-id="203d2-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="203d2-112">Zobacz [getversionfromprocess —](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) lub [getrequestedruntimeversion —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody, aby uzyskać informacje dotyczące pobierania tej wartości.</span><span class="sxs-lookup"><span data-stu-id="203d2-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="203d2-113">[out] Lokalizacji, która otrzymuje wskaźnik `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="203d2-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="203d2-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="203d2-114">Return Value</span></span>  
 <span data-ttu-id="203d2-115">Ta metoda zwraca standardowych kodów błędu modelu COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="203d2-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="203d2-116">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="203d2-116">Return code</span></span>|<span data-ttu-id="203d2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="203d2-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="203d2-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="203d2-118">S_OK</span></span>|<span data-ttu-id="203d2-119">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="203d2-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="203d2-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="203d2-120">E_INVALIDARG</span></span>|<span data-ttu-id="203d2-121">`szDebuggeeVersion` lub `ppCordb` ma wartość null lub wersji ciąg jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="203d2-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="203d2-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="203d2-122">Remarks</span></span>  
 <span data-ttu-id="203d2-123">`szDebuggeeVersion` Parametr mapowany na odpowiednią wersję plik MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="203d2-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="203d2-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="203d2-124">Requirements</span></span>  
 <span data-ttu-id="203d2-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="203d2-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="203d2-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="203d2-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="203d2-127">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="203d2-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="203d2-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="203d2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203d2-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="203d2-129">See also</span></span>

- [<span data-ttu-id="203d2-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="203d2-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
