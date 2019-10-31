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
ms.openlocfilehash: cbc272070e9eb6810b34ec1f3fdc9e944c624cd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132380"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="4f04a-102">COR_ACTIVE_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="4f04a-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="4f04a-103">Zawiera informacje o funkcjach, które są obecnie aktywne w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="4f04a-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="4f04a-104">Ta struktura jest używana przez metodę [ICorDebugThread2:: GetActiveFunctions —](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4f04a-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f04a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f04a-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="4f04a-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4f04a-106">Members</span></span>  
  
|<span data-ttu-id="4f04a-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4f04a-107">Member</span></span>|<span data-ttu-id="4f04a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4f04a-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="4f04a-109">Wskaźnik do właściciela domeny aplikacji pola `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="4f04a-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="4f04a-110">Wskaźnik do właściciela modułu pola `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="4f04a-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="4f04a-111">Wskaźnik do właściciela funkcji pola `ilOffset`.</span><span class="sxs-lookup"><span data-stu-id="4f04a-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="4f04a-112">Przesunięcie języka pośredniego (MSIL) firmy Microsoft dla ramki.</span><span class="sxs-lookup"><span data-stu-id="4f04a-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="4f04a-113">Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="4f04a-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f04a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f04a-114">Requirements</span></span>  
 <span data-ttu-id="4f04a-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f04a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f04a-116">**Nagłówek:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="4f04a-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="4f04a-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4f04a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f04a-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f04a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f04a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f04a-119">See also</span></span>

- [<span data-ttu-id="4f04a-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="4f04a-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="4f04a-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4f04a-121">Debugging</span></span>](index.md)
