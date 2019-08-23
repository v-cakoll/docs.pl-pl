---
title: ICorDebugAppDomainEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c48c222a34e2e78f29c33e49da331d97d409bae1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949760"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="a238f-102">ICorDebugAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a238f-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="a238f-103">Dostarcza metodę, która zwraca określoną `ICorDebugAppDomainEnum` liczbę wartości, zaczynając od następnej lokalizacji w wyliczeniu. `Next`</span><span class="sxs-lookup"><span data-stu-id="a238f-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="a238f-104">Ten interfejs jest podklasą elementu "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="a238f-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a238f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a238f-105">Methods</span></span>  
  
|<span data-ttu-id="a238f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a238f-106">Method</span></span>|<span data-ttu-id="a238f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a238f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a238f-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="a238f-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="a238f-109">Pobiera określoną liczbę domen aplikacji z kolekcji, rozpoczynając od bieżącego położenia kursora.</span><span class="sxs-lookup"><span data-stu-id="a238f-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a238f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a238f-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a238f-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a238f-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a238f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a238f-112">Requirements</span></span>  
 <span data-ttu-id="a238f-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a238f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a238f-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a238f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a238f-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a238f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a238f-116">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a238f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a238f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a238f-117">See also</span></span>

- [<span data-ttu-id="a238f-118">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a238f-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="a238f-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a238f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
