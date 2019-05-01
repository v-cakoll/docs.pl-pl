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
ms.openlocfilehash: da1fc949109455cf50767191a99a8a727116f77c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989511"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="3518a-102">ICorDebugAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="3518a-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="3518a-103">Udostępnia `Next` metody, która zwraca określoną liczbę `ICorDebugAppDomainEnum` wartości, zaczynając od następnej pozycji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="3518a-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="3518a-104">Ten interfejs jest podklasą "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="3518a-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3518a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3518a-105">Methods</span></span>  
  
|<span data-ttu-id="3518a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3518a-106">Method</span></span>|<span data-ttu-id="3518a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3518a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3518a-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="3518a-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="3518a-109">Pobiera określoną liczbę domen aplikacji z kolekcji, począwszy od bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="3518a-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3518a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3518a-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3518a-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="3518a-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3518a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3518a-112">Requirements</span></span>  
 <span data-ttu-id="3518a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3518a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3518a-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3518a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3518a-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3518a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3518a-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3518a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3518a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3518a-117">See also</span></span>

- [<span data-ttu-id="3518a-118">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="3518a-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="3518a-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3518a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
