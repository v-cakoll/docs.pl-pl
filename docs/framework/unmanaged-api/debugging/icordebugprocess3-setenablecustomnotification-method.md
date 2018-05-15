---
title: ICorDebugProcess3::SetEnableCustomNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a84061cff7cc5dbdeba1e0e66396e04a8f345cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="f421f-102">ICorDebugProcess3::SetEnableCustomNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="f421f-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="f421f-103">Włącza i wyłącza powiadomienia debugera niestandardowe określonego typu.</span><span class="sxs-lookup"><span data-stu-id="f421f-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f421f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f421f-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f421f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f421f-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="f421f-106">[in] Typ, który określa debuger niestandardowych powiadomień.</span><span class="sxs-lookup"><span data-stu-id="f421f-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="f421f-107">[in] `true` do włączenia powiadomień debugera niestandardowych; `false` Aby wyłączyć powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="f421f-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="f421f-108">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f421f-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f421f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f421f-109">Remarks</span></span>  
 <span data-ttu-id="f421f-110">Gdy `fEnable` ustawiono `true`, wywołań <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> wyzwalacza — metoda [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f421f-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="f421f-111">Powiadomienia są domyślnie wyłączona; w związku z tym debuger należy określić wszystkie typy powiadomień zna i chce obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="f421f-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="f421f-112">Ponieważ [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) klasy jest ograniczone w zależności od domeny aplikacji, należy wywołać debuger `SetEnableCustomNotification` dla każdej domeny aplikacji w ramach procesu, jeśli chce otrzymywać powiadomienia przez cały proces.</span><span class="sxs-lookup"><span data-stu-id="f421f-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="f421f-113">Począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], tylko powiadomień obsługiwanych jest powiadomień zależności między wątkami.</span><span class="sxs-lookup"><span data-stu-id="f421f-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f421f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f421f-114">Requirements</span></span>  
 <span data-ttu-id="f421f-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f421f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f421f-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f421f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f421f-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f421f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f421f-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f421f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f421f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f421f-119">See Also</span></span>  
 [<span data-ttu-id="f421f-120">ICorDebugProcess3, interfejs</span><span class="sxs-lookup"><span data-stu-id="f421f-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [<span data-ttu-id="f421f-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f421f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f421f-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f421f-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
