---
title: COR_ACTIVE_FUNCTION — Struktura
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50dd4acece43628b20b6bc50a539ee197e865855
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274156"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="14ad9-102">COR_ACTIVE_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="14ad9-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="14ad9-103">Zawiera informacje o funkcjach, które są obecnie aktywne w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="14ad9-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="14ad9-104">Ta struktura jest używana przez metodę [ICorDebugThread2:: GetActiveFunctions —](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="14ad9-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14ad9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="14ad9-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="14ad9-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="14ad9-106">Members</span></span>  
  
|<span data-ttu-id="14ad9-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="14ad9-107">Member</span></span>|<span data-ttu-id="14ad9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="14ad9-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="14ad9-109">Wskaźnik do właściciela `ilOffset` domeny aplikacji pola.</span><span class="sxs-lookup"><span data-stu-id="14ad9-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="14ad9-110">Wskaźnik do właściciela `ilOffset` modułu pola.</span><span class="sxs-lookup"><span data-stu-id="14ad9-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="14ad9-111">Wskaźnik do właściciela `ilOffset` funkcji pola.</span><span class="sxs-lookup"><span data-stu-id="14ad9-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="14ad9-112">Przesunięcie języka pośredniego (MSIL) firmy Microsoft dla ramki.</span><span class="sxs-lookup"><span data-stu-id="14ad9-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="14ad9-113">Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="14ad9-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14ad9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14ad9-114">Requirements</span></span>  
 <span data-ttu-id="14ad9-115">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14ad9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14ad9-116">**Nagłówki** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="14ad9-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="14ad9-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14ad9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14ad9-118">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14ad9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ad9-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14ad9-119">See also</span></span>

- [<span data-ttu-id="14ad9-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="14ad9-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="14ad9-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="14ad9-121">Debugging</span></span>](index.md)
