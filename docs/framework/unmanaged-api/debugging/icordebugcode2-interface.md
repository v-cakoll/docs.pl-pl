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
ms.openlocfilehash: 9cb7be64089a55e7b653fcd6272219abba311af8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960811"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="835d6-102">ICorDebugCode2, interfejs</span><span class="sxs-lookup"><span data-stu-id="835d6-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="835d6-103">Dostarcza metody, które zwiększają możliwości programu "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="835d6-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="835d6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="835d6-104">Methods</span></span>  
  
|<span data-ttu-id="835d6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="835d6-105">Method</span></span>|<span data-ttu-id="835d6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="835d6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="835d6-107">GetCodeChunks, metoda</span><span class="sxs-lookup"><span data-stu-id="835d6-107">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="835d6-108">Pobiera fragmenty kodu, z których składa się ten obiekt kodu.</span><span class="sxs-lookup"><span data-stu-id="835d6-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="835d6-109">GetCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="835d6-109">GetCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="835d6-110">Pobiera flagi określające warunki, w których ten obiekt kodu był skompilowany lub generowany przy użyciu natywnego generatora obrazu (Ngen. exe).</span><span class="sxs-lookup"><span data-stu-id="835d6-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="835d6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="835d6-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="835d6-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="835d6-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="835d6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="835d6-113">Requirements</span></span>  
 <span data-ttu-id="835d6-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="835d6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="835d6-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="835d6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="835d6-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="835d6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="835d6-117">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="835d6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835d6-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="835d6-118">See also</span></span>

- [<span data-ttu-id="835d6-119">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="835d6-119">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="835d6-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="835d6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
