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
ms.openlocfilehash: e5fd1730bbe5b6f2905691dce41a7f503227534a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179071"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="4b8ba-102">ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="4b8ba-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="4b8ba-103">Pobiera wyliczenia dla wszystkich typów środowiska wykonawczego systemu Windows w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4b8ba-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b8ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b8ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b8ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b8ba-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="4b8ba-106">[na zewnątrz] Wskaźnik do obiektu interfejsu [ICorDebugGuidToTypeEnum,](icordebugguidtotypeenum-interface.md) który może wyliczyć zarządzane reprezentacje typów środowiska wykonawczego systemu Windows aktualnie ładowanych w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4b8ba-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b8ba-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b8ba-107">Requirements</span></span>  
 <span data-ttu-id="4b8ba-108">**Platformy:** Środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4b8ba-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="4b8ba-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b8ba-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b8ba-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b8ba-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b8ba-111">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b8ba-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8ba-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b8ba-112">See also</span></span>

- [<span data-ttu-id="4b8ba-113">ICorDebugAppDomain3, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b8ba-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
