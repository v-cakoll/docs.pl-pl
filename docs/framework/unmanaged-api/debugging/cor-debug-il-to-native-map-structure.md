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
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274073"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="a450c-102">COR_DEBUG_IL_TO_NATIVE_MAP — Struktura</span><span class="sxs-lookup"><span data-stu-id="a450c-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="a450c-103">Zawiera przesunięcia, które są używane do mapowania kodu języka pośredniego firmy Microsoft (MSIL) na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="a450c-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a450c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a450c-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="a450c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a450c-105">Members</span></span>  
  
|<span data-ttu-id="a450c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a450c-106">Member</span></span>|<span data-ttu-id="a450c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a450c-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="a450c-108">Przesunięcie kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="a450c-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="a450c-109">Przesunięcie początku kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="a450c-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="a450c-110">Przesunięcie końca kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="a450c-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a450c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a450c-111">Requirements</span></span>  
 <span data-ttu-id="a450c-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a450c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a450c-113">**Nagłówki** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="a450c-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="a450c-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a450c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a450c-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a450c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a450c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a450c-116">See also</span></span>

- [<span data-ttu-id="a450c-117">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="a450c-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="a450c-118">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="a450c-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="a450c-119">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="a450c-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a450c-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a450c-120">Debugging</span></span>](index.md)
