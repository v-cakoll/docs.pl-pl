---
title: "COR_DEBUG_IL_TO_NATIVE_MAP — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 954060d790d432456585846e24b399223b513b61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="38426-102">COR_DEBUG_IL_TO_NATIVE_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="38426-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="38426-103">Zawiera przesunięcia, które są używane do mapowania kodu natywnego kodu języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38426-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38426-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38426-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="38426-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="38426-105">Members</span></span>  
  
|<span data-ttu-id="38426-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="38426-106">Member</span></span>|<span data-ttu-id="38426-107">Opis</span><span class="sxs-lookup"><span data-stu-id="38426-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="38426-108">Przesunięcie kod MSIL.</span><span class="sxs-lookup"><span data-stu-id="38426-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="38426-109">Przesunięcie początku kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="38426-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="38426-110">Przesunięcia końca kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="38426-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38426-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38426-111">Requirements</span></span>  
 <span data-ttu-id="38426-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38426-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38426-113">**Nagłówek:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="38426-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="38426-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38426-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38426-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38426-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38426-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38426-116">See Also</span></span>  
 [<span data-ttu-id="38426-117">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="38426-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)  
 [<span data-ttu-id="38426-118">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="38426-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="38426-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="38426-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="38426-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="38426-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
