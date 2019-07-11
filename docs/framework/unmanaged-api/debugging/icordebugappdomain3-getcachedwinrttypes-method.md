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
ms.openlocfilehash: 4ba981d86f90af449820ce13aa847169ca877429
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737774"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="6675b-102">ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="6675b-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="6675b-103">Pobiera moduł wyliczający dla wszystkich typów środowiska wykonawczego Windows pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6675b-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6675b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6675b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6675b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6675b-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="6675b-106">[out] Wskaźnik do [icordebugguidtotypeenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) obiektu interfejsu, który można wyliczyć zarządzanych reprezentacja typów środowiska wykonawczego Windows obecnie załadowane w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6675b-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6675b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6675b-107">Requirements</span></span>  
 <span data-ttu-id="6675b-108">**Platformy:** Środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6675b-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="6675b-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6675b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6675b-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6675b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6675b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6675b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6675b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6675b-112">See also</span></span>

- [<span data-ttu-id="6675b-113">ICorDebugAppDomain3, interfejs</span><span class="sxs-lookup"><span data-stu-id="6675b-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
