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
ms.openlocfilehash: 2a36c9808f29c038e3185157078c235959baf13c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132365"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="6eff6-102">COR_DEBUG_IL_TO_NATIVE_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="6eff6-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="6eff6-103">Zawiera przesunięcia, które są używane do mapowania kodu języka pośredniego firmy Microsoft (MSIL) na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="6eff6-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eff6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6eff6-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="6eff6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6eff6-105">Members</span></span>  
  
|<span data-ttu-id="6eff6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6eff6-106">Member</span></span>|<span data-ttu-id="6eff6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6eff6-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="6eff6-108">Przesunięcie kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="6eff6-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="6eff6-109">Przesunięcie początku kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="6eff6-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="6eff6-110">Przesunięcie końca kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="6eff6-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6eff6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6eff6-111">Requirements</span></span>  
 <span data-ttu-id="6eff6-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eff6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eff6-113">**Nagłówek:** CorProf. idl, CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="6eff6-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="6eff6-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6eff6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eff6-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eff6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eff6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6eff6-116">See also</span></span>

- [<span data-ttu-id="6eff6-117">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="6eff6-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="6eff6-118">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="6eff6-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="6eff6-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="6eff6-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="6eff6-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6eff6-120">Debugging</span></span>](index.md)
