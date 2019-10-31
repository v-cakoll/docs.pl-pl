---
title: ICorDebugAppDomainEnum — Interfejs
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
ms.openlocfilehash: 6cc3ec1c802c28b74248380aa7f686e675a92f1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088843"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="ef822-102">ICorDebugAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef822-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="ef822-103">Udostępnia metodę `Next`, która zwraca określoną liczbę `ICorDebugAppDomainEnum` wartości, zaczynając od następnej lokalizacji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="ef822-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="ef822-104">Ten interfejs jest podklasą elementu "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="ef822-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef822-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ef822-105">Methods</span></span>  
  
|<span data-ttu-id="ef822-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ef822-106">Method</span></span>|<span data-ttu-id="ef822-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ef822-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef822-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="ef822-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="ef822-109">Pobiera określoną liczbę domen aplikacji z kolekcji, rozpoczynając od bieżącego położenia kursora.</span><span class="sxs-lookup"><span data-stu-id="ef822-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef822-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef822-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef822-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="ef822-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef822-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef822-112">Requirements</span></span>  
 <span data-ttu-id="ef822-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef822-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef822-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef822-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef822-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ef822-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef822-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef822-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef822-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef822-117">See also</span></span>

- [<span data-ttu-id="ef822-118">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef822-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="ef822-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ef822-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
