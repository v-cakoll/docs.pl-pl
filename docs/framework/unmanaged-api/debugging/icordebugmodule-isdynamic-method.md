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
ms.openlocfilehash: 5157c62f2719a9d62608750cd122561807197494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="932d3-102">ICorDebugModule::IsDynamic — Metoda</span><span class="sxs-lookup"><span data-stu-id="932d3-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="932d3-103">Pobiera wartość wskazującą, czy ten moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="932d3-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="932d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="932d3-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="932d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="932d3-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="932d3-106">[out] `true` Jeśli ten moduł jest dynamiczny; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="932d3-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="932d3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="932d3-107">Remarks</span></span>  
 <span data-ttu-id="932d3-108">Modułu dynamicznego może dodawać nowe klasy i Usuń istniejące klasy, nawet po załadowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="932d3-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="932d3-109">[ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołania zwrotne informuje debuger po klasie zostały dodane lub usunięte.</span><span class="sxs-lookup"><span data-stu-id="932d3-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="932d3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="932d3-110">Requirements</span></span>  
 <span data-ttu-id="932d3-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="932d3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="932d3-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="932d3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="932d3-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="932d3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="932d3-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="932d3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
