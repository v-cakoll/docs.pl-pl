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
ms.openlocfilehash: 8723de93f5d7fa93b1f62764f3774c8719750bd4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492299"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="e4ed4-102">ICorDebugProcess3::SetEnableCustomNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4ed4-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="e4ed4-103">Włącza i wyłącza niestandardowymi powiadomieniami debugera określonego typu.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ed4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4ed4-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4ed4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4ed4-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="e4ed4-106">[in] Typ, który określa niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="e4ed4-107">[in] `true` umożliwiające niestandardowymi powiadomieniami debugera; `false` wyłączyć powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="e4ed4-108">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4ed4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4ed4-109">Remarks</span></span>  
 <span data-ttu-id="e4ed4-110">Gdy `fEnable` jest ustawiona na `true`, wywołania <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metoda wyzwalacza [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="e4ed4-111">Powiadomienia są domyślnie wyłączona; w związku z tym debuger należy określić wszystkie typy powiadomień obsługującemu i chce, aby obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="e4ed4-112">Ponieważ [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) klasy jest ograniczone przez domenę aplikacji, debuger musi wywołać `SetEnableCustomNotification` dla każdej domeny aplikacji, w tym procesie, jeśli chce otrzymać powiadomienia przez cały proces.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="e4ed4-113">Począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], tylko obsługiwane powiadomienie jest powiadomienie zależności między wątkami.</span><span class="sxs-lookup"><span data-stu-id="e4ed4-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4ed4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4ed4-114">Requirements</span></span>  
 <span data-ttu-id="e4ed4-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4ed4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4ed4-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4ed4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4ed4-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4ed4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4ed4-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4ed4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ed4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4ed4-119">See also</span></span>
- [<span data-ttu-id="e4ed4-120">ICorDebugProcess3, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4ed4-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [<span data-ttu-id="e4ed4-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e4ed4-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e4ed4-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e4ed4-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
