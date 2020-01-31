---
title: ICorDebugProcess3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
ms.openlocfilehash: 28d1d426276e9654c2122f03fb64735b7e67f44f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792478"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="acd8a-102">ICorDebugProcess3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="acd8a-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="acd8a-103">Steruje niestandardowymi powiadomieniami debugera.</span><span class="sxs-lookup"><span data-stu-id="acd8a-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acd8a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="acd8a-104">Methods</span></span>  
  
|<span data-ttu-id="acd8a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="acd8a-105">Method</span></span>|<span data-ttu-id="acd8a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="acd8a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acd8a-107">SetEnableCustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="acd8a-107">SetEnableCustomNotification Method</span></span>](icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="acd8a-108">Włącza i wyłącza niestandardowe powiadomienia debugera określonego typu.</span><span class="sxs-lookup"><span data-stu-id="acd8a-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acd8a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acd8a-109">Remarks</span></span>  
 <span data-ttu-id="acd8a-110">Ten interfejs logicznie rozszerza interfejsy ICorDebugProcess i ICorDebugProcess2.</span><span class="sxs-lookup"><span data-stu-id="acd8a-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acd8a-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="acd8a-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acd8a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="acd8a-112">Requirements</span></span>  
 <span data-ttu-id="acd8a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acd8a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acd8a-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="acd8a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acd8a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="acd8a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acd8a-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acd8a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd8a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acd8a-117">See also</span></span>

- [<span data-ttu-id="acd8a-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="acd8a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="acd8a-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="acd8a-119">Debugging</span></span>](index.md)
