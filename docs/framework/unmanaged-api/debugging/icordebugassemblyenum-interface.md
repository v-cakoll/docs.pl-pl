---
title: ICorDebugAssemblyEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum
helpviewer_keywords:
- ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: 891ceb43-5161-421e-a0bf-299962fd7efd
topic_type:
- apiref
ms.openlocfilehash: 988637956b1176235618bf8f4aee7ecec9ce1187
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894835"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="bc1a0-102">ICorDebugAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc1a0-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="bc1a0-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="bc1a0-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc1a0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bc1a0-104">Methods</span></span>  
  
|<span data-ttu-id="bc1a0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bc1a0-105">Method</span></span>|<span data-ttu-id="bc1a0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bc1a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc1a0-107">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="bc1a0-107">Next Method</span></span>](icordebugassemblyenum-next-method.md)|<span data-ttu-id="bc1a0-108">Pobiera określoną liczbę `ICorDebugAssembly` wystąpień w wyliczeniu, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="bc1a0-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc1a0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc1a0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc1a0-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="bc1a0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1a0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc1a0-111">Requirements</span></span>  
 <span data-ttu-id="bc1a0-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc1a0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc1a0-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc1a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc1a0-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc1a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc1a0-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc1a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1a0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc1a0-116">See also</span></span>

- [<span data-ttu-id="bc1a0-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc1a0-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
