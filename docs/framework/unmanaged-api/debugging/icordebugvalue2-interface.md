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
ms.openlocfilehash: 5c4d4f5d85fb076748b3f8aae498f024804fb0b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492367"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="d8842-102">ICorDebugValue2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d8842-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="d8842-103">Umożliwia rozbudowanie interfejsu "ICorDebugValue", aby zapewnić obsługę dla obiektów "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="d8842-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8842-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d8842-104">Methods</span></span>  
  
|<span data-ttu-id="d8842-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d8842-105">Method</span></span>|<span data-ttu-id="d8842-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d8842-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8842-107">GetExactType, metoda</span><span class="sxs-lookup"><span data-stu-id="d8842-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="d8842-108">Pobiera wskaźnik interfejsu do `ICorDebugType` obiekt, który reprezentuje <xref:System.Type> tej wartości.</span><span class="sxs-lookup"><span data-stu-id="d8842-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8842-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8842-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8842-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="d8842-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8842-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8842-111">Requirements</span></span>  
 <span data-ttu-id="d8842-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8842-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8842-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8842-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8842-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8842-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8842-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8842-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8842-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8842-116">See also</span></span>
- [<span data-ttu-id="d8842-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d8842-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="d8842-118">ICorDebugValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8842-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
