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
ms.openlocfilehash: 0526c050bcf1316eccf2c756a404fbb971e6d7d0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792744"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="e60ed-102">ICorDebugObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="e60ed-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="e60ed-103">Implementuje metody ICorDebugEnum i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).</span><span class="sxs-lookup"><span data-stu-id="e60ed-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e60ed-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e60ed-104">Methods</span></span>  
  
|<span data-ttu-id="e60ed-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e60ed-105">Method</span></span>|<span data-ttu-id="e60ed-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e60ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e60ed-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="e60ed-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="e60ed-108">Pobiera RVA określoną liczbę obiektów z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="e60ed-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e60ed-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e60ed-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e60ed-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e60ed-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e60ed-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e60ed-111">Requirements</span></span>  
 <span data-ttu-id="e60ed-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e60ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e60ed-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e60ed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e60ed-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e60ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e60ed-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e60ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60ed-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e60ed-116">See also</span></span>

- [<span data-ttu-id="e60ed-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e60ed-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
