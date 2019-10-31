---
title: ICorDebugModule::IsDynamic — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 5774b40178ce0d7c2ef5d063a37b9011fc2630df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127950"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="20e6c-102">ICorDebugModule::IsDynamic — Metoda</span><span class="sxs-lookup"><span data-stu-id="20e6c-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="20e6c-103">Pobiera wartość wskazującą, czy ten moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="20e6c-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20e6c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20e6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20e6c-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="20e6c-106">[out] `true`, jeśli ten moduł jest dynamiczny; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="20e6c-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20e6c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20e6c-107">Remarks</span></span>  
 <span data-ttu-id="20e6c-108">Moduł dynamiczny może dodawać nowe klasy i usuwać istniejące klasy nawet po załadowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="20e6c-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="20e6c-109">Wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) informują debuger po dodaniu lub usunięciu klasy.</span><span class="sxs-lookup"><span data-stu-id="20e6c-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e6c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20e6c-110">Requirements</span></span>  
 <span data-ttu-id="20e6c-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20e6c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e6c-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20e6c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20e6c-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20e6c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20e6c-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e6c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
