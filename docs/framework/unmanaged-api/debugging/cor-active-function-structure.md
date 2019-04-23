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
ms.openlocfilehash: c0400da0cd29d642a1be42be7e2b22213ae54b94
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121774"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="83de0-102">COR_ACTIVE_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="83de0-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="83de0-103">Zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach w wątku.</span><span class="sxs-lookup"><span data-stu-id="83de0-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="83de0-104">Ta struktura jest używany przez [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="83de0-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83de0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="83de0-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="83de0-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="83de0-106">Members</span></span>  
  
|<span data-ttu-id="83de0-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="83de0-107">Member</span></span>|<span data-ttu-id="83de0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="83de0-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="83de0-109">Wskaźnik do właściciela domeny aplikacji `ilOffset` pola.</span><span class="sxs-lookup"><span data-stu-id="83de0-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="83de0-110">Wskaźnik do właściciela modułu `ilOffset` pola.</span><span class="sxs-lookup"><span data-stu-id="83de0-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="83de0-111">Wskaźnik do funkcji właściciela `ilOffset` pola.</span><span class="sxs-lookup"><span data-stu-id="83de0-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="83de0-112">Przesunięcia języka pośredniego (MSIL) firmy Microsoft ramki.</span><span class="sxs-lookup"><span data-stu-id="83de0-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="83de0-113">Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="83de0-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83de0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83de0-114">Requirements</span></span>  
 <span data-ttu-id="83de0-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83de0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83de0-116">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="83de0-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="83de0-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83de0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83de0-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83de0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83de0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83de0-119">See also</span></span>

- [<span data-ttu-id="83de0-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="83de0-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="83de0-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="83de0-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
