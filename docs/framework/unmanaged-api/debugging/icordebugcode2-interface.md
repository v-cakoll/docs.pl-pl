---
title: ICorDebugCode2, interfejs
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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750114"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="93cf4-102">ICorDebugCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="93cf4-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="93cf4-103">Udostępnia metody, które rozszerzają możliwości "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="93cf4-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93cf4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="93cf4-104">Methods</span></span>  
  
|<span data-ttu-id="93cf4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="93cf4-105">Method</span></span>|<span data-ttu-id="93cf4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="93cf4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93cf4-107">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="93cf4-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="93cf4-108">Pobiera fragmentów kodu, który składa się ten obiekt kodu z.</span><span class="sxs-lookup"><span data-stu-id="93cf4-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="93cf4-109">GetCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="93cf4-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="93cf4-110">Pobiera flagi, które określają warunki, na których ten obiekt kod był albo just-in-time (JIT) skompilowanego lub wygenerowany za pomocą generator obrazu natywnego (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="93cf4-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93cf4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93cf4-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93cf4-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="93cf4-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93cf4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93cf4-113">Requirements</span></span>  
 <span data-ttu-id="93cf4-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93cf4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93cf4-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93cf4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93cf4-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93cf4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93cf4-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93cf4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93cf4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93cf4-118">See also</span></span>

- [<span data-ttu-id="93cf4-119">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="93cf4-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="93cf4-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="93cf4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
