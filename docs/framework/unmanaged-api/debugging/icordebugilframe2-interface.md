---
title: ICorDebugILFrame2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 08c2946a9bd6251f377ea594c0c3ca5d1bd98c67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095092"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="1daf4-102">ICorDebugILFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1daf4-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="1daf4-103">Logiczne rozszerzenie interfejsu ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="1daf4-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1daf4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1daf4-104">Methods</span></span>  
  
|<span data-ttu-id="1daf4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1daf4-105">Method</span></span>|<span data-ttu-id="1daf4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1daf4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1daf4-107">EnumerateTypeParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="1daf4-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="1daf4-108">Pobiera obiekt ICorDebugTypeEnum, który zawiera <xref:System.Type> parametry w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="1daf4-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="1daf4-109">RemapFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="1daf4-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="1daf4-110">Ponownie mapuje edytowaną funkcję przez określenie nowego przesunięcia MSIL.</span><span class="sxs-lookup"><span data-stu-id="1daf4-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1daf4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1daf4-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1daf4-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="1daf4-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1daf4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1daf4-113">Requirements</span></span>  
 <span data-ttu-id="1daf4-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1daf4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1daf4-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1daf4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1daf4-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1daf4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1daf4-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1daf4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1daf4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1daf4-118">See also</span></span>

- [<span data-ttu-id="1daf4-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1daf4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
