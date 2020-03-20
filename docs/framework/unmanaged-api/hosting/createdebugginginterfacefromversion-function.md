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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176451"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="d3dab-102">CreateDebuggingInterfaceFromVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d3dab-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="d3dab-103">Tworzy obiekt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) na podstawie informacji o określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="d3dab-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="d3dab-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d3dab-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="d3dab-105">Zamiast tego, aby uzyskać interfejs dla środowiska wykonawczego języka wspólnego (CLR) 2.0, należy użyć [metody ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) i określić identyfikator klasy CLSID_CLRDebuggingLegacy i identyfikator interfejsu IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="d3dab-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="d3dab-106">Aby uzyskać interfejs dla clr 4 lub nowszego, wywołaj [clrCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji i określić identyfikator klasy CLSID_CLRDebugging i identyfikator interfejsu IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="d3dab-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3dab-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3dab-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3dab-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3dab-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="d3dab-109">[w] Wersja tego `ICorDebug` jest oczekiwana przez debugera.</span><span class="sxs-lookup"><span data-stu-id="d3dab-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="d3dab-110">Zobacz [wyliczenie CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) dla prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="d3dab-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="d3dab-111">[w] Wersja środowiska wykonawczego języka wspólnego skojarzone z aplikacji lub procesu do debugowania.</span><span class="sxs-lookup"><span data-stu-id="d3dab-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="d3dab-112">Zobacz [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) lub [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody informacji na temat pobierania tej wartości.</span><span class="sxs-lookup"><span data-stu-id="d3dab-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="d3dab-113">[na zewnątrz] Lokalizacja, która odbiera wskaźnik `ICorDebug` do obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3dab-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3dab-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d3dab-114">Return Value</span></span>  
 <span data-ttu-id="d3dab-115">Ta metoda zwraca standardowe kody błędów COM zdefiniowane w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="d3dab-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="d3dab-116">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="d3dab-116">Return code</span></span>|<span data-ttu-id="d3dab-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d3dab-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d3dab-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3dab-118">S_OK</span></span>|<span data-ttu-id="d3dab-119">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d3dab-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="d3dab-120">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="d3dab-120">E_INVALIDARG</span></span>|<span data-ttu-id="d3dab-121">`szDebuggeeVersion`lub `ppCordb` ma wartość null lub ciąg wersji jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="d3dab-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3dab-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3dab-122">Remarks</span></span>  
 <span data-ttu-id="d3dab-123">Parametr `szDebuggeeVersion` jest mapowana na odpowiednią wersję pliku MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="d3dab-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3dab-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3dab-124">Requirements</span></span>  
 <span data-ttu-id="d3dab-125">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3dab-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3dab-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3dab-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3dab-127">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d3dab-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3dab-128">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3dab-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3dab-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3dab-129">See also</span></span>

- [<span data-ttu-id="d3dab-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d3dab-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
