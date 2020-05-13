---
title: ICorDebugILFrame2, interfejs
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
ms.openlocfilehash: 2e0f284625e99215900c6aaab94e4eae611787ed
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212103"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="a79b8-102">ICorDebugILFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a79b8-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="a79b8-103">Logiczne rozszerzenie interfejsu ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="a79b8-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a79b8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a79b8-104">Methods</span></span>  
  
|<span data-ttu-id="a79b8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a79b8-105">Method</span></span>|<span data-ttu-id="a79b8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a79b8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a79b8-107">EnumerateTypeParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="a79b8-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="a79b8-108">Pobiera obiekt ICorDebugTypeEnum, który zawiera <xref:System.Type> Parametry w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="a79b8-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="a79b8-109">RemapFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="a79b8-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="a79b8-110">Ponownie mapuje edytowaną funkcję przez określenie nowego przesunięcia MSIL.</span><span class="sxs-lookup"><span data-stu-id="a79b8-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a79b8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a79b8-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a79b8-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a79b8-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a79b8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a79b8-113">Requirements</span></span>  
 <span data-ttu-id="a79b8-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a79b8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a79b8-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a79b8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a79b8-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a79b8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a79b8-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a79b8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a79b8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a79b8-118">See also</span></span>

- [<span data-ttu-id="a79b8-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a79b8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
