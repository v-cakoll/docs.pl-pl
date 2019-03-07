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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d872e4a65c0556dddac468336e6a42dd7d7923c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477652"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="b14b2-102">ICorDebugType::GetFirstTypeParameter — Metoda</span><span class="sxs-lookup"><span data-stu-id="b14b2-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="b14b2-103">Pobiera wskaźnik interfejsu do ICorDebugType, który reprezentuje pierwszy <xref:System.Type> parametru na typ reprezentowany przez ten `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="b14b2-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b14b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b14b2-104">Syntax</span></span>  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b14b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b14b2-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="b14b2-106">[out] Wskaźnik na adres `ICorDebugType` obiekt, który reprezentuje pierwszy parametr.</span><span class="sxs-lookup"><span data-stu-id="b14b2-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b14b2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b14b2-107">Remarks</span></span>  
 <span data-ttu-id="b14b2-108">`GetFirstTypeParameter` można wywołać w przypadkach, w którym dodatkowe informacje o typie pociąga za sobą, co najwyżej jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="b14b2-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="b14b2-109">W szczególności może służyć Jeśli typ jest ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, pole lub ELEMENT_TYPE_PTR, wskazane przez [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b14b2-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b14b2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b14b2-110">Requirements</span></span>  
 <span data-ttu-id="b14b2-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b14b2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b14b2-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b14b2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b14b2-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b14b2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b14b2-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b14b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
