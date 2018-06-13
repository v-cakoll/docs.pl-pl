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
ms.openlocfilehash: 950790b246094c71900a5fb4da7d92be7d24aba2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421619"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="2141d-102">ICorDebugModule::EnableClassLoadCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="2141d-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="2141d-103">Formanty czy [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołań zwrotnych są nazywane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="2141d-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2141d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2141d-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2141d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2141d-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="2141d-106">[in] Ta wartość `true` Aby włączyć środowisko uruchomieniowe języka wspólnego (CLR), aby wywołać `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` metody, gdy występują ich skojarzonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2141d-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="2141d-107">Wartość domyślna to `false` dla modułów-dynamic.</span><span class="sxs-lookup"><span data-stu-id="2141d-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="2141d-108">Wartość jest zawsze `true` dla modułów dynamicznych i nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="2141d-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2141d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2141d-109">Remarks</span></span>  
 <span data-ttu-id="2141d-110">`ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` wywołań zwrotnych dla modułów dynamicznej zawsze są włączone i nie można wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="2141d-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2141d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2141d-111">Requirements</span></span>  
 <span data-ttu-id="2141d-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2141d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2141d-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2141d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2141d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2141d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2141d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2141d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2141d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2141d-116">See Also</span></span>  
    
 
