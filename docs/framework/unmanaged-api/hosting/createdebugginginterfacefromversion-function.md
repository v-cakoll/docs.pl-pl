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
ms.openlocfilehash: 0e1395229b67c4054df62935375a4136edf63078
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616492"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="c4a3b-102">CreateDebuggingInterfaceFromVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c4a3b-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="c4a3b-103">Tworzy obiekt [ICorDebug](../debugging/icordebug-interface.md) na podstawie informacji o określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-103">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="c4a3b-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="c4a3b-105">Zamiast tego, aby uzyskać interfejs środowiska uruchomieniowego języka wspólnego (CLR) 2,0, użyj metody [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) i określ identyfikator klasy CLSID_CLRDebuggingLegacy i identyfikator interfejsu IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="c4a3b-106">Aby uzyskać interfejs dla środowiska CLR 4 lub nowszego, wywołaj funkcję [CLRCreateInstance](clrcreateinstance-function.md) i określ identyfikator klasy CLSID_CLRDebugging i identyfikator interfejsu IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a3b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4a3b-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4a3b-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4a3b-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="c4a3b-109">podczas Wersja programu `ICorDebug` oczekiwana przez debuger.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="c4a3b-110">Zapoznaj się z wyliczeniem [CorDebugInterfaceVersion —](../debugging/cordebuginterfaceversion-enumeration.md) pod kątem prawidłowych wartości.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-110">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="c4a3b-111">podczas Wersja środowiska uruchomieniowego języka wspólnego skojarzona z aplikacją lub procesem do debugowania.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="c4a3b-112">Aby uzyskać informacje na temat pobierania tej wartości, zobacz [GetVersionFromProcess —](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) lub [GetRequestedRuntimeVersion —](getrequestedruntimeversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="c4a3b-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="c4a3b-113">określoną Lokalizacja, która otrzymuje wskaźnik do `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4a3b-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c4a3b-114">Return Value</span></span>  
 <span data-ttu-id="c4a3b-115">Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w pliku WinError. h, a także następujące wartości.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="c4a3b-116">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="c4a3b-116">Return code</span></span>|<span data-ttu-id="c4a3b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c4a3b-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c4a3b-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4a3b-118">S_OK</span></span>|<span data-ttu-id="c4a3b-119">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="c4a3b-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c4a3b-120">E_INVALIDARG</span></span>|<span data-ttu-id="c4a3b-121">`szDebuggeeVersion`lub `ppCordb` ma wartość null lub ciąg wersji jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4a3b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4a3b-122">Remarks</span></span>  
 <span data-ttu-id="c4a3b-123">`szDebuggeeVersion`Parametr mapuje do odpowiedniej wersji mscordbi. dll.</span><span class="sxs-lookup"><span data-stu-id="c4a3b-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4a3b-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4a3b-124">Requirements</span></span>  
 <span data-ttu-id="c4a3b-125">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4a3b-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4a3b-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c4a3b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4a3b-127">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c4a3b-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4a3b-128">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4a3b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a3b-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4a3b-129">See also</span></span>

- [<span data-ttu-id="c4a3b-130">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="c4a3b-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
