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
ms.openlocfilehash: d403a8bfba3599a60d8af72307590f5a569480dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791294"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="768aa-102">ICorDebugType::GetClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="768aa-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="768aa-103">Pobiera wskaźnik interfejsu do ICorDebugClass, który reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="768aa-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="768aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="768aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="768aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="768aa-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="768aa-106">określoną Wskaźnik do adresu interfejsu `ICorDebugClass`, który reprezentuje typ ogólny bez wystąpień.</span><span class="sxs-lookup"><span data-stu-id="768aa-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="768aa-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="768aa-107">Remarks</span></span>  
 <span data-ttu-id="768aa-108">`GetClass` można wywołać tylko w określonych warunkach.</span><span class="sxs-lookup"><span data-stu-id="768aa-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="768aa-109">Wywołaj metodę [ICorDebugType:: GetType](icordebugtype-gettype-method.md) przed wywołaniem `GetClass`.</span><span class="sxs-lookup"><span data-stu-id="768aa-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="768aa-110">Jeśli `ICorDebugType::GetType` zwraca wartość CorElementType —, która jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, `GetClass` można wywołać, aby uzyskać typ nieskonkretyzowany dla typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="768aa-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="768aa-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="768aa-111">Requirements</span></span>  
 <span data-ttu-id="768aa-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="768aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="768aa-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="768aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="768aa-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="768aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="768aa-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="768aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
