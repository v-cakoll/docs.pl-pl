---
title: ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73a08e83d67c973294938a030b95b906aec6be6d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126610"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="5a950-102">ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a950-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="5a950-103">Pobiera moduł wyliczający dla wszystkich buforowanych [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typów.</span><span class="sxs-lookup"><span data-stu-id="5a950-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a950-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a950-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a950-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a950-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="5a950-106">[out] Wskaźnik do [icordebugguidtotypeenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) obiektu interfejsu, który można wyliczyć reprezentacje zarządzane [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy załadowanych obecnie do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a950-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a950-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a950-107">Requirements</span></span>  
 **<span data-ttu-id="5a950-108">Platformy:</span><span class="sxs-lookup"><span data-stu-id="5a950-108">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="5a950-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a950-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a950-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a950-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5a950-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5a950-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a950-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a950-112">See also</span></span>

- [<span data-ttu-id="5a950-113">ICorDebugAppDomain3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5a950-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
