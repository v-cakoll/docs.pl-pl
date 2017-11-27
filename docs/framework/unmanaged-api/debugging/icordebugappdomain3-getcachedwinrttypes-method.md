---
title: "ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb41b278b21b2289c7f5a7164a1bd01bc39423b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="e7347-102">ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="e7347-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="e7347-103">Pobiera moduł wyliczający wszystkie buforowane [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów.</span><span class="sxs-lookup"><span data-stu-id="e7347-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7347-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7347-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7347-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7347-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="e7347-106">[out] Wskaźnik do [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) obiektu interfejsu, który można wyliczyć zarządzanych reprezentacje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy załadowany w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7347-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7347-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7347-107">Requirements</span></span>  
 <span data-ttu-id="e7347-108">**Platformy:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7347-108">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="e7347-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7347-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7347-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7347-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7347-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7347-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7347-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7347-112">See Also</span></span>  
 [<span data-ttu-id="e7347-113">ICorDebugAppDomain3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="e7347-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
