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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db5d07d2b9a295a5cd21b4d4af954503b8bd7a8b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763667"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="dcf2f-102">ICorDebugModule::IsDynamic — Metoda</span><span class="sxs-lookup"><span data-stu-id="dcf2f-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="dcf2f-103">Pobiera wartość wskazującą, czy ten moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcf2f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcf2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcf2f-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="dcf2f-106">[out] `true` Jeśli ten moduł jest dynamiczny; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcf2f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcf2f-107">Remarks</span></span>  
 <span data-ttu-id="dcf2f-108">Modułu dynamicznego może dodawać nowe klasy i Usuń istniejące klasy, nawet po zakończeniu moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="dcf2f-109">[ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołania zwrotne informują debugera, gdy klasa zostały dodane lub usunięte.</span><span class="sxs-lookup"><span data-stu-id="dcf2f-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcf2f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcf2f-110">Requirements</span></span>  
 <span data-ttu-id="dcf2f-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf2f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf2f-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcf2f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcf2f-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcf2f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcf2f-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf2f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
