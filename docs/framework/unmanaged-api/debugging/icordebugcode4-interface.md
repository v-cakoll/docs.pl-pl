---
title: ICorDebugCode4, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
ms.openlocfilehash: 870ac1e62363493989fe638483ea474d648c8c69
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893319"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="b4eb1-102">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4eb1-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="b4eb1-103">Zapewnia metodę, która umożliwia debugerowi Wyliczenie zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="b4eb1-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4eb1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b4eb1-104">Methods</span></span>  
  
|<span data-ttu-id="b4eb1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4eb1-105">Method</span></span>|<span data-ttu-id="b4eb1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b4eb1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4eb1-107">EnumerateVariableHomes, metoda</span><span class="sxs-lookup"><span data-stu-id="b4eb1-107">EnumerateVariableHomes Method</span></span>](icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="b4eb1-108">Pobiera moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="b4eb1-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4eb1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4eb1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4eb1-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b4eb1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4eb1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4eb1-111">Requirements</span></span>  
 <span data-ttu-id="b4eb1-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4eb1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4eb1-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4eb1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4eb1-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4eb1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4eb1-115">**.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4eb1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4eb1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4eb1-116">See also</span></span>

- [<span data-ttu-id="b4eb1-117">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b4eb1-117">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="b4eb1-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b4eb1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
