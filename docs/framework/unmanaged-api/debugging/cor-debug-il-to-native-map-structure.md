---
title: COR_DEBUG_IL_TO_NATIVE_MAP — Struktura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56d4255b06f1317c87685737e4ee4021c37a77f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555014"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="3f1f8-102">COR_DEBUG_IL_TO_NATIVE_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="3f1f8-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="3f1f8-103">Zawiera przesunięcia, które są używane do mapowania kod intermediate language (MSIL) firmy Microsoft do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="3f1f8-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f1f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f1f8-104">Syntax</span></span>  
  
```  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="3f1f8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3f1f8-105">Members</span></span>  
  
|<span data-ttu-id="3f1f8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3f1f8-106">Member</span></span>|<span data-ttu-id="3f1f8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3f1f8-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="3f1f8-108">Przesunięcie kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="3f1f8-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="3f1f8-109">Przesunięcie początku kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="3f1f8-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="3f1f8-110">Przesunięcia końca kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="3f1f8-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f1f8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f1f8-111">Requirements</span></span>  
 <span data-ttu-id="3f1f8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f1f8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f1f8-113">**Nagłówek:** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="3f1f8-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="3f1f8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f1f8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f1f8-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f1f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f1f8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f1f8-116">See also</span></span>
- [<span data-ttu-id="3f1f8-117">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="3f1f8-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="3f1f8-118">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="3f1f8-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="3f1f8-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="3f1f8-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="3f1f8-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3f1f8-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
