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
ms.openlocfilehash: 1b51b924652019cf05401e1972797c18e74b82d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431551"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="a5dc5-102">CreateDebuggingInterfaceFromVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a5dc5-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="a5dc5-103">Tworzy [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiekt na podstawie określonej wersji informacji.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="a5dc5-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5dc5-104">This function is obsolete in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="a5dc5-105">Aby uzyskać interfejsu na środowisko uruchomieniowe języka wspólnego (CLR) 2.0, użyj [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) — metoda i określ identyfikator klasy CLSID_CLRDebuggingLegacy oraz identyfikatora interfejsu IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="a5dc5-106">Aby uzyskać interfejs 4 CLR lub później, wywołaj [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji, a następnie określ identyfikator klasy CLSID_CLRDebugging i identyfikatora interfejsu IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5dc5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5dc5-107">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5dc5-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5dc5-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="a5dc5-109">[in] Wersja `ICorDebug` przez debuger zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="a5dc5-110">Zobacz [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) wyliczenie dla prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="a5dc5-111">[in] Typowe wersja środowiska uruchomieniowego CLR skojarzony z aplikacją lub procesów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="a5dc5-112">Zobacz [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) lub [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody, aby uzyskać informacje dotyczące pobierania tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="a5dc5-113">[out] Lokalizacja, w której otrzymuje wskaźnik `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5dc5-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a5dc5-114">Return Value</span></span>  
 <span data-ttu-id="a5dc5-115">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="a5dc5-116">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="a5dc5-116">Return code</span></span>|<span data-ttu-id="a5dc5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a5dc5-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a5dc5-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5dc5-118">S_OK</span></span>|<span data-ttu-id="a5dc5-119">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="a5dc5-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a5dc5-120">E_INVALIDARG</span></span>|<span data-ttu-id="a5dc5-121">`szDebuggeeVersion` lub `ppCordb` ma wartość null lub wersja parametry są niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5dc5-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5dc5-122">Remarks</span></span>  
 <span data-ttu-id="a5dc5-123">`szDebuggeeVersion` Parametr mapowany na odpowiednią wersję programu MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="a5dc5-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5dc5-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5dc5-124">Requirements</span></span>  
 <span data-ttu-id="a5dc5-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5dc5-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5dc5-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a5dc5-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5dc5-127">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5dc5-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5dc5-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5dc5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5dc5-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5dc5-129">See Also</span></span>  
 [<span data-ttu-id="a5dc5-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a5dc5-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
