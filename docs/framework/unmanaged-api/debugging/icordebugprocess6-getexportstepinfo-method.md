---
title: Metoda ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178529"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="a2a4a-102">Metoda ICorDebugProcess6::GetExportStepInfo</span><span class="sxs-lookup"><span data-stu-id="a2a4a-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="a2a4a-103">Zawiera informacje na temat wyeksportowanych funkcji środowiska wykonawczego, aby ułatwić przechodzenie przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2a4a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2a4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2a4a-105">Parameters</span></span>  
 <span data-ttu-id="a2a4a-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="a2a4a-106">pszExportName</span></span>  
 <span data-ttu-id="a2a4a-107">[w] Nazwa funkcji eksportu środowiska uruchomieniowego, jak zapisano w tabeli eksportu pe.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="a2a4a-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="a2a4a-108">invokeKind</span></span>  
 <span data-ttu-id="a2a4a-109">[na zewnątrz] Wskaźnik do członka wyliczenia [CorDebugCodeInvokeKind,](cordebugcodeinvokekind-enumeration.md) który opisuje, jak wyeksportowana funkcja wywoła kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="a2a4a-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="a2a4a-110">invokePurpose</span></span>  
 <span data-ttu-id="a2a4a-111">[na zewnątrz] Wskaźnik do członka wyliczenia [CorDebugCodeInvokePurpose,](cordebugcodeinvokepurpose-enumeration.md) który opisuje, dlaczego wyeksportowana funkcja wywoła kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2a4a-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2a4a-112">Return Value</span></span>  
 <span data-ttu-id="a2a4a-113">Metoda może zwracać wartości wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="a2a4a-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2a4a-114">Return value</span></span>|<span data-ttu-id="a2a4a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a2a4a-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="a2a4a-116">Wywołanie metody zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="a2a4a-117">`pInvokeKind`lub `pInvokePurpose` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="a2a4a-118">Inne `HRESULT` wartości, które nie po awarii.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="a2a4a-119">W stosownych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2a4a-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2a4a-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2a4a-121">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a2a4a-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2a4a-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2a4a-122">Requirements</span></span>  
 <span data-ttu-id="a2a4a-123">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2a4a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2a4a-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2a4a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2a4a-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2a4a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2a4a-126">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2a4a-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a4a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2a4a-127">See also</span></span>

- [<span data-ttu-id="a2a4a-128">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2a4a-128">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="a2a4a-129">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a2a4a-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
