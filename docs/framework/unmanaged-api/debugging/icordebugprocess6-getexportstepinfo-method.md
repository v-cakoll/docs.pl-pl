---
title: Metoda ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: d92b05e3d84a230e87901378f34ed27ac38286b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123461"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="bd5a8-102">Metoda ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="bd5a8-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="bd5a8-103">Zawiera informacje dotyczące funkcji wyeksportowanych przez środowisko uruchomieniowe, które ułatwiają przechodzenie przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd5a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd5a8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd5a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd5a8-105">Parameters</span></span>  
 <span data-ttu-id="bd5a8-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="bd5a8-106">pszExportName</span></span>  
 <span data-ttu-id="bd5a8-107">podczas Nazwa funkcji eksportu środowiska uruchomieniowego, która została zapisywana w tabeli eksportu PE.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="bd5a8-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="bd5a8-108">invokeKind</span></span>  
 <span data-ttu-id="bd5a8-109">określoną Wskaźnik do elementu członkowskiego wyliczenia [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) , który opisuje sposób, w jaki wyeksportowana funkcja wywoła kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="bd5a8-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="bd5a8-110">invokePurpose</span></span>  
 <span data-ttu-id="bd5a8-111">określoną Wskaźnik do elementu członkowskiego wyliczenia [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) , który opisuje, dlaczego wyeksportowana funkcja wywoła kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd5a8-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd5a8-112">Return Value</span></span>  
 <span data-ttu-id="bd5a8-113">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="bd5a8-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd5a8-114">Return value</span></span>|<span data-ttu-id="bd5a8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="bd5a8-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="bd5a8-116">Wywołanie metody zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="bd5a8-117">`pInvokeKind` lub `pInvokePurpose` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="bd5a8-118">Inne błędne wartości `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="bd5a8-119">Zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd5a8-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd5a8-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd5a8-121">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd5a8-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd5a8-122">Requirements</span></span>  
 <span data-ttu-id="bd5a8-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd5a8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd5a8-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bd5a8-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd5a8-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bd5a8-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd5a8-126">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd5a8-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd5a8-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd5a8-127">See also</span></span>

- [<span data-ttu-id="bd5a8-128">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd5a8-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="bd5a8-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bd5a8-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
