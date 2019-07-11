---
title: ICorDebugType::GetClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd68df77adafb8b21e7684b28fe978722ca37e16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736792"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="65e64-102">ICorDebugType::GetClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="65e64-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="65e64-103">Pobiera wskaźnik interfejsu do ICorDebugClass, który reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="65e64-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e64-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65e64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65e64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65e64-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="65e64-106">[out] Wskaźnik na adres `ICorDebugClass` interfejs, który reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="65e64-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65e64-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65e64-107">Remarks</span></span>  
 <span data-ttu-id="65e64-108">`GetClass` może być wywoływana tylko w określonych warunkach.</span><span class="sxs-lookup"><span data-stu-id="65e64-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="65e64-109">Wywołaj [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) przed wywołaniem `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="65e64-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="65e64-110">Jeśli `ICorDebugType::GetType` zwraca wartość corelementtype — ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, `GetClass` może być wywoływana w celu uzyskania bez wystąpień typu dla typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="65e64-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65e64-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65e64-111">Requirements</span></span>  
 <span data-ttu-id="65e64-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65e64-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65e64-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65e64-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65e64-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65e64-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65e64-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65e64-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
