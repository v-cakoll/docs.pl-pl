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
ms.openlocfilehash: 55d0b40bbdb5628f60090d9d70f7dccbebe9d58f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784996"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="d56d6-102">ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="d56d6-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="d56d6-103">Pobiera moduł wyliczający dla wszystkich typów środowisko wykonawcze systemu Windows w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d56d6-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d56d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d56d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d56d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d56d6-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="d56d6-106">określoną Wskaźnik do obiektu interfejsu [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) , który może wyliczyć zarządzane reprezentacje typów środowisko wykonawcze systemu Windows aktualnie załadowanych w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d56d6-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d56d6-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d56d6-107">Requirements</span></span>  
 <span data-ttu-id="d56d6-108">**Platformy:** środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d56d6-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="d56d6-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d56d6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d56d6-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d56d6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d56d6-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d56d6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56d6-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d56d6-112">See also</span></span>

- [<span data-ttu-id="d56d6-113">ICorDebugAppDomain3, interfejs</span><span class="sxs-lookup"><span data-stu-id="d56d6-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
