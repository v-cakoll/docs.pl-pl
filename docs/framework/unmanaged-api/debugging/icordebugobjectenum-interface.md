---
title: ICorDebugObjectEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: b77d5859986c90d6ef61c02547014d0bec354106
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096140"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="9eaea-102">ICorDebugObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9eaea-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="9eaea-103">Implementuje metody ICorDebugEnum i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="9eaea-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9eaea-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9eaea-104">Methods</span></span>  
  
|<span data-ttu-id="9eaea-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9eaea-105">Method</span></span>|<span data-ttu-id="9eaea-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9eaea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9eaea-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="9eaea-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="9eaea-108">Pobiera RVA określoną liczbę obiektów z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="9eaea-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eaea-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9eaea-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9eaea-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="9eaea-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eaea-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9eaea-111">Requirements</span></span>  
 <span data-ttu-id="9eaea-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eaea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eaea-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9eaea-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eaea-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9eaea-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eaea-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eaea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eaea-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9eaea-116">See also</span></span>

- [<span data-ttu-id="9eaea-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9eaea-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
