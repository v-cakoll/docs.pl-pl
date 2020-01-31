---
title: ICorDebugType::GetFirstTypeParameter — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 1a02190b595fb01bdc2df46182bfa64bfe638db4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791289"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="b0eae-102">ICorDebugType::GetFirstTypeParameter — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0eae-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="b0eae-103">Pobiera wskaźnik interfejsu do ICorDebugType, który reprezentuje pierwszy parametr <xref:System.Type> typu reprezentowanego przez ten `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="b0eae-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0eae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0eae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0eae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0eae-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="b0eae-106">określoną Wskaźnik do adresu obiektu `ICorDebugType`, który reprezentuje pierwszy parametr.</span><span class="sxs-lookup"><span data-stu-id="b0eae-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0eae-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0eae-107">Remarks</span></span>  
 <span data-ttu-id="b0eae-108">`GetFirstTypeParameter` można wywołać w przypadkach, gdy dodatkowe informacje o typie obejmują, co najwyżej jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="b0eae-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="b0eae-109">W szczególności można go użyć, jeśli typ jest ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF lub ELEMENT_TYPE_PTR, zgodnie z opisem przez metodę [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b0eae-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0eae-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0eae-110">Requirements</span></span>  
 <span data-ttu-id="b0eae-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0eae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0eae-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0eae-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0eae-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b0eae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0eae-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0eae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
