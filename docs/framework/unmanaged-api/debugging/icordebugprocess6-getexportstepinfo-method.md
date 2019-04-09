---
title: Metoda ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a891e6d65d159875f5607ac33b0668414cb380
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137218"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="6c0d8-102">Metoda ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="6c0d8-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="6c0d8-103">Zawiera informacje na temat funkcji środowiska uruchomieniowego wyeksportowane ułatwiające Przechodź przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c0d8-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c0d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c0d8-105">Parameters</span></span>  
 <span data-ttu-id="6c0d8-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="6c0d8-106">pszExportName</span></span>  
 <span data-ttu-id="6c0d8-107">[in] Nazwa funkcji eksportu środowiska uruchomieniowego podczas zapisywania w tabeli eksportu PE.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="6c0d8-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="6c0d8-108">invokeKind</span></span>  
 <span data-ttu-id="6c0d8-109">[out] Wskaźnik do składowej klasy [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) wyliczenie opisujące jak eksportowanych funkcji spowoduje wywołanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="6c0d8-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="6c0d8-110">invokePurpose</span></span>  
 <span data-ttu-id="6c0d8-111">[out] Wskaźnik do składowej klasy [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) wyliczenie, które w tym artykule opisano, dlaczego eksportowanych funkcji będzie wywoływać kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c0d8-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c0d8-112">Return Value</span></span>  
 <span data-ttu-id="6c0d8-113">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="6c0d8-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c0d8-114">Return value</span></span>|<span data-ttu-id="6c0d8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6c0d8-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="6c0d8-116">Wywołanie metody powiodło się.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-116">The method call was successful.</span></span>|  
|`E_POINTER`|`pInvokeKind` <span data-ttu-id="6c0d8-117">lub `pInvokePurpose` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-117">or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="6c0d8-118">Inne niepowodzenia `HRESULT` wartości.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="6c0d8-119">Odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c0d8-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c0d8-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c0d8-121">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6c0d8-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c0d8-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c0d8-122">Requirements</span></span>  
 <span data-ttu-id="6c0d8-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c0d8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0d8-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c0d8-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c0d8-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c0d8-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6c0d8-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6c0d8-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6c0d8-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c0d8-127">See also</span></span>

- [<span data-ttu-id="6c0d8-128">Interfejs ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="6c0d8-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="6c0d8-129">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6c0d8-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
