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
ms.openlocfilehash: 45b1d0c0a3199227ab644ba8732198dd14b1cb4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792996"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="055ec-102">ICorDebugModule::IsDynamic — Metoda</span><span class="sxs-lookup"><span data-stu-id="055ec-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="055ec-103">Pobiera wartość wskazującą, czy ten moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="055ec-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="055ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="055ec-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="055ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="055ec-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="055ec-106">[out] `true`, jeśli ten moduł jest dynamiczny; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="055ec-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="055ec-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="055ec-107">Remarks</span></span>  
 <span data-ttu-id="055ec-108">Moduł dynamiczny może dodawać nowe klasy i usuwać istniejące klasy nawet po załadowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="055ec-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="055ec-109">Wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](icordebugmanagedcallback-unloadclass-method.md) informują debuger po dodaniu lub usunięciu klasy.</span><span class="sxs-lookup"><span data-stu-id="055ec-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="055ec-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="055ec-110">Requirements</span></span>  
 <span data-ttu-id="055ec-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="055ec-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="055ec-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="055ec-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="055ec-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="055ec-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="055ec-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="055ec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
