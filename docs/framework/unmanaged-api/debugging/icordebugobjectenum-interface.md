---
title: ICorDebugObjectEnum, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1faa78150659b4397cd4174583b607e1f7841b8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943362"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="05ce6-102">ICorDebugObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="05ce6-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="05ce6-103">Implementuje metody ICorDebugEnum i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="05ce6-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05ce6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="05ce6-104">Methods</span></span>  
  
|<span data-ttu-id="05ce6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="05ce6-105">Method</span></span>|<span data-ttu-id="05ce6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="05ce6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05ce6-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="05ce6-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="05ce6-108">Pobiera RVA określoną liczbę obiektów z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="05ce6-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05ce6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05ce6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05ce6-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="05ce6-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ce6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05ce6-111">Requirements</span></span>  
 <span data-ttu-id="05ce6-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ce6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ce6-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05ce6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05ce6-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05ce6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05ce6-115">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ce6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ce6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05ce6-116">See also</span></span>

- [<span data-ttu-id="05ce6-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="05ce6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
