---
title: ICorDebugModule::EnableClassLoadCallbacks — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: 1ca3adf30ad633fcfb10a4b43a435698d2899597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213533"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="a1406-102">ICorDebugModule::EnableClassLoadCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1406-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="a1406-103">Określa, czy wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](icordebugmanagedcallback-unloadclass-method.md) są wywoływane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="a1406-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1406-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1406-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1406-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1406-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="a1406-106">podczas Ustaw tę wartość, aby umożliwić programowi `true` uruchomieniowemu języka wspólnego (CLR) wywoływanie `ICorDebugManagedCallback::LoadClass` metod i w `ICorDebugManagedCallback::UnloadClass` przypadku wystąpienia skojarzonych ze zdarzeniami zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a1406-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="a1406-107">Wartość domyślna to `false` dla modułów niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="a1406-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="a1406-108">Wartość jest zawsze `true` dla modułów dynamicznych i nie można jej zmienić.</span><span class="sxs-lookup"><span data-stu-id="a1406-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1406-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1406-109">Remarks</span></span>  
 <span data-ttu-id="a1406-110">`ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` Wywołania zwrotne i są zawsze włączone dla modułów dynamicznych i nie można ich wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="a1406-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1406-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1406-111">Requirements</span></span>  
 <span data-ttu-id="a1406-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1406-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1406-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a1406-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1406-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1406-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1406-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1406-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1406-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1406-116">See also</span></span>
