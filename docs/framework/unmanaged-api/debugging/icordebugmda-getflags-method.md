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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a35e9f7cf43105db05408f285cd89dbd839a4cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969042"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="c0fc3-102">ICorDebugMDA::GetFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0fc3-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="c0fc3-103">Pobiera flagi skojarzone z zarządzanego Asystenta debugowania (MDA), reprezentowana przez [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c0fc3-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0fc3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0fc3-104">Syntax</span></span>  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0fc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0fc3-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="c0fc3-106">[in] Bitowa kombinacja [cordebugmdaflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) wartości wyliczenia, które określają ustawienia flagi to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="c0fc3-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0fc3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0fc3-107">Requirements</span></span>  
 <span data-ttu-id="c0fc3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0fc3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0fc3-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0fc3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0fc3-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0fc3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0fc3-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0fc3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fc3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0fc3-112">See also</span></span>

- [<span data-ttu-id="c0fc3-113">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="c0fc3-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="c0fc3-114">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c0fc3-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
