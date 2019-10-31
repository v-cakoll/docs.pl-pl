---
title: ICorDebugModule2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: a3a1b658f4ab05c7029de907882fe5ab2513ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127885"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="013f8-102">ICorDebugModule2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="013f8-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="013f8-103">Służy jako logiczne rozszerzenie interfejsu ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="013f8-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="013f8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="013f8-104">Methods</span></span>  
  
|<span data-ttu-id="013f8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="013f8-105">Method</span></span>|<span data-ttu-id="013f8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="013f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="013f8-107">ApplyChanges, metoda</span><span class="sxs-lookup"><span data-stu-id="013f8-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="013f8-108">Stosuje zmiany w metadanych i zmiany w kodzie języka pośredniego firmy Microsoft (MSIL) do uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="013f8-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="013f8-109">GetJITCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="013f8-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="013f8-110">Pobiera flagi kontrolujące kompilację just-in-Time (JIT) dla tego `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="013f8-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="013f8-111">ResolveAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="013f8-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="013f8-112">Rozwiązuje zestaw, do którego odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="013f8-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="013f8-113">SetJITCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="013f8-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="013f8-114">Ustawia flagi kontrolujące kompilację JIT dla tego `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="013f8-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="013f8-115">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="013f8-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="013f8-116">Ustawia stan Tylko mój kod (JMC) dla wszystkich metod wszystkich klas w tym `ICorDebugModule2` do określonej wartości, z wyjątkiem tych w tablicy `pTokens`, która jest ustawiana na wartość odwrotną.</span><span class="sxs-lookup"><span data-stu-id="013f8-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="013f8-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="013f8-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="013f8-118">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="013f8-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="013f8-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="013f8-119">Requirements</span></span>  
 <span data-ttu-id="013f8-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="013f8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="013f8-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="013f8-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="013f8-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="013f8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="013f8-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="013f8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013f8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="013f8-124">See also</span></span>

- [<span data-ttu-id="013f8-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="013f8-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
