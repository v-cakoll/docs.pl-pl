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
ms.openlocfilehash: a9ce778cfa1aed4dcf6117c4fe2eca23ccda37a3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777950"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="288e8-102">ICorDebugCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="288e8-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="288e8-103">Dostarcza metody, które zwiększają możliwości programu "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="288e8-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="288e8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="288e8-104">Methods</span></span>  
  
|<span data-ttu-id="288e8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="288e8-105">Method</span></span>|<span data-ttu-id="288e8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="288e8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="288e8-107">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="288e8-107">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="288e8-108">Pobiera fragmenty kodu, z których składa się ten obiekt kodu.</span><span class="sxs-lookup"><span data-stu-id="288e8-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="288e8-109">GetCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="288e8-109">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="288e8-110">Pobiera flagi określające warunki, w których ten obiekt kodu był skompilowany lub generowany przy użyciu natywnego generatora obrazu (Ngen. exe).</span><span class="sxs-lookup"><span data-stu-id="288e8-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="288e8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="288e8-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="288e8-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="288e8-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="288e8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="288e8-113">Requirements</span></span>  
 <span data-ttu-id="288e8-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="288e8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="288e8-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="288e8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="288e8-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="288e8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="288e8-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="288e8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="288e8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="288e8-118">See also</span></span>

- [<span data-ttu-id="288e8-119">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="288e8-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="288e8-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="288e8-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
