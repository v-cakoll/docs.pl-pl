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
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139219"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="b1c91-102">ICorDebugModule::EnableClassLoadCallbacks — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1c91-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="b1c91-103">Określa, czy wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) są wywoływane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="b1c91-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1c91-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1c91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1c91-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="b1c91-106">podczas Ustaw tę wartość na `true`, aby umożliwić programowi uruchomieniowemu języka wspólnego (CLR) wywoływanie metod `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` w przypadku wystąpienia skojarzonych z nimi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b1c91-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="b1c91-107">Wartość domyślna to `false` modułów niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="b1c91-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="b1c91-108">Wartość jest zawsze `true` dla modułów dynamicznych i nie można jej zmienić.</span><span class="sxs-lookup"><span data-stu-id="b1c91-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1c91-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1c91-109">Remarks</span></span>  
 <span data-ttu-id="b1c91-110">Wywołania zwrotne `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` są zawsze włączone dla modułów dynamicznych i nie można ich wyłączyć.</span><span class="sxs-lookup"><span data-stu-id="b1c91-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c91-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1c91-111">Requirements</span></span>  
 <span data-ttu-id="b1c91-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c91-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c91-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1c91-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1c91-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1c91-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1c91-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c91-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c91-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1c91-116">See also</span></span>
