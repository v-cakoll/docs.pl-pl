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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dcf814311821218c0dfd8fdcbb91afd3973f2b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482473"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="0e38b-102">ICorDebugModule::EnableClassLoadCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="0e38b-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="0e38b-103">Formanty czy [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołania zwrotne są wywoływane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0e38b-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e38b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e38b-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e38b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e38b-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="0e38b-106">[in] Ustaw tę wartość na `true` Aby włączyć środowisko uruchomieniowe języka wspólnego (CLR), aby wywołać `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` metody, gdy wystąpią ich powiązanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0e38b-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="0e38b-107">Wartość domyślna to `false` dla modułów nie dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="0e38b-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="0e38b-108">Wartość jest zawsze `true` dla modułów dynamicznych i nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="0e38b-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e38b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e38b-109">Remarks</span></span>  
 <span data-ttu-id="0e38b-110">`ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` wywołania zwrotne są zawsze włączone dla modułów dynamicznych i nie może być wyłączony.</span><span class="sxs-lookup"><span data-stu-id="0e38b-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e38b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e38b-111">Requirements</span></span>  
 <span data-ttu-id="0e38b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e38b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e38b-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e38b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e38b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e38b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e38b-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e38b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e38b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e38b-116">See also</span></span>


