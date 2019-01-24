---
title: ICorDebug::EnumerateProcesses — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10741ef9d329986d869665ef3aae14196946bb22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724424"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="045bf-102">ICorDebug::EnumerateProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="045bf-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="045bf-103">Pobiera moduł wyliczający dla procesów, które są debugowane.</span><span class="sxs-lookup"><span data-stu-id="045bf-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="045bf-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="045bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="045bf-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="045bf-106">Wskaźnik na adres icordebugprocessenum — obiekt, który jest moduł wyliczający dla procesów debugowania.</span><span class="sxs-lookup"><span data-stu-id="045bf-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="045bf-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="045bf-107">Requirements</span></span>  
 <span data-ttu-id="045bf-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="045bf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="045bf-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="045bf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="045bf-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="045bf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="045bf-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="045bf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045bf-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="045bf-112">See also</span></span>
- [<span data-ttu-id="045bf-113">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="045bf-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
