---
title: "ICorDebug::EnumerateProcesses — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ffabcc97a4af33fc859cd096e671f98d52e89e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="ab777-102">ICorDebug::EnumerateProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="ab777-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="ab777-103">Pobiera moduł wyliczający dla procesów, które są debugowane.</span><span class="sxs-lookup"><span data-stu-id="ab777-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab777-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab777-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab777-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab777-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="ab777-106">Wskaźnik do adresu ICorDebugProcessEnum obiektu, który moduł wyliczający dla procesów debugowany.</span><span class="sxs-lookup"><span data-stu-id="ab777-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab777-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab777-107">Requirements</span></span>  
 <span data-ttu-id="ab777-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab777-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab777-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab777-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab777-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab777-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab777-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab777-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab777-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab777-112">See Also</span></span>  
 [<span data-ttu-id="ab777-113">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab777-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
