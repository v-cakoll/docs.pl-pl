---
title: ICorDebugModule2, interfejs
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
ms.openlocfilehash: 32774aacecf3e56510bc6f0670538a44fde794c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792990"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="b673b-102">ICorDebugModule2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b673b-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="b673b-103">Służy jako logiczne rozszerzenie interfejsu ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="b673b-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b673b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b673b-104">Methods</span></span>  
  
|<span data-ttu-id="b673b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b673b-105">Method</span></span>|<span data-ttu-id="b673b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b673b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b673b-107">ApplyChanges, metoda</span><span class="sxs-lookup"><span data-stu-id="b673b-107">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="b673b-108">Stosuje zmiany w metadanych i zmiany w kodzie języka pośredniego firmy Microsoft (MSIL) do uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="b673b-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="b673b-109">GetJITCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="b673b-109">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="b673b-110">Pobiera flagi kontrolujące kompilację just-in-Time (JIT) dla tego `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="b673b-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="b673b-111">ResolveAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="b673b-111">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="b673b-112">Rozwiązuje zestaw, do którego odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="b673b-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="b673b-113">SetJITCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="b673b-113">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="b673b-114">Ustawia flagi kontrolujące kompilację JIT dla tego `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="b673b-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="b673b-115">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="b673b-115">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="b673b-116">Ustawia stan Tylko mój kod (JMC) dla wszystkich metod wszystkich klas w tym `ICorDebugModule2` do określonej wartości, z wyjątkiem tych w tablicy `pTokens`, która jest ustawiana na wartość odwrotną.</span><span class="sxs-lookup"><span data-stu-id="b673b-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b673b-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b673b-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b673b-118">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b673b-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b673b-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b673b-119">Requirements</span></span>  
 <span data-ttu-id="b673b-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b673b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b673b-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b673b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b673b-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b673b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b673b-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b673b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b673b-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b673b-124">See also</span></span>

- [<span data-ttu-id="b673b-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b673b-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
