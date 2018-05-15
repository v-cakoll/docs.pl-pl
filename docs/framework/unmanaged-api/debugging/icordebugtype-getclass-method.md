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
ms.openlocfilehash: ff2258faa8bc766c8c769f4e135f868334516b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="153b8-102">ICorDebugType::GetClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="153b8-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="153b8-103">Pobiera wskaźnika interfejsu do ICorDebugClass, który reprezentuje bez wystąpień typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="153b8-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="153b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="153b8-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="153b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="153b8-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="153b8-106">[out] Wskaźnik do adresu `ICorDebugClass` interfejs, który reprezentuje bez wystąpień typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="153b8-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="153b8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="153b8-107">Remarks</span></span>  
 <span data-ttu-id="153b8-108">`GetClass` może zostać wywołany tylko w niektórych warunkach.</span><span class="sxs-lookup"><span data-stu-id="153b8-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="153b8-109">Wywołanie [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) przed wywołaniem `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="153b8-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="153b8-110">Jeśli `ICorDebugType::GetType` zwraca wartość CorElementType po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, `GetClass` można wywołać w celu uzyskania bez wystąpień typu dla typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="153b8-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="153b8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="153b8-111">Requirements</span></span>  
 <span data-ttu-id="153b8-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="153b8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="153b8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="153b8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="153b8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="153b8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="153b8-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="153b8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
