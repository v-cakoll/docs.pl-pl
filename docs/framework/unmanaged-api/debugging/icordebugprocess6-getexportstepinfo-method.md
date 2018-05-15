---
title: Metoda ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d0758a8603b7c31844b39c9f3beefea04e0a029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="9f424-102">Metoda ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="9f424-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="9f424-103">Zawiera informacje dotyczące środowiska uruchomieniowego wyeksportowane funkcje ułatwiające krok za pomocą kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9f424-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f424-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f424-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f424-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f424-105">Parameters</span></span>  
 <span data-ttu-id="9f424-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="9f424-106">pszExportName</span></span>  
 <span data-ttu-id="9f424-107">[in] Nazwa funkcji eksportu środowiska uruchomieniowego podczas zapisywania w tabeli eksportu PE.</span><span class="sxs-lookup"><span data-stu-id="9f424-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="9f424-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="9f424-108">invokeKind</span></span>  
 <span data-ttu-id="9f424-109">[out] Wskaźnik do elementu członkowskiego [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) wyliczenie opisujące jak wyeksportowanej funkcji wywoła kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9f424-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="9f424-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="9f424-110">invokePurpose</span></span>  
 <span data-ttu-id="9f424-111">[out] Wskaźnik do elementu członkowskiego [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) wyliczenia, który opisuje Dlaczego wyeksportowanej funkcji wywoła kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9f424-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f424-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9f424-112">Return Value</span></span>  
 <span data-ttu-id="9f424-113">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9f424-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="9f424-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9f424-114">Return value</span></span>|<span data-ttu-id="9f424-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9f424-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="9f424-116">Wywołanie metody zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9f424-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="9f424-117">`pInvokeKind` lub `pInvokePurpose` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="9f424-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="9f424-118">Inne niepowodzenie `HRESULT` wartości.</span><span class="sxs-lookup"><span data-stu-id="9f424-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="9f424-119">Jako odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="9f424-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f424-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f424-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f424-121">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9f424-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f424-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f424-122">Requirements</span></span>  
 <span data-ttu-id="9f424-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f424-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f424-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f424-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f424-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f424-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f424-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f424-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f424-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f424-127">See Also</span></span>  
 [<span data-ttu-id="9f424-128">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="9f424-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="9f424-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9f424-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
