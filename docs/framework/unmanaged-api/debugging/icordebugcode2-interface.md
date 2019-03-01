---
title: ICorDebugCode2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dce3e3e4baeaa351c5ed1d9e5ca2c03631c3fce4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964270"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="45beb-102">ICorDebugCode2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="45beb-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="45beb-103">Udostępnia metody, które rozszerzają możliwości "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="45beb-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45beb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="45beb-104">Methods</span></span>  
  
|<span data-ttu-id="45beb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="45beb-105">Method</span></span>|<span data-ttu-id="45beb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="45beb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45beb-107">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="45beb-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="45beb-108">Pobiera fragmentów kodu, który składa się ten obiekt kodu z.</span><span class="sxs-lookup"><span data-stu-id="45beb-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="45beb-109">GetCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="45beb-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="45beb-110">Pobiera flagi, które określają warunki, na których ten obiekt kod był albo just-in-time (JIT) skompilowanego lub wygenerowany za pomocą generator obrazu natywnego (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="45beb-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45beb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45beb-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45beb-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="45beb-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45beb-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45beb-113">Requirements</span></span>  
 <span data-ttu-id="45beb-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45beb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45beb-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45beb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45beb-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45beb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45beb-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45beb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45beb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45beb-118">See also</span></span>

- [<span data-ttu-id="45beb-119">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="45beb-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="45beb-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="45beb-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
