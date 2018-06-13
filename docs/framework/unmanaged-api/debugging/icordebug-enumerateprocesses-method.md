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
ms.openlocfilehash: 53d40c198b53370733009c76fd3d49f14df93e6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402099"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="197fa-102">ICorDebug::EnumerateProcesses — Metoda</span><span class="sxs-lookup"><span data-stu-id="197fa-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="197fa-103">Pobiera moduł wyliczający dla procesów, które są debugowane.</span><span class="sxs-lookup"><span data-stu-id="197fa-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="197fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="197fa-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="197fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="197fa-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="197fa-106">Wskaźnik do adresu ICorDebugProcessEnum obiektu, który moduł wyliczający dla procesów debugowany.</span><span class="sxs-lookup"><span data-stu-id="197fa-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="197fa-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="197fa-107">Requirements</span></span>  
 <span data-ttu-id="197fa-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="197fa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="197fa-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="197fa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="197fa-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="197fa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="197fa-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="197fa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197fa-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="197fa-112">See Also</span></span>  
 [<span data-ttu-id="197fa-113">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="197fa-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
