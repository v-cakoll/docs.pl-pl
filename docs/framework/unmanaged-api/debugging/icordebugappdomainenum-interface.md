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
ms.openlocfilehash: 38603fb53b9cd6548595437b05c1e99ef208d940
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895095"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="cec24-102">ICorDebugAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="cec24-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="cec24-103">Dostarcza `Next` metodę, która zwraca określoną liczbę `ICorDebugAppDomainEnum` wartości, zaczynając od następnej lokalizacji w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="cec24-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="cec24-104">Ten interfejs jest podklasą elementu "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="cec24-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cec24-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cec24-105">Methods</span></span>  
  
|<span data-ttu-id="cec24-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="cec24-106">Method</span></span>|<span data-ttu-id="cec24-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cec24-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cec24-108">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="cec24-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="cec24-109">Pobiera określoną liczbę domen aplikacji z kolekcji, rozpoczynając od bieżącego położenia kursora.</span><span class="sxs-lookup"><span data-stu-id="cec24-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cec24-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cec24-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cec24-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="cec24-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cec24-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cec24-112">Requirements</span></span>  
 <span data-ttu-id="cec24-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cec24-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cec24-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cec24-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cec24-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cec24-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cec24-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cec24-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec24-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cec24-117">See also</span></span>

- [<span data-ttu-id="cec24-118">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cec24-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="cec24-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cec24-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
