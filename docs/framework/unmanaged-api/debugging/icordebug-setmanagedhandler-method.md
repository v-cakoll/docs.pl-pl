---
title: "ICorDebug::SetManagedHandler — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetManagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06f0989058ed21e736fde0aee5f1cd1dd66e0ca8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="7786b-102">ICorDebug::SetManagedHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="7786b-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="7786b-103">Określa obiekt programu obsługi zdarzeń dla zdarzeń zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="7786b-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7786b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7786b-104">Syntax</span></span>  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7786b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7786b-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="7786b-106">[in] Wskaźnik do [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) obiektu, który jest obiektem programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7786b-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7786b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7786b-107">Remarks</span></span>  
 <span data-ttu-id="7786b-108">`SetManagedHandler`musi zostać wywołana w czasie tworzenia.</span><span class="sxs-lookup"><span data-stu-id="7786b-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="7786b-109">Jeśli `ICorDebugManagedCallback` implementacji nie zawiera wystarczających interfejsy do obsługi zdarzeń debugowania dla aplikacji, która jest debugowana, `SetManagedHandler` zwraca HRESULT E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="7786b-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7786b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7786b-110">Requirements</span></span>  
 <span data-ttu-id="7786b-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7786b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7786b-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7786b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7786b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7786b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7786b-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7786b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7786b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7786b-115">See Also</span></span>  
 [<span data-ttu-id="7786b-116">ICorDebug — interfejs</span><span class="sxs-lookup"><span data-stu-id="7786b-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
