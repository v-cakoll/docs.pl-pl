---
title: ICorDebugMDA::GetFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
ms.openlocfilehash: 7c3b0331cc4d987070b2d04beb621c4966a27cb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129834"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="d97e0-102">ICorDebugMDA::GetFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="d97e0-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="d97e0-103">Pobiera flagi skojarzone z zarządzanym asystentem debugowania (MDA) reprezentowane przez [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d97e0-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d97e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d97e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d97e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d97e0-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="d97e0-106">podczas Bitowa kombinacja wartości wyliczenia [CorDebugMDAFlags —](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) , które określają ustawienia flag dla tego MDA.</span><span class="sxs-lookup"><span data-stu-id="d97e0-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d97e0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d97e0-107">Requirements</span></span>  
 <span data-ttu-id="d97e0-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d97e0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d97e0-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d97e0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d97e0-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d97e0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d97e0-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d97e0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97e0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d97e0-112">See also</span></span>

- [<span data-ttu-id="d97e0-113">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="d97e0-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="d97e0-114">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="d97e0-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
