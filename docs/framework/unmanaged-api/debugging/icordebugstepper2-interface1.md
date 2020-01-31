---
title: ICorDebugStepper2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
ms.openlocfilehash: d154cf10e60935d12653c70875323079f92ae288
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791744"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="f17b6-102">ICorDebugStepper2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f17b6-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="f17b6-103">Zapewnia obsługę debugowania tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="f17b6-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f17b6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f17b6-104">Methods</span></span>  
  
|<span data-ttu-id="f17b6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f17b6-105">Method</span></span>|<span data-ttu-id="f17b6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f17b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f17b6-107">SetJMC, metoda</span><span class="sxs-lookup"><span data-stu-id="f17b6-107">SetJMC Method</span></span>](icordebugstepper2-setjmc-method.md)|<span data-ttu-id="f17b6-108">Ustawia wartość określającą, czy ten ICorDebugStepper czynności tylko za pomocą kodu, który jest tworzony przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f17b6-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f17b6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f17b6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f17b6-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="f17b6-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f17b6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f17b6-111">Requirements</span></span>  
 <span data-ttu-id="f17b6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f17b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f17b6-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f17b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f17b6-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f17b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f17b6-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f17b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17b6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f17b6-116">See also</span></span>

- [<span data-ttu-id="f17b6-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f17b6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
