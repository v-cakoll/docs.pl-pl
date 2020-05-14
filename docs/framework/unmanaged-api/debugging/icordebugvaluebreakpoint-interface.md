---
title: ICorDebugValueBreakpoint, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
ms.openlocfilehash: 1183f9f6d1ac221b20767f0a1bab15b3e9665a61
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396610"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="1c8f0-102">ICorDebugValueBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c8f0-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="1c8f0-103">Rozszerza interfejs ICorDebugBreakpoint w celu zapewnienia dostępu do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="1c8f0-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c8f0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1c8f0-104">Methods</span></span>  
  
|<span data-ttu-id="1c8f0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1c8f0-105">Method</span></span>|<span data-ttu-id="1c8f0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1c8f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c8f0-107">GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c8f0-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="1c8f0-108">Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wartość obiektu, na którym jest ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="1c8f0-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c8f0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c8f0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c8f0-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="1c8f0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c8f0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c8f0-111">Requirements</span></span>  
 <span data-ttu-id="1c8f0-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c8f0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c8f0-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c8f0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c8f0-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c8f0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c8f0-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c8f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8f0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c8f0-116">See also</span></span>

- [<span data-ttu-id="1c8f0-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1c8f0-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
