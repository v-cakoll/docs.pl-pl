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
ms.openlocfilehash: 9fb849c78636d5e29f58a70f59aa4cb3cd22df40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784738"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="2c8fc-102">ICorDebugAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="2c8fc-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="2c8fc-103">Udostępnia metodę `Next`, która zwraca określoną liczbę `ICorDebugAppDomainEnum` wartości, zaczynając od następnej lokalizacji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="2c8fc-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="2c8fc-104">Ten interfejs jest podklasą elementu "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="2c8fc-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c8fc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2c8fc-105">Methods</span></span>  
  
|<span data-ttu-id="2c8fc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2c8fc-106">Method</span></span>|<span data-ttu-id="2c8fc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2c8fc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c8fc-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="2c8fc-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="2c8fc-109">Pobiera określoną liczbę domen aplikacji z kolekcji, rozpoczynając od bieżącego położenia kursora.</span><span class="sxs-lookup"><span data-stu-id="2c8fc-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c8fc-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c8fc-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c8fc-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="2c8fc-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c8fc-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c8fc-112">Requirements</span></span>  
 <span data-ttu-id="2c8fc-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c8fc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c8fc-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c8fc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c8fc-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2c8fc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c8fc-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c8fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c8fc-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c8fc-117">See also</span></span>

- [<span data-ttu-id="2c8fc-118">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="2c8fc-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="2c8fc-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2c8fc-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
