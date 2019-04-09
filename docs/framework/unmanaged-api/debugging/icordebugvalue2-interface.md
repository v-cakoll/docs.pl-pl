---
title: ICorDebugValue2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6718bbfdb1825b9f01698d76deec3fab16cb2ac6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091606"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="d414f-102">ICorDebugValue2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d414f-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="d414f-103">Umożliwia rozbudowanie interfejsu "ICorDebugValue", aby zapewnić obsługę dla obiektów "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="d414f-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d414f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d414f-104">Methods</span></span>  
  
|<span data-ttu-id="d414f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d414f-105">Method</span></span>|<span data-ttu-id="d414f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d414f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d414f-107">GetExactType, metoda</span><span class="sxs-lookup"><span data-stu-id="d414f-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="d414f-108">Pobiera wskaźnik interfejsu do `ICorDebugType` obiekt, który reprezentuje <xref:System.Type> tej wartości.</span><span class="sxs-lookup"><span data-stu-id="d414f-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d414f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d414f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d414f-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="d414f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d414f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d414f-111">Requirements</span></span>  
 <span data-ttu-id="d414f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d414f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d414f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d414f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d414f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d414f-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d414f-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d414f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d414f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d414f-116">See also</span></span>

- [<span data-ttu-id="d414f-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d414f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="d414f-118">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d414f-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
