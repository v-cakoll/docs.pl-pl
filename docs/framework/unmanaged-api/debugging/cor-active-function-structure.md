---
title: "COR_ACTIVE_FUNCTION — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ACTIVE_FUNCTION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ACTIVE_FUNCTION
helpviewer_keywords: COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85096b607fa2fec9875e497cc1f50167fc482fbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="e74fd-102">COR_ACTIVE_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="e74fd-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="e74fd-103">Zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="e74fd-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="e74fd-104">Ta struktura jest używany przez [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e74fd-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e74fd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e74fd-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="e74fd-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e74fd-106">Members</span></span>  
  
|<span data-ttu-id="e74fd-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e74fd-107">Member</span></span>|<span data-ttu-id="e74fd-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e74fd-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="e74fd-109">Wskaźnik do właściciela domeny aplikacji `ilOffset` pola.</span><span class="sxs-lookup"><span data-stu-id="e74fd-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="e74fd-110">Wskaźnik do właściciela modułu `ilOffset` pola.</span><span class="sxs-lookup"><span data-stu-id="e74fd-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="e74fd-111">Wskaźnik do funkcji właściciela `ilOffset` pola.</span><span class="sxs-lookup"><span data-stu-id="e74fd-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="e74fd-112">Język pośredni (MSIL) firmy Microsoft przesunięcie ramki.</span><span class="sxs-lookup"><span data-stu-id="e74fd-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="e74fd-113">Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="e74fd-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e74fd-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e74fd-114">Requirements</span></span>  
 <span data-ttu-id="e74fd-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e74fd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e74fd-116">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="e74fd-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e74fd-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e74fd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e74fd-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e74fd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74fd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e74fd-119">See Also</span></span>  
 [<span data-ttu-id="e74fd-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="e74fd-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="e74fd-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e74fd-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
