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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23f588b46eb452b7670085249938f7d10cea1ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61752259"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="9c57b-102">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="9c57b-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="9c57b-103">Dostarcza metodę, która umożliwia debugera wyliczanie zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="9c57b-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c57b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9c57b-104">Methods</span></span>  
  
|<span data-ttu-id="9c57b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9c57b-105">Method</span></span>|<span data-ttu-id="9c57b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9c57b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9c57b-107">EnumerateVariableHomes, metoda</span><span class="sxs-lookup"><span data-stu-id="9c57b-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="9c57b-108">Pobiera moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="9c57b-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c57b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c57b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c57b-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="9c57b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c57b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c57b-111">Requirements</span></span>  
 <span data-ttu-id="9c57b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c57b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c57b-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c57b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c57b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c57b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c57b-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c57b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c57b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c57b-116">See also</span></span>

- [<span data-ttu-id="9c57b-117">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="9c57b-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="9c57b-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9c57b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
