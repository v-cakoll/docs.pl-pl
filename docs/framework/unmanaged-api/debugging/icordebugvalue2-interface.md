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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091606"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="caf8e-102">ICorDebugValue2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="caf8e-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="caf8e-103">Umożliwia rozbudowanie interfejsu "ICorDebugValue", aby zapewnić obsługę dla obiektów "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="caf8e-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="caf8e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="caf8e-104">Methods</span></span>  
  
|<span data-ttu-id="caf8e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="caf8e-105">Method</span></span>|<span data-ttu-id="caf8e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="caf8e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="caf8e-107">GetExactType, metoda</span><span class="sxs-lookup"><span data-stu-id="caf8e-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="caf8e-108">Pobiera wskaźnik interfejsu do `ICorDebugType` obiekt, który reprezentuje <xref:System.Type> tej wartości.</span><span class="sxs-lookup"><span data-stu-id="caf8e-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caf8e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="caf8e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caf8e-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="caf8e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caf8e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="caf8e-111">Requirements</span></span>  
 <span data-ttu-id="caf8e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caf8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caf8e-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="caf8e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="caf8e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="caf8e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caf8e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caf8e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf8e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="caf8e-116">See also</span></span>

- [<span data-ttu-id="caf8e-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="caf8e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="caf8e-118">ICorDebugValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="caf8e-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
