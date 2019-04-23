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
ms.openlocfilehash: 22a838748414f9d89cdc7ff469f7f5cc5e11b9d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108306"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="51882-102">ICorDebugModule::EnableClassLoadCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="51882-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="51882-103">Formanty czy [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołania zwrotne są wywoływane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="51882-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51882-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51882-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51882-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51882-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="51882-106">[in] Ustaw tę wartość na `true` Aby włączyć środowisko uruchomieniowe języka wspólnego (CLR), aby wywołać `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` metody, gdy wystąpią ich powiązanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51882-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="51882-107">Wartość domyślna to `false` dla modułów nie dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="51882-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="51882-108">Wartość jest zawsze `true` dla modułów dynamicznych i nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="51882-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51882-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51882-109">Remarks</span></span>  
 <span data-ttu-id="51882-110">`ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` wywołania zwrotne są zawsze włączone dla modułów dynamicznych i nie może być wyłączony.</span><span class="sxs-lookup"><span data-stu-id="51882-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51882-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51882-111">Requirements</span></span>  
 <span data-ttu-id="51882-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51882-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51882-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51882-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51882-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51882-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51882-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51882-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51882-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51882-116">See also</span></span>
